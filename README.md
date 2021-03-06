protosum-lib
=============

Basic libraries that take advantage of protosum.

protosum.event
____________________
ABOUT:
  AS3 like event handling.

USAGE:

  - see jsdoc for updated documentation
  - new PCEventDispatcher(); // Creates and event dispatcher instance
  - window.CustomEvent = ProtoSum('CustomEvent', PCEvent); // Extends class PCEvent to create a custom event.

 PCEventDispatcher methods:

    - see jsdoc

 PCEvent methos:

    - preventDefault()

        * stops event queue execution after this handlerFunction finishes.

  Define events like you would do in acstionscript. See example.


EXAMPLE:

    var CustomEvent = ProtoSum('CustomEvent', PCEvent); (function() {
        var proto = CustomEvent.prototype;

        proto.name = "customevent";

        proto.__init__ = function(data) {
            this.data = data;
        }

    })();

    var C = ProtoSum(A, B); (function() {
        var proto = C.prototype;

        proto.someVar = "somveValue";

        proto.customeEventHandler = function(event) {
            log("C.customEvent", "event.data = ", event.data, "this.someVar = ",this.someVar);
        }

    })();

    var ed = new PCEventDispatcher();

    ed.bind(CustomEvent, c.customeEventHandler, c);
    ed.trigger(new CustomEvent("custom event data")); // C.customeEventHandler gets called

    ed.unbind(CustomEvent, c.customeEventHandler, c);
    ed.trigger(new CustomEvent("custom event data")); // Nothing happens


CONSIDERATIONS: