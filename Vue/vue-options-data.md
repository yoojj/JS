# Vue Options Data

- Data
    - [data](#data)
    - [props](#props)
    - propsData
    - [methods](#methods)
    - [computed](#computed)
    - [watch](#watch)
- [DOM](./vue-options-dom.md)
- [Assets](./vue-options-assets.md)
- [Composition](./vue-options-composition.md)
- [Misc](./vue-options-misc.md)



## data
: vue 인스턴스가 관리하는 데이터 객체나 함수  

```js
var vm = new Vue({

    // 객체인 경우 모든 vue 인스턴스에서 참조
    // data : {},

    data() {
        return {
            key : 'value',
            // get key : reactiveGetter()
            // set key : reactiveSetter(newVal)
        }
    }

});

(vm.$data.str === vm.str) == true



/* vue.js */
// 반응형 설정  
function initData(vm) {
    var data = vm.$options.data;
    data = vm._data = typeof data === 'function'
      ? getData(data, vm)
      : data || {};

    if (!isPlainObject(data)) {
        data = {};
        warn('data functions should return an object...');
    };

    var keys = Object.keys(data);
    var props = vm.$options.props;

    var i = keys.length;
    while(i--) {
        if (props && hasOwn(props, keys[i])) {
            warn(`The data property ${keys[i]} is already declared as a prop...`);
        } else {
            proxy(vm, keys[i]);
        }

        observe(data, true);
    }
}

function observe(value, asRootData) { .. }
```



## props
: 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달할 때 데이터를 받는 속성

**옵션**    
- type
- default
- required
- validator


```html
<div id="app">
    <component-name :propsdata="obj" />
</div>

<script>
// 하위 컴포넌트
var child = {
    props : {
        propsdata : {
            type : Object,
            default : () => ({}),
        }
    },
    template : `
        <div>
            <h1>children component</h1>
            <p>{{ propsdata }}</p>
        </div>`,
};

// 상위 컴포넌트
new Vue({

    el : app,

    data() {
        return {
            obj : {
                str : 'string',
                num : 'number',
            },
        }
    },

    components : {
        ComponentName : child,
    },

});
</script>
```



## methods
: vue 인스턴스에 기능을 추가하기 위한 속성

```html
<div id="app">
    <button @click="setDate">click</button>
    <p>{{ date }}</p>
</div>

<script>
new Vue({

    el : app,

    data(){
        return {
            date : null,
        }
    },

    methods : {
        setDate() {
            this.date = new Date();
        },
    },

});
</script>
```



## computed
: 데이터 조작과 관련된 기능을 추가하기 위한 속성    
: data 속성의 변경 사항을 추적하여 데이터 변경마다 수행      

**computed vs methods**    
: computed 속성은 데이터가 변경되지 않았다면 이전 값을 캐싱하고 methods 속성은 호출마다 로직 수행    


```html
<div id="app">
    <p>{{ Date = '2020-12-25' }}</p>
    <p>{{ Date }}</p>
</div>

<script>
new Vue({

    el : app,

    data() {
        return {
            date : null,
        }
    },

    computed : {
        Date : {
            get() {
                return this.date;
            },

            set(val) {
                if(val === null) {
                    this.date = new Date();
                } else {
                    this.date = new Date(val);
                }
            },
        },
    },

});
</script>
```



## watch
: 데이터 변경시 특정 기능을 추가하기 위한 속성    
: data 속성의 변경 사항을 추적하여 데이터가 변경될 경우 지정된 로직 실행  

**옵션**   
- immediate : 페이지 로드 즉시 한 번 실행 여부 설정
- deep : 중첩 데이터 변경 감지 여부 설정
- handler : 변경 발생시 호출할 함수


```html
<div id="app">
    <p>{{ date }}</p>
    <p>{{ getDate }}</p>
</div>

<script>
var vm = new Vue({

    el : app,

    data() {
        return {
            date : new Date(),
            count : 0,
        }
    },

    watch : {
        date(val, oldVal) {
            this.count += 1;
        },
        count : {
            deep : true,
            handler() {
                console.log('count : ' + this.count);
            }
        }
    },

    computed : {
        getDate() {
            return this.date.toString().slice(10, 25);
        },
    },

});

setInterval(() => {
    vm.date = new Date();
}, 3000);
</script>
```



[top](#)
