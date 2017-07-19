```
var Promise = function() {
    this.doneList = [];
    this.failList = [];
    this.state = 'pending';
};

Promise.prototype = {
    constructor: 'Promise',
    resolve: function() {
        this.state = 'resolved';
        var list = this.doneList;
        for(var i = 0, len = list.length; i < len; i++) {
            list[0].call(this);
            list.shift();
        }
    },
    reject: function() {
        this.state = 'rejected';
        var list = this.failList;
        for(var i = 0, len = list.length; i < len; i++){
            list[0].call(this);
            list.shift();
        }
    },
    done: function(func) {
        if(typeof func === 'function') {
            this.doneList.push(func);
        }
        return this;
    },
    fail: function(func) {
        if(typeof func === 'function') {
            this.failList.push(func);
        }
        return this;
    },
    then: function(doneFn, failFn) {
        this.done(doneFn).fail(failFn);
        return this;
    },
    always: function(fn) {
        this.done(fn).fail(fn);
        return this;
    }
};
```