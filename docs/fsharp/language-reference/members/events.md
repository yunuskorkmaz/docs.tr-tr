---
title: Olaylar
description: 'F # olaylarının, GUI programlamasında önemli olan Kullanıcı eylemleriyle işlev çağrılarını ilişkilendirmenizi nasıl sağladığını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 682686ba58d0f7a56e7da2585e6507ccd0156a44
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854938"
---
# <a name="events"></a><span data-ttu-id="7b35c-103">Olaylar</span><span class="sxs-lookup"><span data-stu-id="7b35c-103">Events</span></span>

<span data-ttu-id="7b35c-104">Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="7b35c-105">Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-105">Events can also be triggered by your applications or by the operating system.</span></span>

> [!NOTE]
> <span data-ttu-id="7b35c-106">F # için docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7b35c-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="7b35c-107">Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="7b35c-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="handling-events"></a><span data-ttu-id="7b35c-108">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="7b35c-108">Handling Events</span></span>

<span data-ttu-id="7b35c-109">Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="7b35c-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="7b35c-110">Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="7b35c-111">Aşağıdaki kodda gösterildiği gibi, bir düğmeye tıklama gibi, var olan adlandırılmış olaya (örneğin, `Click` `Form` sınıfının olayı) başvurarak ve yöntemini çağırarak, önceden var olan bir olaya özel davranış ekleyebilirsiniz `Add` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="7b35c-112">Bunu F# Etkileşimli çalıştırırsanız, çağrısı atlayın `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="7b35c-113">`Add`Yöntemin türü `('a -> unit) -> unit` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="7b35c-114">Bu nedenle, olay işleyicisi yöntemi bir parametre alır, genellikle olay bağımsız değişkenleri ve döndürür `unit` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="7b35c-115">Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="7b35c-116">Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="7b35c-117">Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="7b35c-118">Bir `MouseMove` olay için sistem, `System.Windows.Forms.MouseEventArgs` `X` işaretçinin ve konumunu içeren bir nesnesi geçirir `Y` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="7b35c-119">Özel Olaylar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b35c-119">Creating Custom Events</span></span>

<span data-ttu-id="7b35c-120">F # olayları, [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimini uygulayan f # [olay](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="7b35c-121">`IEvent`, iki diğer arabirimin işlevselliğini birleştiren bir arabirimdir `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="7b35c-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="7b35c-122">Bu nedenle, `Event` diğer dillerdeki temsilcilerle ilgili eşdeğer işlevlere ek olarak, `IObservable` f # olaylarının olay filtrelemeyi desteklediği ve olay Işleyicileri olarak f # birinci sınıf işlevlerini ve Lambda ifadelerini kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="7b35c-123">Bu işlevsellik [olay modülünde](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="7b35c-124">Tüm diğer .NET Framework olayları gibi davranan bir sınıfta bir olay oluşturmak için, sınıf `let` içinde bir alan olarak tanımlayan bağlama sınıfına ekleyin `Event` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="7b35c-125">İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b35c-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="7b35c-126">Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="7b35c-127">Bu üye [Clienevent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliğine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b35c-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="7b35c-128">Bir özellik gibi bildirilmiştir ve bunun uygulanması, etkinliğin [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) özelliğine yapılan bir çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="7b35c-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="7b35c-129">Sınıfınızın kullanıcıları, `Add` bir işleyici eklemek için yayımlanan olayın yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="7b35c-130">Yöntemi için bağımsız değişken `Add` bir lambda ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="7b35c-131">Olayı `Trigger` yükseltmek ve bağımsız değişkenleri işleyici işlevine iletmek için olay özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b35c-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="7b35c-132">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-132">The following code example illustrates this.</span></span> <span data-ttu-id="7b35c-133">Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="7b35c-134">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7b35c-134">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="7b35c-135">Modül tarafından sunulan ek işlevsellik `Event` burada gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="7b35c-136">Aşağıdaki kod örneği, `Event.create` bir olay ve tetikleyici yöntemi oluşturmak için temel kullanımını gösterir, lambda ifadeleri biçiminde iki olay işleyicisi ekleyin ve ardından her iki lambda ifadesini yürütmek için olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="7b35c-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="7b35c-137">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-137">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="7b35c-138">Olay Akışını İşleme</span><span class="sxs-lookup"><span data-stu-id="7b35c-138">Processing Event Streams</span></span>

<span data-ttu-id="7b35c-139">Event [. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevini kullanarak bir olay için yalnızca bir olay işleyicisi eklemek yerine, `Event` olayların akışlarını yüksek düzeyde özelleştirilmiş yöntemlerle işlemek için modüldeki işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b35c-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="7b35c-140">Bunu yapmak için, `|>` bir dizi işlev çağrısı içindeki ilk değer olarak olay ile birlikte ilet kanalını () kullanın ve `Event` Modül sonraki işlev çağrıları gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7b35c-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="7b35c-141">Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="7b35c-142">[Observable modülü](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) , observable nesnelerinde çalışan benzer işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="7b35c-143">Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.</span><span class="sxs-lookup"><span data-stu-id="7b35c-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="7b35c-144">Bir Arabirim Olayı Uygulama</span><span class="sxs-lookup"><span data-stu-id="7b35c-144">Implementing an Interface Event</span></span>

<span data-ttu-id="7b35c-145">UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="7b35c-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="7b35c-146">Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b35c-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="7b35c-147">`System.ComponentModel.INotifyPropertyChanged`Arabirim tek bir olayı tanımlar `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="7b35c-148">Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="7b35c-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="7b35c-149">Olayı oluşturucuda bağlamak isterseniz, aşağıdaki örnekte olduğu gibi, olay kancasının ek bir oluşturucuda bir blokta olması gerektiğinden, kod biraz daha karmaşıktır `then` .</span><span class="sxs-lookup"><span data-stu-id="7b35c-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7b35c-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b35c-150">See also</span></span>

- [<span data-ttu-id="7b35c-151">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b35c-151">Members</span></span>](index.md)
- [<span data-ttu-id="7b35c-152">Olaylar Oluşturma ve İşleme</span><span class="sxs-lookup"><span data-stu-id="7b35c-152">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="7b35c-153">Lambda Ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7b35c-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="7b35c-154">Control. Event modülü</span><span class="sxs-lookup"><span data-stu-id="7b35c-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="7b35c-155">Control. Event&#60; 'T&#62; sınıfı</span><span class="sxs-lookup"><span data-stu-id="7b35c-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="7b35c-156">Control. Event&#60; ' Delegate, ' args&#62; Class</span><span class="sxs-lookup"><span data-stu-id="7b35c-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
