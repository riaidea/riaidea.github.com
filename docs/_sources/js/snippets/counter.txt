


统计代码
======================

.. code-block:: javascript

    var Counter = {
        webclick: {
            track: function(word){
                var key = Cookie.get("ClubAuth");
                var data = "key=" + key + "&refe=" + escape(word) + "&random=" + Math.random();
                setTimeout(function () {
                    var img = new Image();
                    img.onload = function(){
                        img.onload = null;
                    }
                    img.src = "http://webclick.yeshj.com/clickgather.ashx?counter=dict_huaci&" + data;
                }, 10);
            }
        },

        ga: {
            //TODO: async bug
            get: function(){
                var gaq = window._gaq = window._gaq || {};
                if (!gaq._getAsyncTracker){
                    var ga = document.createElement('script'); 
                    ga.type = 'text/javascript'; 
                    ga.async = true;
                    ga.src = ('https:' == window.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
                    var s = document.getElementsByTagName('script')[0];
                    s.parentNode.insertBefore(ga, s);
                }
                return gaq;
            },
            account: function(id){
                this.get().push(["dt._setAccount", id]);
            },
            track: function(category, action, label, value){
                this.get().push(['dt._trackEvent', category, action, label, value]);
            }
        }
    };