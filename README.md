*This module is no longer necessary for doing Real Time Data in Excel with Python.*
*See https://www.pyxll.com/docs/userguide/rtd.html*

exceltypes
==========

The `exceltypes` package is a set of C++ Python types wrapping a sub-set of the Excel COM types.
It is an extension to [pywin32](http://pywin32.sourceforge.net/) and so `pythoncom.PyIUnknown` instances can be cast to `exceltypes` types using the `QueryInterface` method.

The motivation behind this package is that although the Excel object model can be used via the wrappers generated by `win32com`'s makepy wrappers, these all rely on the `IDispatch.Invoke` method and at least one type (`IRTDUpdateEvent`) only works when called via the vtable binding and not when called via its `IDispatch` interface.

### Building

Build using the included `setup.py`. Use the `--help` and `--help-commands` options for more information about available options.

```
python setup.py install
```

### Examples

Cast a `pythoncom.PyIDispatch` object to an `excel.PyIRTDUpdateEvent` object:

```python
import exceltypes

# cast an object to a PyIRTDUpdateEvent instance using QueryInterface
#obj = <a PyIDispatch object passed from Excel>
update_event = obj.QueryInterface(exceltypes.IID_IRTDUpdateEvent)
```

### References
- http://stackoverflow.com/questions/9985512/excel-rtd-server-in-python-not-updating-data
- https://mail.python.org/pipermail/python-win32/2012-April/012207.html
