# Submitter
> [Documentation](../README.md) ▸ [API Reference](API.md) ▸ [Dataflow](Dataflow.md) ▸ **Submitter**

`Submitter<'T>` is a special kind of input node in the [Dataflow](Dataflow.md)
layer. Its purpose is to allow punctual events such as, typically, button
clicks, to participate in the graph.

The purpose of a submitter is to provide a [View](View.md) which gets its value
from a given input view, but only gets updated when punctual events are
`Trigger`ed.

```fsharp
type Submitter<'T> =
    member View : View<'T>
    member Trigger : unit -> unit
    member Input : View<'T>

type Submitter =
    static member Create : input: View<'T> -> init: 'T -> Submitter<'T>
    static member View : Submitter<'T> -> View<'T>
    static member Trigger : Submitter<'T> -> unit
    static member Input : Submitter<'T> -> View<'T>
```

<a name="Create" href="#Create">#</a> Submitter.**Create** : `input: View<'T> -> init: 'T -> Submitter<'T>`

Create a submitter for the given input [View](View.md). The initial value of the
submitter's output `View` is `init`. Then, every time `Trigger` is called, the
value of the output `View` is updated to be the current value of `input`.

<a name="View" href="#View">#</a> submitter.**View** : `View<'T>`

Get the output view of a submitter.

<a name="Trigger" href="#Trigger">#</a> submitter.**Trigger** : `unit -> unit`

Trigger a submitter, causing its output view to get the value from its input view.

<a name="Input" href="#Input">#</a> submitter.**Input** : `View<'T>`

Get the input view of a submitter.

<a name="SView" href="#SView">#</a> Submitter.**View** : `Submitter<'T> -> View<'T>`

Equivalent to <a href="#View">submitter.View</a>.

<a name="STrigger" href="#STrigger">#</a> Submitter.**Trigger** : `Submitter<'T> -> unit`

Equivalent to <a href="#Trigger">submitter.Trigger()</a>.

<a name="SInput" href="#SInput">#</a> Submitter.**Input** : `Submitter<'T> -> View<'T>`

Equivalent to <a href="#Input">submitter.Input</a>.
