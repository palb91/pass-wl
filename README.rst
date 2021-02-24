``pass-wl``
###########

    :Author:       palb91
    :License:      MIT
    :Description:  Type a password from password-store in a Wayland environment
    :Dependancies: - pass_;
                   - pass-otp_ (optional);
                   - wtype_;
                   - bemenu_;
                   - wl-clipboard_ (optional).

::

    Type a password from password-store in a Wayland environment.

    Usage:
        pass-wl [-h]
        pass-wl [-u|-b|-o] [URL]
        pass-wl -c [-u|-o] [URL]

    Options:
        -u, --user  Type the username instead of the password.
        -b, --both  Type the username and the password separated by a <Tab>.
        -o, --otp   Type the otp code if exists.
        -c, --copy  Copy instead of type.
        -h, --help  Print this help.

    Argument:
        URL         If any, must be the last parameter. pass-wl will try to
                    find only matching values from `pass`.

Note:
=====

I mostly use it with qutebrowser_. Qutebrowser has a userscript called
qute-pass_ that does the same thing but using the builtin `fake-key` command
that is logged (run `$ qutebrowser -l vdebug` to check).

I set up qutebrowser as follow (`pass-wl` should be in your `$PATH`):

.. code:: python

    # in config.py
    config.bind('<Alt-p>', 'mode-enter insert ;; spawn -- pass-wl {url}')
    config.bind('<Alt-u>', 'mode-enter insert ;; spawn -- pass-wl -u {url}')
    config.bind('<Alt-l>', 'mode-enter insert ;; spawn -- pass-wl -b {url}')
    config.bind('<Alt-o>', 'mode-enter insert ;; spawn -- pass-wl -o {url}')
    config.bind('<Alt-p>', 'spawn -- pass-wl    {url}', mode='insert')
    config.bind('<Alt-u>', 'spawn -- pass-wl -u {url}', mode='insert')
    config.bind('<Alt-l>', 'spawn -- pass-wl -b {url}', mode='insert')
    config.bind('<Alt-o>', 'spawn -- pass-wl -o {url}', mode='insert')


.. _qutebrowser:  https://github.com/qutebrowser/qutebrowser
.. _qute-pass:    https://github.com/qutebrowser/qutebrowser/blob/master/misc/userscripts/qute-pass
.. _pass:         https://www.passwordstore.org/
.. _pass-otp:     https://github.com/tadfisher/pass-otp
.. _wtype:        https://github.com/atx/wtype
.. _bemenu:       https://github.com/Cloudef/bemenu
.. _wl-clipboard: https://github.com/bugaevc/wl-clipboard
