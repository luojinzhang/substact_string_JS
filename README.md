# substact_string_JS
number String - number String function
        String.prototype.subtract = function (subtrahend) {
            var a = this.split("").map(Number).reverse();
            var b = subtrahend.split("").map(Number).reverse();
            var c = [];
            var borrow = 0;

            if (a.length > b.length) {
                var distance = a.length - b.length;
                for (var i = 0; i < distance; i++) {
                    b.push(0);
                }
            }
            else if (a.length < b.length) {
                var distance = a.length - b.length;
                for (var i = 0; i < distance; i++) {
                    a.push(0);
                }
            }

            while (a.length !== 0 || b.length !== 0) {
                var a_ = a.shift();
                var b_ = b.shift() + borrow;
                if (isNaN(a_) || isNaN(b_)) {
                    return "NaN";
                }
                if (a_ >= (b_)) {
                    c.push((a_ - b_));
                    if (borrow > 0) {
                        borrow--;
                    }
                }
                else {
                    c.push((a_ + 10 - b_));
                    borrow++;
                }
            }
            c = c.reverse();
            var n = c.join('');
            return n;
        };
