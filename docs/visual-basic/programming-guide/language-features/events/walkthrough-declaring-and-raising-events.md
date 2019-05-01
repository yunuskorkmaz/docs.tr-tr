---
title: (Visual Basic) olay bildirme ve oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973096"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="be00c-102">İzlenecek yol: (Visual Basic) olay bildirme ve oluşturma</span><span class="sxs-lookup"><span data-stu-id="be00c-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="be00c-103">Bu izlenecek yolda bildirme ve adlı bir sınıf için bir olay yapmayı gösteren `Widget`.</span><span class="sxs-lookup"><span data-stu-id="be00c-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="be00c-104">Adımları tamamladıktan sonra Yardımcısı konuyu okumak isteyebilirsiniz [izlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), olaylarından kullanmak nasıl `Widget` uygulamada durum bilgilerini sağlamak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="be00c-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="be00c-105">Pencere sınıfı</span><span class="sxs-lookup"><span data-stu-id="be00c-105">The Widget Class</span></span>  
 <span data-ttu-id="be00c-106">Sahip olduğunuz süre varsayar bir `Widget` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be00c-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="be00c-107">`Widget` Sınıfında bir yöntem çalıştırmak uzun sürebilir ve uygulamanızın tamamlama göstergesi tür yerleştirebilir istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="be00c-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="be00c-108">Elbette yapabileceğiniz `Widget` nesne bir tamamlanma yüzdesi iletişim kutusu gösterir, ancak daha sonra bu iletişim kutusu, kullandığınız her projede takılmış `Widget` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be00c-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="be00c-109">Bir nesne tanıtıcısına kullanıcı arabirimini kullanan uygulamaya bildirmek için iyi bir nesne tasarım ilkesini olan — bir form veya iletişim kutusu yönetmek için tek amaç nesnenin olmadığı sürece.</span><span class="sxs-lookup"><span data-stu-id="be00c-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="be00c-110">Amacı `Widget` eklemek daha iyi, bu nedenle diğer görevleri gerçekleştirmek için bir `PercentDone` olay ve let çağıran yordam `Widget`kullanıcının, yöntemleri işleyen olayı ve görüntü durumunu güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="be00c-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="be00c-111">`PercentDone` Olay ayrıca görev iptal etmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="be00c-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="be00c-112">Bu konu için kod örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be00c-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="be00c-113">Yeni bir Visual Basic Windows uygulaması projesi açın ve adlı bir form oluşturun `Form1`.</span><span class="sxs-lookup"><span data-stu-id="be00c-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="be00c-114">İki düğme ve bir etiketin ekleme `Form1`.</span><span class="sxs-lookup"><span data-stu-id="be00c-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="be00c-115">Aşağıdaki tabloda gösterildiği gibi nesneleri ad.</span><span class="sxs-lookup"><span data-stu-id="be00c-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="be00c-116">Nesne</span><span class="sxs-lookup"><span data-stu-id="be00c-116">Object</span></span>|<span data-ttu-id="be00c-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="be00c-117">Property</span></span>|<span data-ttu-id="be00c-118">Ayar</span><span class="sxs-lookup"><span data-stu-id="be00c-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="be00c-119">Başlangıç görevi</span><span class="sxs-lookup"><span data-stu-id="be00c-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="be00c-120">İptal</span><span class="sxs-lookup"><span data-stu-id="be00c-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="be00c-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="be00c-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="be00c-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="be00c-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="be00c-123">Üzerinde **proje** menüsünde seçin **sınıfı Ekle** adlı bir sınıf eklemek için `Widget.vb` projeye.</span><span class="sxs-lookup"><span data-stu-id="be00c-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="be00c-124">Pencere sınıfı için bir olay bildirmek için</span><span class="sxs-lookup"><span data-stu-id="be00c-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="be00c-125">Kullanım `Event` bir olayı bildirmek için anahtar sözcüğü `Widget` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be00c-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="be00c-126">Bir olay olabilir Not `ByVal` ve `ByRef` bağımsız olarak `Widget`'s `PercentDone` olay gösterir:</span><span class="sxs-lookup"><span data-stu-id="be00c-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="be00c-127">Çağrı nesnesi aldığında bir `PercentDone` olay `Percent` tamamlanmış görev yüzdesi bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="be00c-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="be00c-128">`Cancel` Bağımsız değişkeni ayarlanabilir `True` olayı başlatan yöntem iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="be00c-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be00c-129">Yordamlar, aşağıdaki istisnalarla birlikte bağımsız olarak olay bağımsız değişkenleri bildirebilirsiniz: Olaylar olamaz `Optional` veya `ParamArray` bağımsız değişkenleri ve olaylar, dönüş değerleri yok.</span><span class="sxs-lookup"><span data-stu-id="be00c-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="be00c-130">`PercentDone` Olayı tarafından oluşturulur `LongTask` yöntemi `Widget` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be00c-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="be00c-131">`LongTask` iki bağımsız değişkeni alır: sürenin uzunluğunu yöntemi önce en az zaman aralığını yanı sıra iş çıkarıyor amaçları olan kişilerle tanışabilirsiniz `LongTask` yükseltmek için duraklamaları `PercentDone` olay.</span><span class="sxs-lookup"><span data-stu-id="be00c-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="be00c-132">PercentDone olayı yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="be00c-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="be00c-133">Erişimini basitleştirmek için `Timer` Bu sınıf tarafından kullanılan özellik Ekle bir `Imports` sınıfı modülünüzde bildirimler bölümünü üstüne deyimi yukarıda `Class Widget` deyimi.</span><span class="sxs-lookup"><span data-stu-id="be00c-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="be00c-134">Aşağıdaki kodu ekleyin `Widget` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="be00c-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="be00c-135">Uygulamanızı çağırdığında `LongTask` yöntemi `Widget` sınıfı harekete geçirirse `PercentDone` olay her `MinimumInterval` saniye.</span><span class="sxs-lookup"><span data-stu-id="be00c-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="be00c-136">Olay döndürüldüğünde `LongTask` denetler `Cancel` bağımsız değişken ayarlanmıştır `True`.</span><span class="sxs-lookup"><span data-stu-id="be00c-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="be00c-137">Bazı bildirimler burada gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be00c-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="be00c-138">Kolaylık olması için `LongTask` yordam varsayar bildiğiniz önceden görevin ne kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="be00c-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="be00c-139">Neredeyse hiç durum budur.</span><span class="sxs-lookup"><span data-stu-id="be00c-139">This is almost never the case.</span></span> <span data-ttu-id="be00c-140">Görevleri bile boyutu öbeklere bölünmesi zor olabilir ve kullanıcılara en sık şeylere yalnızca bir şeyler oluyor göstergesidir aldıkları önce geçen süre miktarıdır.</span><span class="sxs-lookup"><span data-stu-id="be00c-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="be00c-141">Bu örnekte başka bir kusur anlaþýlmaz.</span><span class="sxs-lookup"><span data-stu-id="be00c-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="be00c-142">`Timer` Özelliği gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, yalnızca gece yarısından önce başlattıysanız uygulama takılı.</span><span class="sxs-lookup"><span data-stu-id="be00c-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="be00c-143">Sürenin ölçülmesine daha dikkatli bir yaklaşım gibi bu sınır koşulları dikkate alın veya gibi özellikleri kullanarak bunları sorunlarını tamamen önlemek `Now`.</span><span class="sxs-lookup"><span data-stu-id="be00c-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="be00c-144">Şimdi `Widget` sınıf olayları oluşturma, sonraki adım adım kılavuz taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be00c-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="be00c-145">[İzlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) nasıl kullanılacağını gösteren `WithEvents` bir olay işleyicisi ile ilişkilendirilecek `PercentDone` olay.</span><span class="sxs-lookup"><span data-stu-id="be00c-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be00c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be00c-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="be00c-147">İzlenecek yol: Olayları işleme</span><span class="sxs-lookup"><span data-stu-id="be00c-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="be00c-148">Olaylar</span><span class="sxs-lookup"><span data-stu-id="be00c-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
