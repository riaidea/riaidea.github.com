
Flash插入代码
=====================

.. code-block:: javascript

    _installSoundPlayer: function(container, id, vars){
        container = container || document.body;
        id = id || "hjdext_sound_player";
        vars = vars || "";
        var file = "http://dict.hjenglish.com/flash/sound2.swf";
        
        var obj;
        //create flash object, use classid for IE only
        var isIE = navigator.userAgent.toLowerCase().indexOf("msie") != -1;
        if(isIE) obj = "<object classid='clsid:d27cdb6e-ae6d-11cf-96b8-444553540000'";
        else obj = "<object type='application/x-shockwave-flash' data='"+ file +"'";
        obj += " width='1' height='1' id='" + id + "' name='" + id + "'>";
        //bug: doesn't play sound when first load in IE
        if(isIE) obj += "<param name='movie' value='"+ file + "?r=" + Math.random() +"' />";
        obj += "<param name='flashvars' value='" + vars + "' />";
        obj += "<param name='allowScriptAccess' value='always' />";
        obj += "<param name='wmode' value='transparent' />";
        obj += "</object>";
        
        var span = document.createElement("span");
        span.id = id + "_wrapper";
        span.style.cssText = "width:0;height:0;margin:0;padding:0;border:0;position:absolute;";
        span.innerHTML = obj;
        container.appendChild(span);
    }