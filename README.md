# ASP-GUID
Guids for ASP classic JScript based on M$ implmementation https://support.microsoft.com/en-us/kb/320375
```
var Guid = {
    New : function(format) {
        var format = (format == undefined || String(format) == "undefined" || String(format) == "" || format == null) ? "D" : format;
        if (format == "N") {
            return this.__formatGuid("");
        } else if (format == "D") {
            return this.__formatGuid("-");
        } else {
            return this.__formatGuid("-");
        }
    },
    __formatGuid : function(seperator) {
        seperator = (seperator !== undefined && seperator !== "undefined") ? seperator : "-";
        return  this.__createGUID(8) + seperator +
                this.__createGUID(4) + seperator +
                this.__createGUID(4) + seperator +
                this.__createGUID(4) + seperator +
                this.__createGUID(12);
    },
    __createGUID: function(tmpLength) {
        var tmpCounter=0, tmpGUID = "";
        var strValid = "ABCDEFGHIJKLM0123456789NOPQRSTUVWXYZ";
        for (var tmpCounter = 0; tmpLength > tmpCounter; tmpCounter++) {
            tmpGUID += strValid.substr(Math.random() * strValid.length + 1, 1);
        }
        return tmpGUID;
    }
};

```
Usage.
Guid.New() | Guid.New("D") returns xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Guid.New("N") returns xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
