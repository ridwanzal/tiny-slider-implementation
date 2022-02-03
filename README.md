# Implement tiny slider dynamic load
As replacer for owl carousel, tiny slider bring minimal and great solutions without depend on jquery.
This tiny library is behave like previous owl carousel with almost the same results, but for spesific use case,
this library need to be tweak according to repo documentation and author suggestions. So, I made an example about, how to implement
dynamic load using tiny slider library. It worked well for static content, but not for dynamic load. So we need to initiate the instance when the event was invoked. This issue was related to components like : modal, view on click, tab and etc.

Original Repository : 
<a target="_blank" href="https://github.com/ganlanyuan/tiny-slider">tiny slider</a>

Related issues: <br/>
https://github.com/ganlanyuan/tiny-slider/issues/223 <br/>
https://github.com/ganlanyuan/tiny-slider/issues/157 <br/>
https://github.com/ganlanyuan/tiny-slider/issues/242
                         
### Tiny slider instance on bootstrap modal
Below, the example of, how to implement and mimic the behaviour when using tiny slider for dynamic load.
Initiate tns instance when bootstrap is shown, and destroy when modal already kill/ hidden from the dom. This will generate correct behaviour. 
So, I think for you that comes with the same issue, you can use this as sample implementation. Thankyou

```
let sliderModal = null;
$('.my-modal').on('shown.bs.modal', function (event) {
    sliderModal = tns({
        container: '.js-slide-modal',
        items: 3,
        nav: false,
        slideBy: 1,
        mouseDrag: true,
        autoWidth: true,
        autoplay: true
    });
    $('.js-slide-modal').show();
    sliderModal.refresh();
});

$('.my-modal').on('shown.bs.modal', function (event) { 
    sliderModal.destroy();
});
```
