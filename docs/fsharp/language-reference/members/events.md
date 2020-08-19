---
title: Ekinlikler
description: 'F # olaylarının, GUI programlamasında önemli olan Kullanıcı eylemleriyle işlev çağrılarını ilişkilendirmenizi nasıl sağladığını öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 42783255412d56c6ff6729694c31d0868ed99633
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559199"
---
# <a name="events"></a><span data-ttu-id="78acb-103">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="78acb-103">Events</span></span>

<span data-ttu-id="78acb-104">Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="78acb-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="78acb-105">Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="78acb-105">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="78acb-106">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="78acb-106">Handling Events</span></span>

<span data-ttu-id="78acb-107">Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="78acb-107">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="78acb-108">Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="78acb-108">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="78acb-109">Aşağıdaki kodda gösterildiği gibi, bir düğmeye tıklama gibi, var olan adlandırılmış olaya (örneğin, `Click` `Form` sınıfının olayı) başvurarak ve yöntemini çağırarak, önceden var olan bir olaya özel davranış ekleyebilirsiniz `Add` .</span><span class="sxs-lookup"><span data-stu-id="78acb-109">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="78acb-110">Bunu F# Etkileşimli çalıştırırsanız, çağrısı atlayın `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` .</span><span class="sxs-lookup"><span data-stu-id="78acb-110">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="78acb-111">`Add`Yöntemin türü `('a -> unit) -> unit` .</span><span class="sxs-lookup"><span data-stu-id="78acb-111">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="78acb-112">Bu nedenle, olay işleyicisi yöntemi bir parametre alır, genellikle olay bağımsız değişkenleri ve döndürür `unit` .</span><span class="sxs-lookup"><span data-stu-id="78acb-112">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="78acb-113">Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78acb-113">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="78acb-114">Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="78acb-114">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="78acb-115">Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="78acb-115">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="78acb-116">Bir `MouseMove` olay için sistem, `System.Windows.Forms.MouseEventArgs` `X` işaretçinin ve konumunu içeren bir nesnesi geçirir `Y` .</span><span class="sxs-lookup"><span data-stu-id="78acb-116">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="78acb-117">Özel Olaylar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="78acb-117">Creating Custom Events</span></span>

<span data-ttu-id="78acb-118">F # olayları, [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) arabirimini uygulayan f # [olay](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) türü tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="78acb-118">F# events are represented by the F# [Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) type, which implements the [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) interface.</span></span> <span data-ttu-id="78acb-119">`IEvent` , iki diğer arabirimin işlevselliğini birleştiren bir arabirimdir `System.IObservable<'T>` ve [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span><span class="sxs-lookup"><span data-stu-id="78acb-119">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span></span> <span data-ttu-id="78acb-120">Bu nedenle, `Event` diğer dillerdeki temsilcilerle ilgili eşdeğer işlevlere ek olarak, `IObservable` f # olaylarının olay filtrelemeyi desteklediği ve olay Işleyicileri olarak f # birinci sınıf işlevlerini ve Lambda ifadelerini kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78acb-120">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="78acb-121">Bu işlevsellik [olay modülünde](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html)verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78acb-121">This functionality is provided in the [Event module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span></span>

<span data-ttu-id="78acb-122">Tüm diğer .NET Framework olayları gibi davranan bir sınıfta bir olay oluşturmak için, sınıf `let` içinde bir alan olarak tanımlayan bağlama sınıfına ekleyin `Event` .</span><span class="sxs-lookup"><span data-stu-id="78acb-122">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="78acb-123">İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78acb-123">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="78acb-124">Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78acb-124">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="78acb-125">Bu üye [Clienevent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) özniteliğine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78acb-125">This member should have the [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) attribute.</span></span> <span data-ttu-id="78acb-126">Bir özellik gibi bildirilmiştir ve bunun uygulanması, etkinliğin [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) özelliğine yapılan bir çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="78acb-126">It is declared like a property and its implementation is just a call to the [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) property of the event.</span></span> <span data-ttu-id="78acb-127">Sınıfınızın kullanıcıları, `Add` bir işleyici eklemek için yayımlanan olayın yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="78acb-127">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="78acb-128">Yöntemi için bağımsız değişken `Add` bir lambda ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="78acb-128">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="78acb-129">Olayı `Trigger` yükseltmek ve bağımsız değişkenleri işleyici işlevine iletmek için olay özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78acb-129">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="78acb-130">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="78acb-130">The following code example illustrates this.</span></span> <span data-ttu-id="78acb-131">Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.</span><span class="sxs-lookup"><span data-stu-id="78acb-131">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="78acb-132">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="78acb-132">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="78acb-133">Modül tarafından sunulan ek işlevsellik `Event` burada gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="78acb-133">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="78acb-134">Aşağıdaki kod örneği, `Event.create` bir olay ve tetikleyici yöntemi oluşturmak için temel kullanımını gösterir, lambda ifadeleri biçiminde iki olay işleyicisi ekleyin ve ardından her iki lambda ifadesini yürütmek için olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="78acb-134">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="78acb-135">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="78acb-135">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="78acb-136">Olay Akışını İşleme</span><span class="sxs-lookup"><span data-stu-id="78acb-136">Processing Event Streams</span></span>

<span data-ttu-id="78acb-137">Event [. Add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) işlevini kullanarak bir olay için yalnızca bir olay işleyicisi eklemek yerine, `Event` olayların akışlarını yüksek düzeyde özelleştirilmiş yöntemlerle işlemek için modüldeki işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78acb-137">Instead of just adding an event handler for an event by using the [Event.add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="78acb-138">Bunu yapmak için, `|>` bir dizi işlev çağrısı içindeki ilk değer olarak olay ile birlikte ilet kanalını () kullanın ve `Event` Modül sonraki işlev çağrıları gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="78acb-138">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="78acb-139">Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78acb-139">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="78acb-140">[Observable modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) , observable nesnelerinde çalışan benzer işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="78acb-140">The [Observable module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="78acb-141">Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.</span><span class="sxs-lookup"><span data-stu-id="78acb-141">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="78acb-142">Bir Arabirim Olayı Uygulama</span><span class="sxs-lookup"><span data-stu-id="78acb-142">Implementing an Interface Event</span></span>

<span data-ttu-id="78acb-143">UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="78acb-143">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="78acb-144">Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="78acb-144">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="78acb-145">`System.ComponentModel.INotifyPropertyChanged`Arabirim tek bir olayı tanımlar `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` .</span><span class="sxs-lookup"><span data-stu-id="78acb-145">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="78acb-146">Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="78acb-146">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="78acb-147">Olayı oluşturucuda bağlamak isterseniz, aşağıdaki örnekte olduğu gibi, olay kancasının ek bir oluşturucuda bir blokta olması gerektiğinden, kod biraz daha karmaşıktır `then` .</span><span class="sxs-lookup"><span data-stu-id="78acb-147">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="78acb-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78acb-148">See also</span></span>

- [<span data-ttu-id="78acb-149">Üyeler</span><span class="sxs-lookup"><span data-stu-id="78acb-149">Members</span></span>](index.md)
- [<span data-ttu-id="78acb-150">Olaylar Oluşturma ve İşleme</span><span class="sxs-lookup"><span data-stu-id="78acb-150">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="78acb-151">Lambda Ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="78acb-151">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
