---
title: Olaylar (F#)
description: "F # olayları nasıl GUI programlamada önemli kullanıcı eylemlerini işlev çağrılarını ilişkilendirmek etkinleştirme hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 28b588f2-0c9e-4c0d-babf-901ed934638a
ms.openlocfilehash: 43ff52134093acbd670d48ea83d40f1e9eb377c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="events"></a><span data-ttu-id="8818a-104">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8818a-104">Events</span></span>

> [!NOTE]
<span data-ttu-id="8818a-105">Bu makalede API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="8818a-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="8818a-106">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="8818a-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="8818a-107">Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8818a-107">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="8818a-108">Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8818a-108">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="8818a-109">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="8818a-109">Handling Events</span></span>
<span data-ttu-id="8818a-110">Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8818a-110">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="8818a-111">Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="8818a-111">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="8818a-112">Bir düğmeye gibi belirli olay ilgi adlandırılmış başvurarak önceden var olan bir olaya özel davranış ekleyebilirsiniz (örneğin, `Click` olayı `Form` sınıfı) ve çağırma `Add` aşağıdaki kodda gösterildiği gibi yöntemi .</span><span class="sxs-lookup"><span data-stu-id="8818a-112">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="8818a-113">Bu F # Etkileşimli çalıştırırsanız, çağrısı atlayın `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="8818a-113">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="8818a-114">Türü `Add` yöntemi `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="8818a-114">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="8818a-115">Bu nedenle, olay işleyicisi yöntemi bir parametre, genellikle olay değişkenlerini alır ve verir `unit`.</span><span class="sxs-lookup"><span data-stu-id="8818a-115">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="8818a-116">Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8818a-116">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="8818a-117">Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="8818a-117">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="8818a-118">Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8818a-118">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="8818a-119">İçin bir `MouseMove` sistem olayı geçirmeden bir `System.Windows.Forms.MouseEventArgs` içeren bir nesne, `X` ve `Y` işaretçinin konumu.</span><span class="sxs-lookup"><span data-stu-id="8818a-119">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="8818a-120">Özel Olaylar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8818a-120">Creating Custom Events</span></span>
<span data-ttu-id="8818a-121">F # olayları temsil F # tarafından [olay](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfı, hangi uygulayan [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8818a-121">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="8818a-122">`IEvent`kendisini diğer iki arabirim işlevlerini birleştiren bir arabirimdir `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="8818a-122">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="8818a-123">Bu nedenle, `Event`s sahip diğer dillerde temsilciler eşdeğer işlevselliğini yanı sıra, ek işlevinden `IObservable`, başka bir deyişle, F # olayları olay filtreleme ve F # birinci sınıf işlevler ve lambda ifadeleri kullanma desteği olay işleyicileri olarak.</span><span class="sxs-lookup"><span data-stu-id="8818a-123">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="8818a-124">Bu işlev sağlanan [Olay Modülü](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="8818a-124">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="8818a-125">Yalnızca tüm diğer .NET Framework olay gibi davranan bir sınıf bir olay oluşturmak için sınıfa eklemek bir `let` tanımlar bağlama bir `Event` bir sınıftaki bir alan olarak.</span><span class="sxs-lookup"><span data-stu-id="8818a-125">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="8818a-126">İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8818a-126">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="8818a-127">Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8818a-127">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="8818a-128">Bu üye olmalıdır [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8818a-128">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="8818a-129">Bir özellik gibi bildirilmiş ve bir çağrı yalnızca kendi uygulamasıdır [Yayımla](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) olay özelliği.</span><span class="sxs-lookup"><span data-stu-id="8818a-129">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="8818a-130">Kullanıcılar sınıfınızın `Add` yayınlanan olay işleyicisi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8818a-130">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="8818a-131">Bağımsız değişken için `Add` yöntemi lambda ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8818a-131">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="8818a-132">Kullanabileceğiniz `Trigger` olay işleyicisi işleve bağımsız değişkenleri geçirme olayı özelliği.</span><span class="sxs-lookup"><span data-stu-id="8818a-132">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="8818a-133">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8818a-133">The following code example illustrates this.</span></span> <span data-ttu-id="8818a-134">Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.</span><span class="sxs-lookup"><span data-stu-id="8818a-134">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="8818a-135">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8818a-135">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="8818a-136">Tarafından sağlanan ek işlevler `Event` modülü burada gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8818a-136">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="8818a-137">Aşağıdaki kod örneğinde temel kullanımını göstermektedir `Event.create` bir olay ve tetikleyici yöntemi oluşturmak için lambda ifadeleri biçiminde iki olay işleyicileri eklemek ve hem lambda ifadeleri yürütülecek olay tetikler.</span><span class="sxs-lookup"><span data-stu-id="8818a-137">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="8818a-138">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="8818a-138">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="8818a-139">Olay Akışını İşleme</span><span class="sxs-lookup"><span data-stu-id="8818a-139">Processing Event Streams</span></span>
<span data-ttu-id="8818a-140">Yalnızca kullanarak bir olayın olay işleyicisi ekleme yerine [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevi, kullanabileceğiniz işlevlerde `Event` üst düzeyde özelleştirilmiş şekillerde olayların işlem akışlara modülü.</span><span class="sxs-lookup"><span data-stu-id="8818a-140">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="8818a-141">Bunu yapmak için ileriye doğru kanal kullanın (`|>`) bir dizi işlev çağrısı, ilk değer olarak olay ile birlikte ve `Event` modülü sonraki işlev çağrısı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="8818a-141">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="8818a-142">Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8818a-142">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="8818a-143">[Observable Modülü](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) observable nesneler üzerinde çalışan benzer işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="8818a-143">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="8818a-144">Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.</span><span class="sxs-lookup"><span data-stu-id="8818a-144">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="8818a-145">Bir Arabirim Olayı Uygulama</span><span class="sxs-lookup"><span data-stu-id="8818a-145">Implementing an Interface Event</span></span>
<span data-ttu-id="8818a-146">UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8818a-146">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="8818a-147">Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8818a-147">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="8818a-148">`System.ComponentModel.INotifyPropertyChanged` Arabirimi tanımlar tek bir `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` olay.</span><span class="sxs-lookup"><span data-stu-id="8818a-148">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="8818a-149">Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8818a-149">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="8818a-150">Olay oluşturucusundaki bağlanacağını istiyorsanız, olay bağlantı olması gerektiğinden kodu biraz daha karmaşıktır bir `then` aşağıdaki örnekteki gibi ek bir oluşturucuda engelle:</span><span class="sxs-lookup"><span data-stu-id="8818a-150">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8818a-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8818a-151">See Also</span></span>
[<span data-ttu-id="8818a-152">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="8818a-152">Members</span></span>](index.md)

[<span data-ttu-id="8818a-153">Olaylar oluşturma ve işleme</span><span class="sxs-lookup"><span data-stu-id="8818a-153">Handling and Raising Events</span></span>](https://msdn.microsoft.com/library/edzehd2t.aspx)

[<span data-ttu-id="8818a-154">Lambda ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="8818a-154">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="8818a-155">Control.Event Modülü</span><span class="sxs-lookup"><span data-stu-id="8818a-155">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="8818a-156">Control.Event &#60;' T &#62; Sınıfı</span><span class="sxs-lookup"><span data-stu-id="8818a-156">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="8818a-157">Control.Event &#60;' Temsilci,'Args &#62; Sınıfı</span><span class="sxs-lookup"><span data-stu-id="8818a-157">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
