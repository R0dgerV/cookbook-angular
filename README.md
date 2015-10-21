# Директивы

Дополнениe к поле INPUT что бы выполнялась функция по Enter

``
        .directive('myEnter', function () {
            return function (scope, element, attrs) {
                element.bind("keydown keypress", function (event) {
                    if(event.which === 13) {
                        scope.$apply(function (){
                            scope.$eval(attrs.myEnter);
                        });

                        event.preventDefault();
                    }
                });
            };
        })
``

Confirm для элементов html

``
        .directive('ngReallyClick', [function() {
            return {
                restrict: 'A',
                link: function(scope, element, attrs) {
                    element.bind('click', function() {
                        var message = attrs.ngReallyMessage;
                        if (message && confirm(message)) {
                            scope.$apply(attrs.ngReallyClick);
                        }
                    });
                }
            }
        }])
``