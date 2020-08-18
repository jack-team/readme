UMD——通用模块规范

用一个工厂函数来统一不同的模块定义规范。

所有定义模块的方法需要单独传入依赖
所有定义模块的方法都需要返回一个对象，供其他模块使用

(function (global, factory) {
    if (typeof exports === 'object' && typeof module !== undefined) { //检查CommonJS是否可用
        module.exports = factory(require('jquery'));
    } else if (typeof define === 'function' && define.amd) {      //检查AMD是否可用
        define('toggler', ['jquery', factory])
    } else {       //两种都不能用，把模块添加到JavaScript的全局命名空间中。
        global.toggler = factory(global, factory);
    }
})(this, function ($) {
    function init() {

    }
    return {
        init: init
    }
});
