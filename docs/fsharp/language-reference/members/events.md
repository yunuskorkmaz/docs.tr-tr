---
title: Olaylar
description: Bilgi nasıl F# olayları GUI programlamada önemlidir kullanıcı eylemlerini, işlev çağrıları ilişkilendirmek etkinleştirin.
ms.date: 05/16/2016
ms.openlocfilehash: 8972d9ab358ff9ff903e8bbbe42b74beea683233
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903935"
---
# <a name="events"></a>Olaylar

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları için MSDN sürer.  Docs.microsoft.com API başvuru tamamlanmadı.

Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir. Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.

## <a name="handling-events"></a>Olayları İşleme

Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır. Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir. Bir düğmeyi tıklamak gibi belirli adlandırılmış olaya başvurarak önceden varolan bir olaya özel davranış ekleyebilirsiniz (örneğin, `Click` olayı `Form` sınıfı) ve bunları çağırırken `Add` aşağıdaki kodda gösterildiği gibi yöntemi . Buradan çalıştırırsanız F# Interactive çağrısını `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Türünü `Add` yöntemi `('a -> unit) -> unit`. Bu nedenle, olay işleyicisi yöntemi genellikle olay bağımsız değişkenleri, bir parametre alır ve döndürür `unit`. Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir. Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir. Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir. İçin bir `MouseMove` sistem olayı geçirir bir `System.Windows.Forms.MouseEventArgs` nesnesini `X` ve `Y` işaretçinin konumu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Özel Olaylar Oluşturma

F#olayları tarafından temsil edilir F# [olay](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfını [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimi. `IEvent` kendisini iki başka arabirimin işlevselliğini birleştiren bir arabirimdir `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). Bu nedenle, `Event`s sahip ek işlevinden yanı sıra diğer dillerdeki temsilcilerin eşdeğer bir işlevselliği `IObservable`, anlamına F# olayları olay filtrelemeyi ve kullanma desteği F# birinci sınıf işlevler ve Lambda ifadelerini olay işleyiciler olarak. Bu işlevsellik sağlanır [Olay Modülü](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Yalnızca tüm diğer .NET Framework olayı gibi davranan bir sınıfta bir olay oluşturmak için sınıfa eklemek bir `let` tanımlayan bir `Event` bir sınıfta bir alan olarak. İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz. Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir. Bu üye olmalıdır [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliği. Bir özellik gibi bildirilir ve uygulanması bir çağrı ise [Yayımla](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) olayının özelliği. Sınıfınızın kullanıcıları kullanabileceğiniz `Add` bir işleyici eklemek için yayımlanan olayın yöntemi. Bağımsız değişkeni `Add` yöntemi, bir lambda ifadesi olabilir. Kullanabileceğiniz `Trigger` bağımsız değişkenleri işleyici işlevine geçirme olayı için olay özelliği. Aşağıdaki kod örneği bunu gösterir. Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Çıktı aşağıdaki gibidir:

```
Event1 occurred! Object data: Hello World!
```

Tarafından sağlanan ek işlevsellik `Event` modülü burada gösterilmiştir. Aşağıdaki kod örneği temel kullanışını `Event.create` bir olay ve tetikleyici yöntemi oluşturmak için lambda ifadeleri biçiminde iki olay işleyicileri ekleyin ve ardından her iki lambda ifadesini yürütmek için olayı tetiklersiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Olay Akışını İşleme

Yalnızca kullanarak bir olay için bir olay işleyicisi eklemek yerine [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevi, kullanabileceğiniz işlevler `Event` akışlarını oldukça özelleştirilebilir yollarla olayların modülü. Bunu yapmak için ileriye doğru kanalı kullanın (`|>`) ilk değer işlev çağrısı, bir dizi olarak olayla birlikte ve `Event` modülü izleyen işlev çağrıları olarak çalışır.

Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Gözlemlenebilir modül](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) gözlemlenebilir nesneler üzerinde çalışan benzer işlevleri içerir. Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.

## <a name="implementing-an-interface-event"></a>Bir Arabirim Olayı Uygulama

UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız. Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir. `System.ComponentModel.INotifyPropertyChanged` Tek bir arabirim tanımlar `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` olay. Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:

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

Olayı oluşturucuya bağlamak isterseniz, bunu olması gerektiğinden kod biraz daha karmaşık bir `then` aşağıdaki örnekteki gibi ek bir oluşturucuda engelle:

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

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Olaylar oluşturma ve işleme](../../../../docs/standard/events/index.md)
- [Lambda Expressions: `fun` Anahtar Sözcüğü](../functions/lambda-expressions-the-fun-keyword.md)
- [Control.Event Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control.Event&#60;'T&#62; sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control.Event&#60;'Temsilci' Args&#62; sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)