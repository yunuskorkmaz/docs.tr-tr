---
title: Olaylar
description: Olay çağrılarını F# , GUI programlamasında önemli olan Kullanıcı eylemleriyle ilişkilendirmenizi nasıl sağlayacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ad60aff318832ab3ba5e9f7c43928898e171cea8
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543631"
---
# <a name="events"></a><span data-ttu-id="2332d-103">Olaylar</span><span class="sxs-lookup"><span data-stu-id="2332d-103">Events</span></span>

> [!NOTE]
> <span data-ttu-id="2332d-104">Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="2332d-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="2332d-105">Docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="2332d-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="2332d-106">Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2332d-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="2332d-107">Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2332d-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="2332d-108">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="2332d-108">Handling Events</span></span>

<span data-ttu-id="2332d-109">Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="2332d-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="2332d-110">Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="2332d-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="2332d-111">Aşağıdaki kodda gösterildiği gibi, bir düğmeye tıklama gibi, ilgili belirli bir olaya (örneğin, `Form` sınıfının `Click` olayı) başvurarak ve `Add` yöntemini çağırarak, önceden var olan bir olaya özel davranış ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2332d-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="2332d-112">Bunu etkileşimli 'den F# çalıştırırsanız, `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`çağrısını atlayın.</span><span class="sxs-lookup"><span data-stu-id="2332d-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="2332d-113">`Add` yönteminin türü `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="2332d-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="2332d-114">Bu nedenle, olay işleyicisi yöntemi genellikle olay bağımsız değişkenlerini bir parametre alır ve `unit`döndürür.</span><span class="sxs-lookup"><span data-stu-id="2332d-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="2332d-115">Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2332d-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="2332d-116">Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="2332d-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="2332d-117">Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2332d-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="2332d-118">`MouseMove` bir olay için sistem, işaretçinin `X` ve `Y` konumunu içeren bir `System.Windows.Forms.MouseEventArgs` nesnesi geçirir.</span><span class="sxs-lookup"><span data-stu-id="2332d-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="2332d-119">Özel Olaylar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2332d-119">Creating Custom Events</span></span>

<span data-ttu-id="2332d-120">F#olaylar, [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimini F# uygulayan [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="2332d-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="2332d-121">`IEvent`, `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)olmak üzere iki diğer arabirimin işlevselliğini birleştiren bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="2332d-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="2332d-122">Bu nedenle, `Event`s, diğer dillerdeki temsilcilerin eşdeğer işlevlerine `IObservable`ek olarak, F# olayların olay filtrelemesini desteklediği ve olay işleyicileri olarak birinci sınıf işlevleri ve Lambda ifadelerini F# kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2332d-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="2332d-123">Bu işlevsellik [olay modülünde](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2332d-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="2332d-124">Tüm diğer .NET Framework olayları gibi davranan bir sınıfta bir olay oluşturmak için, sınıf içinde bir `Event` alan olarak bir tanımlayan `let` bağlama sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2332d-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="2332d-125">İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2332d-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="2332d-126">Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2332d-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="2332d-127">Bu üye [Clienevent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliğine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2332d-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="2332d-128">Bir özellik gibi bildirilmiştir ve bunun uygulanması, etkinliğin [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) özelliğine yapılan bir çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="2332d-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="2332d-129">Sınıfınızın kullanıcıları, bir işleyici eklemek için yayımlanan olayın `Add` yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2332d-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="2332d-130">`Add` yönteminin bağımsız değişkeni bir lambda ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2332d-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="2332d-131">Olayı yükseltmek için olayın `Trigger` özelliğini kullanabilir ve bağımsız değişkenleri işleyici işlevine geçirerek.</span><span class="sxs-lookup"><span data-stu-id="2332d-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="2332d-132">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2332d-132">The following code example illustrates this.</span></span> <span data-ttu-id="2332d-133">Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.</span><span class="sxs-lookup"><span data-stu-id="2332d-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="2332d-134">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2332d-134">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="2332d-135">`Event` modülü tarafından sunulan ek işlevler burada gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2332d-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="2332d-136">Aşağıdaki kod örneği, bir olay ve tetikleyici yöntemi oluşturmak için `Event.create` temel kullanımını gösterir, lambda ifadeleri biçiminde iki olay işleyicisi ekler ve ardından her iki lambda ifadesini yürütmek için olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="2332d-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="2332d-137">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2332d-137">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="2332d-138">Olay Akışını İşleme</span><span class="sxs-lookup"><span data-stu-id="2332d-138">Processing Event Streams</span></span>

<span data-ttu-id="2332d-139">Event [. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevini kullanarak bir olay için yalnızca bir olay işleyicisi eklemek yerine, olayların akışlarını yüksek düzeyde özelleştirilmiş yollarla işlemek için `Event` modülündeki işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2332d-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="2332d-140">Bunu yapmak için, bir dizi işlev çağırmalarda ilk değer olarak olay ile birlikte ilet kanalını (`|>`) ve `Event` modülü sonraki işlev çağrıları gibi işlevlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2332d-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="2332d-141">Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2332d-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="2332d-142">[Observable modülü](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) , observable nesnelerinde çalışan benzer işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2332d-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="2332d-143">Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.</span><span class="sxs-lookup"><span data-stu-id="2332d-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="2332d-144">Bir Arabirim Olayı Uygulama</span><span class="sxs-lookup"><span data-stu-id="2332d-144">Implementing an Interface Event</span></span>

<span data-ttu-id="2332d-145">UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="2332d-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="2332d-146">Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2332d-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="2332d-147">`System.ComponentModel.INotifyPropertyChanged` arabirimi tek bir `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` olayını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2332d-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="2332d-148">Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2332d-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="2332d-149">Olayı oluşturucuda bağlamak isterseniz, aşağıdaki örnekte olduğu gibi, olay kancasının ek bir oluşturucuda `then` bloğunda olması gerektiğinden, kod biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="2332d-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2332d-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2332d-150">See also</span></span>

- [<span data-ttu-id="2332d-151">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2332d-151">Members</span></span>](index.md)
- [<span data-ttu-id="2332d-152">Olayları işleme ve oluşturma</span><span class="sxs-lookup"><span data-stu-id="2332d-152">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="2332d-153">Lambda Ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="2332d-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="2332d-154">Control. Event modülü</span><span class="sxs-lookup"><span data-stu-id="2332d-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="2332d-155">Control. Event&#60;'t&#62; sınıfı</span><span class="sxs-lookup"><span data-stu-id="2332d-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="2332d-156">Control. Event&#60;' Delegate, ' args&#62; Class</span><span class="sxs-lookup"><span data-stu-id="2332d-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
