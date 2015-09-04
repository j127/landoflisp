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

#### `if`

    (if (= 5 (+ 4 1))
         'return-true
         'return-false')

You can fit multiple commands into `if` via `progn`:

    (if (= 5 (+ 4 1))
        (progn (princ "Saluton, Mondo!") ; First command
                'its-true)               ; Second command
        'its-false)

#### `cond`

    (defun number-size (n)
        (cond ((< n 10) 'small)
              ((= n 10) 'medium')
              ((> n 10) 'large)
              (t 'we-reached-the-else)))

#### Others

* There is also a `case`/`otherwise` form that uses `eq` to compare symbols.
* `and`
* `or`

### Functions to Know

* `ash` -- arithmetic shift
* `eq` -- compares two symbols
* `equal` -- use this for most everything else, and you'll be okay
* `equalp` -- like `equal` but handles things like: case-insensitivity and comparing ints with floats
* `eql` -- works for symbols, numbers, and characters
* `=` -- for numbers
* `string-equal` -- for strings
* `char-equal` -- for characters
* `princ`
* `expt` -- exponent
* `sqrt` -- square root
* `cons`, `car`, `cdr`, etc.
* `1+` and `1-`
* `oddp` and `evenp`-- check if number is odd or even
* `list` -- create a list
* `null` returns true for `nil`
* `member` -- see if something is in a list and returns the tail of the list
* `find-if` -- apply a function to list items and return the first item that evaluates as true. `(find-if #'some-fn '(some list of items))`
* `assoc` -- get a key-value pair out of an alist.
* `mapcar` -- map a function over a list
* `apply` -- passes each item in a list into a function, even if nested
* `append` -- joins lists

