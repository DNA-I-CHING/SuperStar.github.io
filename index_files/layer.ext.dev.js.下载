$().ready(function() {
    //获取老图片的原图路径
   $("a[href*=_ueditor\\/dialogs\\/showOriginalImg\\.html\\?img\\=]").each(function(i) {
       var _href = $(this).attr("href");
       $(this).attr("href","#");
       $(this).removeAttr("target");
       _href = _href.substring(_href.indexOf("=")+1);
       //"/_ueditor/dialogs/showOriginalImg.html?img=/_upload/article/46/75/e99fc72945928ad0cf21f744c3cb/9ee2ff3c-b98a-4623-afb7-757e8a266205_d.png
        $("img[src*=_upload\\/article\\/]", this).each(function(i) {
            $(this).attr("original-src",_href);
        });
   });
   ////删除老的a链接
   //var html = $("body").html();
   //html = html.replace(/<a[^>]*_ueditor\/dialogs\/showOriginalImg\.html\?img\=[^>]*>(.+?)<\/a>/gi,"$1");
   //$("body").html(html);
});

layer.prompt = function(g, f, j) {
    var i = {},
    g = g || {},
    h = {
        area: ["auto", "auto"],
        offset: [g.top || "", ""],
        title: g.title || "信息",
        dialog: {
            btns: 2,
            type: -1,
            msg: '<input type="' +
            function() {
                return 1 === g.type ? "password": 2 === g.type ? "file": "text"
            } () + '" class="xubox_prompt xubox_form" id="xubox_prompt" value="' + (g.val || "") + '" />',
            yes: function(b) {
                var a = i.prompt.val();
                "" === a ? i.prompt.focus() : a.replace(/\s/g, "").length > (g.length || 1000) ? layer.tips("最多输入" + (g.length || 1000) + "个字数", "#xubox_prompt", 2) : f && f(a, b, i.prompt)
            },
            no: j
        },
        success: function() {
            i.prompt = $("#xubox_prompt"),
            i.prompt.focus()
        }
    };
    return 3 === g.type && (h.dialog.msg = '<textarea class="xubox_prompt xubox_form xubox_formArea" id="xubox_prompt">' + (g.val || "") + "</textarea>"),
    $.layer(h)
},
layer.tab = function(b) {
    var b = b || {},
    f = b.data || [],
    e = {
        type: 1,
        border: [0],
        area: ["auto", "auto"],
        bgcolor: "",
        title: !1,
        shade: b.shade,
        offset: b.offset,
        move: ".xubox_tabmove",
        closeBtn: !1,
        page: {
            html: '<div class="xubox_tab" style="' +
            function() {
                return b.area = b.area || [],
                "width:" + (b.area[0] || "500px") + "; height:" + (b.area[1] || "300px") + '">'
            } () + '<span class="xubox_tabmove"></span>' + '<div class="xubox_tabtit">' +
            function() {
                var g = f.length,
                c = 1,
                h = "";
                if (g > 0) {
                    for (h = '<span class="xubox_tabnow">' + f[0].title + "</span>"; g > c; c++) {
                        h += "<span>" + f[c].title + "</span>"
                    }
                }
                return h
            } () + "</div>" + '<ul class="xubox_tab_main">' +
            function() {
                var g = f.length,
                c = 1,
                h = "";
                if (g > 0) {
                    for (h = '<li class="xubox_tabli xubox_tab_layer">' + (f[0].content || "content未传入") + "</li>"; g > c; c++) {
                        h += '<li class="xubox_tabli">' + (f[c].content || "content未传入") + "</li>"
                    }
                }
                return h
            } () + "</ul>" + '<span class="xubox_tabclose" title="关闭">X</span>' + "</div>"
        },
        success: function(h) {
            var g = $(".xubox_tabtit").children(),
            j = $(".xubox_tab_main").children(),
            i = $(".xubox_tabclose");
            g.on("click",
            function() {
                var d = $(this),
                c = d.index();
                d.addClass("xubox_tabnow").siblings().removeClass("xubox_tabnow"),
                j.eq(c).show().siblings().hide()
            }),
            i.on("click",
            function() {
                layer.close(h.attr("times"))
            })
        }
    };
    return $.layer(e)
},
layer.photos = function(r) {
    var q, p, o, n, m, l, k, j, initialScale = 1, currentScale, dx, dy, px, py, isSupportTouch = "ontouchend" in document ? true : false;;
    if (r = r || {},
    q = {
        imgIndex: 1,
        end: null,
        html: $("html")
    },
    p = $(window), o = r.json, n = r.page, o) {
        if (m = o.data, 1 !== o.status) {
            return layer.msg("未请求到数据", 2, 8),
            void 0
        }
        if (q.imgLen = m.length, !(m.length > 0)) {
            return layer.msg("没有任何图片", 2, 8),
            void 0
        }
        q.thissrc = m[o.start].src,
        q.pid = m[o.start].pid,
        q.imgsname = o.title || "",
        q.name = m[o.start].name,
        q.imgIndex = o.start + 1
    } else {
        l = $(n.parent).find(n.imgs ? "img" + n.imgs: "img").not(".imgnav .img img"),
        k = l.eq(n.start),
        q.thissrc = k.attr("layer-img") || k.attr("src"),
        q.originalsrc = k.attr("original-src") || q.thissrc,
        q.pid = k.attr("pid"),
        q.scale = k.attr("data-scale"),
        q.imgLen = l.length,
        q.imgsname = n.title || "",
        q.name = k.attr("alt"),
        q.imgIndex = n.start + 1
    }
    return j = {
        type: 1,
        border: [0],
        area: [(r.html ? 915 : 600) + "px", "auto"],
        title: !1,
        shade: [0.9, "#000", !0],
        shadeClose: !0,
        offset: ["10px", ""],
        bgcolor: "",
        page: {
            html: '<div class="xubox_bigimg"><div class="xubox_imgbox xubox_loading"><img src="' + q.thissrc + '" alt="' + (q.name || "") + '" layer-pid="' + (q.pid || "") + '"></div><div class="xubox_imgsee">' +
            function() {
                return q.imgLen > 1 ? '<a href="" class="xubox_iconext xubox_prev"></a><a href="" class="xubox_iconext xubox_next"></a>': ""
            } () + '<div class="xubox_imgtool"><span class="xubox_imgoriginal"><a href="'+q.originalsrc+'" titlt="查看原图" target="_blank">原图</a></span></div><div class="xubox_imgbar"><span class="xubox_imgtit"><a href="javascript:;">' + q.imgsname + " </a><em>" + q.imgIndex + "/" + q.imgLen + "</em></span></div></div></div>" +
            function() {
                return r.html ? '<div class="xubox_intro">' + r.html + "</div>": ""
            } ()
        },
        success: function(b) {
            q.bigimg = b.find(".xubox_bigimg"),
            q.imgbox = q.bigimg.find('.xubox_imgbox'),
            q.imgsee = q.bigimg.find(".xubox_imgsee"),
            q.imgbar = q.imgsee.find(".xubox_imgbar"),
            q.imgtit = q.imgbar.find(".xubox_imgtit"),
            q.imgtool = q.imgsee.find(".xubox_imgtool"),
            q.imgoriginal = q.imgtool.find(".xubox_imgoriginal"),
            q.layero = b;
            var d = q.imgs = q.bigimg.find("img");
            clearTimeout(q.timerr),
            q.timerr = setTimeout(function() {
                $("html").css({"overflow":"hidden"}).attr("layer-full", q.index)
            },
            10),
            d.load(function() {
                q.imgarea = [d.outerWidth(), d.outerHeight()],
                q.imgbox.removeClass('xubox_loading'),
                q.resize(b)
            }),
            q.event()
        },
        end: function() {
            layer.closeAll(),
            q.end = !0
        }
    },
    q.event = function() {
        q.bigimg.hover(function() {
            q.imgsee.show()
        },
        function() {
            q.imgsee.hide()
        }),
        q.imgbox.mousedown(function(){
            q.imgsee.toggle()
        }),
        j.imgprev = function() {
            q.imgIndex--,
            q.imgIndex < 1 && (q.imgIndex = q.imgLen),
            q.tabimg()
        },
        q.bigimg.find(".xubox_prev").on("click",
        function(b) {
            b.preventDefault(),
            j.imgprev()
        }),
        j.imgnext = function() {
            q.imgIndex++,
            q.imgIndex > q.imgLen && (q.imgIndex = 1),
            q.tabimg()
        },
        q.bigimg.find(".xubox_next").on("click",
        function(b) {
            b.preventDefault(),
            j.imgnext()
        }),
        $(document).keyup(function(b) {
            if (!q.end) {
                var d = b.keyCode;
                b.preventDefault(),
                37 === d ? j.imgprev() : 39 === d ? j.imgnext() : 27 === d && layer.close(q.index)
            }
        });
        q.touch = function(){

            j.relocal = function(){
                if(dx>q.imgbox.width()/2+(initialScale-1)*q.imgs.width()/2){
                    dx = q.imgbox.width()/2+(initialScale-1)*q.imgs.width()/2;
                }
                if(dx< (q.imgbox.width()/2-q.imgs.width()-(initialScale-1)*q.imgs.width()/2)){
                    dx = q.imgbox.width()/2-q.imgs.width()-(initialScale-1)*q.imgs.width()/2;
                }
                if(dy>q.imgbox.height()/2+(initialScale-1)*q.imgs.height()/2){
                    dy = q.imgbox.height()/2+(initialScale-1)*q.imgs.height()/2
                }
                if(dy< (q.imgbox.height()/2-q.imgs.height()-(initialScale-1)*q.imgs.height()/2)){
                    dy = q.imgbox.height()/2-q.imgs.height()-(initialScale-1)*q.imgs.height()/2
                }
                q.imgs.stop(true,false).animate({left:dx,top:dy},300);
            }

            if(n.scale){
                touch.on(q.bigimg[0], 'pinch', function(ev){
                    currentScale = ev.scale - 1;
                    currentScale = initialScale + currentScale;
                    currentScale = currentScale > 5 ? 5 : currentScale;
                    currentScale = currentScale < 1 ? 1 : currentScale;
                    q.imgs[0].style.webkitTransform = 'scale(' + currentScale + ')';
                }),
                touch.on(q.bigimg[0], 'pinchend', function(ev){ 
                    if(initialScale>currentScale){
                        dx = px*(currentScale-1)/2+px;
                        dy = py*(currentScale-1)/2+py;
                        q.imgs.stop(true,false).animate({left:dx, top:dy}, 500);    
                    }
                    initialScale = currentScale;
                    j.relocal();
                }),
                touch.on(q.imgs[0], 'touchstart', function(ev){
                    ev.preventDefault();
                    q.imgsee.show();
                }),
                dx = q.imgs.position().left,
                dy = q.imgs.position().top,
                touch.on(q.imgs[0], 'drag', function(ev){
                    dx = dx || 0;
                    dy = dy || 0;   
                    var offx = dx + ev.x;
                    var offy = dy + ev.y;
                    $(this).stop(true,false).css({left:offx,top:offy});
                    j.relocal();
                }),
                touch.on(q.imgs[0], 'dragend', function(ev){
                    dx += ev.x;
                    dy += ev.y;
                    j.relocal();
                })
            }else{
                q.bigimg.find(".xubox_next,.xubox_prev").hide();
                touch.on(q.imgbox[0], 'touchstart', function(ev){
                    ev.preventDefault();
                    q.imgsee.show();
                }),
                touch.on(q.imgbox[0], 'swipeleft', function(ev){
                    console.log(ev.type);
                    j.imgnext();
                }),
                touch.on(q.imgbox[0], 'swiperight', function(ev){
                    console.log(ev.type);
                    j.imgprev();
                })
            }
        }
        if(isSupportTouch){

            if(typeof touch === "undefined"){
                layer.use("extend/touch.min.js",function(){
                    q.touch();
                });
            }else{
                q.touch();
            }

        }
        q.tabimg = function() {
            var f, h, d, c, b, a;
            initialScale = 1,
            q.imgs.removeAttr("style"),
            o ? (b = m[q.imgIndex - 1], f = b.src, d = b.pid, c = b.name) : (a = l.eq(q.imgIndex - 1), f = a.attr("layer-img") || a.attr("src"), h = a.attr("original-src") || f, d = a.attr("layer-pid") || "", c = a.attr("alt") || ""),
            q.imgs.attr({
                src: f,
                "layer-pid": d,
                alt: c
            }),
            q.imgtit.find("em").text(q.imgIndex + "/" + q.imgLen),
            q.imgoriginal.find("a").attr("href", h),
            q.imgsee.show(),
            r.tab && r.tab({
                pid: d,
                name: c
            })
        };
    },
    q.resize = function(i) {
        var b, a = [],
        h = {},
        c = [p.width(), p.height()];
        h.limit = c[0] - c[0] / c[1] * (60 * c[0] / c[1]),
        h.limit < 600 && (h.limit = 600);
        var b = [h.limit, c[1] - 20];
        b[0] = r.html ? b[0] : b[0] - 300,
        b[0] = b[0] == 300 ? c[0] : b[0],
        b[0] = b[0] - 16,
        layer.area(q.index, {
            width: b[0] + (r.html ? 15 : 0),
            height: b[1]
        }),
        h.flwidth = b[0],
        a[0] = h.flwidth / b[1],
        a[1] = q.imgarea[0] / q.imgarea[1];
        if (a[1] > a[0]) {
            q.imgarea[0] > h.flwidth ? q.imgs.css({
                width: h.flwidth,
                height: "auto"
            }) : q.imgs.css({
                width: q.imgarea[0],
                height: "auto"
            })
        } else {
            q.imgarea[1] > b[1] ? q.imgs.css({
                width: "auto",
                height: b[1]
            }) : q.imgs.css({
                width: "auto",
                height: q.imgarea[1]
            })
        }
        py = (b[1] - q.imgs.outerHeight()) / 2,
        px = (b[0] - q.imgs.outerWidth()) / 2,
        q.imgs.css({
            top: py,
            left: px,
            visibility: "visible"
        }),
        dx = q.imgs.position().left,
        dy = q.imgs.position().top,
        q.imgbox.css({
            width: h.flwidth,
            height: b[1]
        }),
        q.bigimg.css({
            width: h.flwidth,
            height: b[1],
            "background-color": r.bgcolor
        }),
        r.html && i.find(".xubox_intro").css({
            height: b[1]
        }),
        h = null,
        c = null,
        b = null
    },
    p.on("resize",
    function() {
        q.end || (q.timer && clearTimeout(q.timer), q.timer = setTimeout(function() {
            q.resize(q.layero)
        },
        200))
    }),
    q.index = $.layer(j),
    q.index
},
layer.photosPage = function(d) {
    var c = {};
    c.run = function(a) {
        layer.photos({
            html: d.html,
            success: d.success,
            page: {
                title: d.title,
                id: d.id,
                start: a,
                scale:d.scale,
                parent: d.parent,
                imgs: d.imgs
            }
        })
    },
    d = d || {},
    $(d.parent).find(d.imgs ? d.imgs: "img").not(".imgnav .img img").each(function(b) {
        $(this).on("click",
        function() {
            c.run(b)
        })
    })
};
layer.use("skin/layer.ext.css",
function() {
    layer.ext && layer.ext()
});