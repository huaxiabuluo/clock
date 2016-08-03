# A clock #

### Example ###

    (function($) {
    	var timer;

    	$.Clock = function() {
    		this.clock;
    		this.hour;
    		this.minute;
    		this.second;

    		this.init();
    	};

    	Clock.prototype.init = function() {
    		this.clock = document.createElement('div');
    		this.clock.classList.add('clock');

    		_createInsert.call(this, ['hour', 'minute', 'second'], {
    			hour: ['hour', 'hand'],
    			minute: ['minute', 'hand'],
    			second: ['second', 'hand'],
    		}, this.clock);

    		document.body.appendChild(this.clock);
    	};

    	Clock.prototype.start = function() {
    		var self = this;
    		timer = setInterval(_setHandDegree.bind(self), 500);
    	};

    	Clock.prototype.stop = function() {
    		clearInterval(timer);
    	};

    	function _setHandDegree() {
    		var time = new Date();
    		var ssDeg = time.getSeconds() / 60 * 360;
    		var mmDeg = time.getMinutes() / 60 * 360;
    		var hhDeg = (time.getHours() % 12 + time.getMinutes() / 60) * 30;

    		this.second.style.transform = 'rotate(' + ssDeg + 'deg)';
    		this.minute.style.transform = 'rotate(' + mmDeg + 'deg)';
    		this.hour.style.transform = 'rotate(' + hhDeg + 'deg)';
    	}

    	function _createInsert(names, classObj, parent) {
    		var self = this;
    		names.forEach(function(name) {
    			self[name] = document.createElement('div');
    			classObj[name].forEach(function(element) {
    				self[name].classList.add(element);
    			});
    			if (!!parent) {
    				parent.appendChild(self[name]);
    			}
    		});
    	}
    })(window);


