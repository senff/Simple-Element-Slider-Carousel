SImple-Element-Slider-Carousel
==============================

A simple slider carousel for (list) items


DROPPING CODE - WORK ON THIS LATER:

$(".faq-slider").msSlider(5);

-- ORIGINAL:

// === CUSTOM DVSLIDER PLUGIN ================================================================================================================================================ 

(function ($) {
    $.fn.msSlider = function (visItems) {
        var me = $(this);
        var totalItems = me.find('ul').children().length;
        leftpos = 0;
        leftentry = 1;
        rightentry = visItems;
        step = 100 / totalItems;

        me.addClass('msSlider');
        me.prepend('<a href="#" class="slide-move slide-left disabled"></a><a href="#" class="slide-move slide-right"></a>');
        me.find('ul').wrap('<div class="msWrapper">');
        me.find('ul').css('width', (100 / visItems * totalItems) + '%');
        me.find('ul li').css('width', step + '%');

        if (totalItems <= visItems) {
            $('.slide-move').addClass('disabled');
            me.find('ul').css('width', '100%');
        }

        me.find('.slide-left').on('click', function (l) {
            l.preventDefault();
            if (!me.find('.slide-left').hasClass('disabled')) {
                leftentry = leftentry - 1;
                rightentry = leftentry - visItems - 1;
                leftpos = leftpos + (100 / visItems);
                $(me).find('ul').animate({ "left": leftpos + '%' }, 300);
                buttons();
            }
        });

        me.find('.slide-right').on('click', function (r) {
            r.preventDefault();
            if (!me.find('.slide-right').hasClass('disabled')) {
                leftentry = leftentry + 1;
                rightentry = leftentry + visItems - 1;
                leftpos = leftpos - (100 / visItems);
                $(me).find('ul').animate({ "left": leftpos + '%' }, 300);
                buttons();
            }
        });

        function buttons() {
            if (leftentry == 1) {
                me.find('.slide-left').addClass('disabled');
            }
            else {
                me.find('.slide-left').removeClass('disabled');
            }

            if (rightentry == totalItems) {
                me.find('.slide-right').addClass('disabled');
            }
            else {
                me.find('.slide-right').removeClass('disabled');
            }
        };
    };
}(jQuery));

==============================================================================================
-- OPTIMIzED: 

    function (n) {
        n.fn.msSlider = function (t) {
            function u() {
                leftentry == 1 ? i.find(".slide-left").addClass("disabled") : i.find(".slide-left").removeClass("disabled");
                rightentry == r ? i.find(".slide-right").addClass("disabled") : i.find(".slide-right").removeClass("disabled")
            }
            var i = n(this),
                r = i.find("ul").children().length;
            leftpos = 0;
            leftentry = 1;
            rightentry = t;
            step = 100 / r;
            i.addClass("msSlider");
            i.prepend('<a href="#" class="slide-move slide-left disabled"><\/a><a href="#" class="slide-move slide-right"><\/a>');
            i.find("ul").wrap('<div class="msWrapper">');
            i.find("ul").css("width", 100 / t * r + "%");
            i.find("ul li").css("width", step + "%");
            r <= t && (n(".slide-move").addClass("disabled"), i.find("ul").css("width", "100%"));
            i.find(".slide-left").on("click", function (r) {
                r.preventDefault();
                i.find(".slide-left").hasClass("disabled") || (leftentry = leftentry - 1, rightentry = leftentry - t - 1, leftpos = leftpos + 100 / t, n(i).find("ul").animate({
                    left: leftpos + "%"
                }, 300), u())
            });
            i.find(".slide-right").on("click", function (r) {
                r.preventDefault();
                i.find(".slide-right").hasClass("disabled") || (leftentry = leftentry + 1, rightentry = leftentry + t - 1, leftpos = leftpos - 100 / t, n(i).find("ul").animate({
                    left: leftpos + "%"
                }, 300), u())
            })
        }
    }(jQuery);
