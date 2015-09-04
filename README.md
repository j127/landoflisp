# Land of Lisp

[Land of Lisp](http://landoflisp.com/)

## To Remember

My notes may not be correct. I'm writing them as I understand it (i.e., incompletely and possibly incorrectly). I might update them as I learn more.

### Variables

* `(defparameter *my-var* 127)` -- not immutable
* `(defvar *my-var* 127)` -- immutable
* Global (a.k.a., _dynamic_, _special_) variables should get \*earmuffs\*.
* `(setf *my-var* 721)` -- change a variable defined with `defparameter`

Set local variables with `let`:

    (let ((x 19)
          (y 127)) ; Define as many as you want
      (* x y))

### Functions

* `(defun some-fn (n) (* n n)` and `(some-fn 9)`

Define local functions with `flet`:

    (flet ((some-fn (n)
             (* n n))
           (other-fn (m)
             (+ m m)))
      (some-fn (other-fn 127))) ; They don't know each other's name

To allow `other-fn` to use the name of `other-fn` within the body, use `labels` instead of `flet`.

### Logic

    (if (= 5 (+ 4 1))
         'return-true
         'return-false')

You can fit multiple commands into `if` via `progn`:

    (if (= 5 (+ 4 1))
        (progn (princ "Saluton, Mondo!") ; First command
                'its-true)               ; Second command
        'its-false)

### Functions to Know

* `ash` -- arithmetic shift
* `eq` -- compares two symbols
* `princ`
* `expt` -- exponent
* `cons`, `car`, `cdr`, etc.
* `1+` and `1-`
