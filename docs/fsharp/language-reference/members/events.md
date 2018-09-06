---
title: Olaylar (F#)
description: 'F # olayları, GUI programlamada önemlidir kullanıcı eylemlerini, işlev çağrıları ilişkilendirmek nasıl olanak öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: ce547bc9ec7b5e0ef9a7492c0889bb690e3040c2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871939"
---
# <a name="events"></a><span data-ttu-id="e38cc-103">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e38cc-103">Events</span></span>

> [!NOTE]
<span data-ttu-id="e38cc-104">Bu makaledeki API başvuru bağlantıları için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="e38cc-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="e38cc-105">Docs.microsoft.com API başvuru tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="e38cc-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e38cc-106">Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="e38cc-107">Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="e38cc-108">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="e38cc-108">Handling Events</span></span>

<span data-ttu-id="e38cc-109">Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="e38cc-110">Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="e38cc-111">Bir düğmeyi tıklamak gibi belirli adlandırılmış olaya başvurarak önceden varolan bir olaya özel davranış ekleyebilirsiniz (örneğin, `Click` olayı `Form` sınıfı) ve bunları çağırırken `Add` aşağıdaki kodda gösterildiği gibi yöntemi .</span><span class="sxs-lookup"><span data-stu-id="e38cc-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="e38cc-112">Bu F # Interactive'den çalıştırırsanız, çağrı atlamak `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="e38cc-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="e38cc-113">Türünü `Add` yöntemi `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="e38cc-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="e38cc-114">Bu nedenle, olay işleyicisi yöntemi genellikle olay bağımsız değişkenleri, bir parametre alır ve döndürür `unit`.</span><span class="sxs-lookup"><span data-stu-id="e38cc-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="e38cc-115">Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="e38cc-116">Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="e38cc-117">Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="e38cc-118">İçin bir `MouseMove` sistem olayı geçirir bir `System.Windows.Forms.MouseEventArgs` nesnesini `X` ve `Y` işaretçinin konumu.</span><span class="sxs-lookup"><span data-stu-id="e38cc-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="e38cc-119">Özel Olaylar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e38cc-119">Creating Custom Events</span></span>

<span data-ttu-id="e38cc-120">F # olayları temsil edilir F # tarafından [olay](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfını [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e38cc-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="e38cc-121">`IEvent` kendisini iki başka arabirimin işlevselliğini birleştiren bir arabirimdir `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="e38cc-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="e38cc-122">Bu nedenle, `Event`s sahip ek işlevinden yanı sıra diğer dillerdeki temsilcilerin eşdeğer bir işlevselliği `IObservable`, yani F # olaylarının olay filtrelemeyi ve F # birinci sınıf işlevlerini ve lambda ifadeleri kullanma desteği olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="e38cc-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="e38cc-123">Bu işlevsellik sağlanır [Olay Modülü](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="e38cc-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="e38cc-124">Yalnızca tüm diğer .NET Framework olayı gibi davranan bir sınıfta bir olay oluşturmak için sınıfa eklemek bir `let` tanımlayan bir `Event` bir sınıfta bir alan olarak.</span><span class="sxs-lookup"><span data-stu-id="e38cc-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="e38cc-125">İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e38cc-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="e38cc-126">Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="e38cc-127">Bu üye olmalıdır [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e38cc-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="e38cc-128">Bir özellik gibi bildirilir ve uygulanması bir çağrı ise [Yayımla](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) olayının özelliği.</span><span class="sxs-lookup"><span data-stu-id="e38cc-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="e38cc-129">Sınıfınızın kullanıcıları kullanabileceğiniz `Add` bir işleyici eklemek için yayımlanan olayın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e38cc-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="e38cc-130">Bağımsız değişkeni `Add` yöntemi, bir lambda ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="e38cc-131">Kullanabileceğiniz `Trigger` bağımsız değişkenleri işleyici işlevine geçirme olayı için olay özelliği.</span><span class="sxs-lookup"><span data-stu-id="e38cc-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="e38cc-132">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-132">The following code example illustrates this.</span></span> <span data-ttu-id="e38cc-133">Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="e38cc-134">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e38cc-134">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="e38cc-135">Tarafından sağlanan ek işlevsellik `Event` modülü burada gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="e38cc-136">Aşağıdaki kod örneği temel kullanışını `Event.create` bir olay ve tetikleyici yöntemi oluşturmak için lambda ifadeleri biçiminde iki olay işleyicileri ekleyin ve ardından her iki lambda ifadesini yürütmek için olayı tetiklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e38cc-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="e38cc-137">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-137">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="e38cc-138">Olay Akışını İşleme</span><span class="sxs-lookup"><span data-stu-id="e38cc-138">Processing Event Streams</span></span>

<span data-ttu-id="e38cc-139">Yalnızca kullanarak bir olay için bir olay işleyicisi eklemek yerine [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevi, kullanabileceğiniz işlevler `Event` akışlarını oldukça özelleştirilebilir yollarla olayların modülü.</span><span class="sxs-lookup"><span data-stu-id="e38cc-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="e38cc-140">Bunu yapmak için ileriye doğru kanalı kullanın (`|>`) ilk değer işlev çağrısı, bir dizi olarak olayla birlikte ve `Event` modülü izleyen işlev çağrıları olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="e38cc-141">Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="e38cc-142">[Gözlemlenebilir modül](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) gözlemlenebilir nesneler üzerinde çalışan benzer işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="e38cc-143">Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.</span><span class="sxs-lookup"><span data-stu-id="e38cc-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="e38cc-144">Bir Arabirim Olayı Uygulama</span><span class="sxs-lookup"><span data-stu-id="e38cc-144">Implementing an Interface Event</span></span>

<span data-ttu-id="e38cc-145">UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e38cc-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="e38cc-146">Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="e38cc-147">`System.ComponentModel.INotifyPropertyChanged` Tek bir arabirim tanımlar `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` olay.</span><span class="sxs-lookup"><span data-stu-id="e38cc-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="e38cc-148">Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e38cc-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
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

<span data-ttu-id="e38cc-149">Olayı oluşturucuya bağlamak isterseniz, bunu olması gerektiğinden kod biraz daha karmaşık bir `then` aşağıdaki örnekteki gibi ek bir oluşturucuda engelle:</span><span class="sxs-lookup"><span data-stu-id="e38cc-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
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

## <a name="see-also"></a><span data-ttu-id="e38cc-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e38cc-150">See also</span></span>

- [<span data-ttu-id="e38cc-151">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e38cc-151">Members</span></span>](index.md)
- [<span data-ttu-id="e38cc-152">Olaylar oluşturma ve işleme</span><span class="sxs-lookup"><span data-stu-id="e38cc-152">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="e38cc-153">Lambda ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e38cc-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="e38cc-154">Control.Event Modülü</span><span class="sxs-lookup"><span data-stu-id="e38cc-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="e38cc-155">Control.Event&#60;'T&#62; sınıfı</span><span class="sxs-lookup"><span data-stu-id="e38cc-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="e38cc-156">Control.Event&#60;'Temsilci' Args&#62; sınıfı</span><span class="sxs-lookup"><span data-stu-id="e38cc-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
