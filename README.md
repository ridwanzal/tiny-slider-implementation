## Implement tiny slider dynamic load
Tiny slider as replacer for owl carousel, bring minimal and great solutions without depend on jquery.
This tiny library is behave like previous owl carousel with almost the same results. But for spesific use case
this library need to be tweak according to repo documentation and author suggestions, below is the example
for dynamic load using tiny slider. For static content that already serve in the dom, it works well, but tiny slider
not good for dynamic content, so the instance need to be initiate when it's invoked. This relate to components like modal, view on click, tab and etc.

### Tiny slider instance on bootstrap modal

Initiate tns instance when bootstrap is shown, and destroy when modal already kill/ hidden from dom. This will generate right behaviour. So, i think for you that comes with the same issue. You can use this as sample implementation

```
        let slider = null;
        $('.my-modal').on('shown.bs.modal', function (event) {
            let slider = tns({
                container: '.js-slide-modal',
                items: 3,
                nav: false,
                slideBy: 1,
                mouseDrag: true,
                autoWidth: true,
                autoplay: true
            });
            $('.js-slide-modal').show();
            slider.refresh();
        });

        $('.my-modal').on('shown.bs.modal', function (event) { 
            slider.destroy();
        });
```
