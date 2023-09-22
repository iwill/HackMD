Hello HeckMD
============

## test

- a
- b
- c
- d

|  a  |  b  |
| --: | :-: |
| 1   | 2   |
| 3   | 4   |

```javascript=
export default function $class(source, SuperClass) {
    // default values
    SuperClass = SuperClass || Object;
    source = source || {};
    // constructor & super constructor
    source.constructor = source.hasOwnProperty("constructor") ? source.constructor : function() {
        SuperClass.apply(this, arguments);
    };
    
    // class & prototype
    const Class = source.constructor;
    Class.isPlainObject = true;
    Class.prototype = new SuperClass();
    // override Class.prototype[each] by source[each]
    for (let each in source) {
        Class.prototype[each] = source[each]; // include `constructor`
    }
    
    return Class;
}

```
