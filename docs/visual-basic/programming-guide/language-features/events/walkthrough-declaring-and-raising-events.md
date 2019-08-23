---
title: Olayları bildirme ve oluşturma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956332"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="9d6c0-102">İzlenecek yol: Olayları bildirme ve oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d6c0-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="9d6c0-103">Bu izlenecek yol, adlı `Widget`bir sınıf için olayların nasıl bildirileceğini ve oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="9d6c0-104">Adımları tamamladıktan sonra yardımcı konusunu okumak isteyebilirsiniz, [izlenecek yol: Bir uygulamada](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)durum bilgilerini sağlamak için `Widget` nesnelerden olayları nasıl kullanacağınızı gösteren olayları işleme.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="9d6c0-105">Pencere öğesi sınıfı</span><span class="sxs-lookup"><span data-stu-id="9d6c0-105">The Widget Class</span></span>  
 <span data-ttu-id="9d6c0-106">Bir `Widget` sınıfa sahip olduğunuz andaki varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="9d6c0-107">`Widget` Sınıfınız, yürütülmesi uzun sürebilecek bir yönteme sahiptir ve uygulamanızın bir tür tamamlanma göstergesi koyabilmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="9d6c0-108">Kuşkusuz `Widget` , nesneyi yüzde-tam-Tamam iletişim kutusu olarak gösterebilirsiniz, ancak bu iletişim kutusuyla `Widget` sınıfı kullandığınız her projede bu iletişim kutusuyla birlikte kalmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="9d6c0-109">Nesne tasarımının iyi bir prensibi, nesnenin tüm amacı bir form veya iletişim kutusunu yönetmediği için, bir nesneyi kullanan uygulamanın kullanıcı arabirimini işlemesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="9d6c0-110">Amacı `Widget` diğer görevleri gerçekleştirmelidir, bu nedenle bir `PercentDone` olay eklemek ve yöntemlerini çağıran `Widget`yordamın bu olayı işleme ve durum güncelleştirmelerini görüntülemesini sağlamak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="9d6c0-111">`PercentDone` Olay, görevi iptal etmek için bir mekanizma da sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="9d6c0-112">Bu konunun kod örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9d6c0-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="9d6c0-113">Yeni bir Visual Basic Windows uygulaması projesi açın ve adlı `Form1`bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="9d6c0-114">İçin `Form1`iki düğme ve bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="9d6c0-115">Nesneleri aşağıdaki tabloda gösterildiği gibi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="9d6c0-116">Nesne</span><span class="sxs-lookup"><span data-stu-id="9d6c0-116">Object</span></span>|<span data-ttu-id="9d6c0-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="9d6c0-117">Property</span></span>|<span data-ttu-id="9d6c0-118">Ayar</span><span class="sxs-lookup"><span data-stu-id="9d6c0-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="9d6c0-119">Başlangıç görevi</span><span class="sxs-lookup"><span data-stu-id="9d6c0-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="9d6c0-120">İptal</span><span class="sxs-lookup"><span data-stu-id="9d6c0-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="9d6c0-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="9d6c0-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="9d6c0-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="9d6c0-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="9d6c0-123">Proje menüsünde , projeye adlı `Widget.vb` bir sınıf eklemek için **Sınıf Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="9d6c0-124">Pencere öğesi sınıfı için bir olay bildirmek için</span><span class="sxs-lookup"><span data-stu-id="9d6c0-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="9d6c0-125">`Widget` Sınıfında bir olay bildirmek için anahtarsözcüğünükullanın.`Event`</span><span class="sxs-lookup"><span data-stu-id="9d6c0-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="9d6c0-126">Olayın, `ByVal` olaygösterdiğigibi`PercentDone` `ByRef` `Widget`, ve bağımsız değişkenlerine sahip olabileceğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="9d6c0-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="9d6c0-127">Çağıran nesne bir `PercentDone` olay aldığında `Percent` , bağımsız değişken tamamlanmış görevin yüzdesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="9d6c0-128">Bağımsız değişkeni, olayı oluşturan yöntemi `True` iptal etmek için olarak ayarlanabilir. `Cancel`</span><span class="sxs-lookup"><span data-stu-id="9d6c0-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d6c0-129">Aşağıdaki özel durumlarla birlikte, yordam bağımsız değişkenlerini yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: Olaylar veya `Optional` `ParamArray` bağımsız değişkenlere sahip olamaz ve olayların dönüş değerleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="9d6c0-130">Olay, `Widget` sınıfının `LongTask` yöntemi tarafından tetiklenir. `PercentDone`</span><span class="sxs-lookup"><span data-stu-id="9d6c0-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="9d6c0-131">`LongTask`iki bağımsız değişken alır: yöntemin iş yapmakta olduğu sürenin uzunluğu ve `LongTask` `PercentDone` olayı yükseltmek için duraklamadan önce en kısa zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="9d6c0-132">PercentDone olayını yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="9d6c0-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="9d6c0-133">Bu sınıf tarafından kullanılan `Timer` özelliğe erişimi basitleştirmek için, `Class Widget` sınıfının üst kısmındaki bildirim `Imports` bölümünün üst kısmına bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="9d6c0-134">`Widget` Sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9d6c0-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="9d6c0-135">Uygulamanız `LongTask` yöntemini çağırdığında `Widget` , sınıfı `PercentDone` olayı her `MinimumInterval` saniye yükseltir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="9d6c0-136">Olay döndüğünde, `LongTask` `Cancel` bağımsız değişkenin olarak `True`ayarlanmış olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="9d6c0-137">Burada birkaç bildirimler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="9d6c0-138">Kolaylık olması için, `LongTask` yordamda görevin ne kadar süreceğine ilişkin daha fazla bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="9d6c0-139">Bu neredeyse hiçbir durum değildir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-139">This is almost never the case.</span></span> <span data-ttu-id="9d6c0-140">Görevleri bile eşit ölçekli parçalara bölmek zor olabilir ve genellikle kullanıcıların en önemli bir şeyi, bir şeyin meydana geldiğinin bir göstergesi olmadan önce geçen süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="9d6c0-141">Bu örnekte başka bir kusuru açığa çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="9d6c0-142">`Timer` Özelliği, gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, uygulama gece yarısından önce başlatılmışsa, uygulama takılmış olur.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="9d6c0-143">Bu süreyi ölçmeye yönelik daha dikkatli bir yaklaşım, gibi özellikleri `Now`kullanarak, bunun dikkate alınması veya bunların tamamen olmaması gibi sınır koşullarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="9d6c0-144">Artık `Widget` sınıfın olayları tetiklemediğini, sonraki izlenecek yolu izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="9d6c0-145">[İzlenecek yol: Olayları](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) işleme `WithEvents` ,`PercentDone` olay işleyicisini olayla ilişkilendirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6c0-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="9d6c0-147">İzlenecek yol: Olayları işleme</span><span class="sxs-lookup"><span data-stu-id="9d6c0-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="9d6c0-148">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9d6c0-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
