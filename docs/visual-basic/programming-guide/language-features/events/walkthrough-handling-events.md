---
title: İşleme olaylar (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1743e5f5d9dcdf83ab646407cd1fcdc77ff71cd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="007bb-102">İzlenecek yol: Olayları İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="007bb-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="007bb-103">Bu olayları ile çalışmak nasıl gösteren iki konuları saniyedir.</span><span class="sxs-lookup"><span data-stu-id="007bb-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="007bb-104">İlk konu [izlenecek yol: bildiren ve yükseltmeyi olayları](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), bildirme ve olaylarının arttığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="007bb-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="007bb-105">Bu bölümde, bunlar gerçekleştiğinde olayları işlemek nasıl göstermek için bu gözden geçirme sınıfından ve form kullanır.</span><span class="sxs-lookup"><span data-stu-id="007bb-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="007bb-106">`Widget` Sınıf örneği, geleneksel olay işleme deyimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="007bb-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="007bb-107">Visual Basic olaylar ile çalışmak için başka teknikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="007bb-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="007bb-108">Bir alıştırma kullanmak için bu örnek değiştirebilirsiniz `AddHandler` ve `Handles` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="007bb-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="007bb-109">Pencere sınıfı PercentDone olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="007bb-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="007bb-110">Aşağıdaki kodda yerleştirin `Form1`:</span><span class="sxs-lookup"><span data-stu-id="007bb-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="007bb-111">`WithEvents` Anahtar sözcüğü belirtir değişkeni `mWidget` nesnenin olayları işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007bb-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="007bb-112">Nesne Oluşturulacak sınıfın adını sağlayarak nesne türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="007bb-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="007bb-113">Değişkeni `mWidget` içinde bildirilen `Form1` çünkü `WithEvents` değişkenleri sınıf düzeyinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="007bb-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="007bb-114">Bu, bunların içine yerleştirin sınıf türü ne olursa olsun geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="007bb-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="007bb-115">Değişkeni `mblnCancel` iptal etmek için kullanılan `LongTask` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="007bb-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="007bb-116">Bir olay işlemek için kod yazma</span><span class="sxs-lookup"><span data-stu-id="007bb-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="007bb-117">Bir değişken kullanarak bildirme hemen `WithEvents`, değişken adı sınıfının sol aşağı açılan listede görüntülenir **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="007bb-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="007bb-118">Seçtiğinizde, `mWidget`, `Widget` sınıfının olayları sağda açılan listede görünür.</span><span class="sxs-lookup"><span data-stu-id="007bb-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="007bb-119">Bir olay seçerek görüntüler önek ile ilgili olay yordamını `mWidget` ve alt çizgi.</span><span class="sxs-lookup"><span data-stu-id="007bb-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="007bb-120">İle ilişkili tüm olay yordamları bir `WithEvents` değişkeni, değişken adı öneki olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="007bb-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="007bb-121">Bir olay işleme</span><span class="sxs-lookup"><span data-stu-id="007bb-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="007bb-122">Seçin `mWidget` sol aşağı açılan listeden **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="007bb-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="007bb-123">Seçin `PercentDone` sağda açılan listeden olay.</span><span class="sxs-lookup"><span data-stu-id="007bb-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="007bb-124">**Kod düzenleyicisinde** açılır `mWidget_PercentDone` olay yordamı.</span><span class="sxs-lookup"><span data-stu-id="007bb-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="007bb-125">**Kod düzenleyicisinde** yararlıdır, ancak gerekli değil, yeni olay işleyicileri ekleme.</span><span class="sxs-lookup"><span data-stu-id="007bb-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="007bb-126">Bu kılavuzda, doğrudan erişimli olay işleyicileri yalnızca doğrudan kodunuza kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="007bb-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="007bb-127">Aşağıdaki kodu ekleyin `mWidget_PercentDone` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="007bb-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="007bb-128">Her `PercentDone` olayı, olay yordamı içinde tamamlanma görüntüler bir `Label` denetim.</span><span class="sxs-lookup"><span data-stu-id="007bb-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="007bb-129">`DoEvents` Yöntemi çizilecek, etiket sağlar ve ayrıca kullanıcı tıklatın fırsatı sunar **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="007bb-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="007bb-130">İçin aşağıdaki kodu ekleyip `Button2_Click` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="007bb-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="007bb-131">Kullanıcı tıklarsa **iptal** düğmesini basılı `LongTask` çalıştığından, `Button2_Click` olay yürütüldüğünde hemen `DoEvents` deyimi olay işleme oluşmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="007bb-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="007bb-132">Sınıf düzeyi değişkeni `mblnCancel` ayarlanır `True`ve `mWidget_PercentDone` olay sonra onu sınar ve ayarlar `ByRef Cancel` bağımsız değişkeni `True`.</span><span class="sxs-lookup"><span data-stu-id="007bb-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="007bb-133">Bir nesneye bir WithEvents değişkeni bağlanma</span><span class="sxs-lookup"><span data-stu-id="007bb-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="007bb-134">`Form1` Şimdi işlemek üzere ayarlanmış bir `Widget` nesnenin olaylar.</span><span class="sxs-lookup"><span data-stu-id="007bb-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="007bb-135">Kalan tek şey bulmak için bir `Widget` yere.</span><span class="sxs-lookup"><span data-stu-id="007bb-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="007bb-136">Bir değişken bildirme zaman `WithEvents` tasarım zamanında hiçbir nesne ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="007bb-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="007bb-137">A `WithEvents` yalnızca herhangi bir başka nesne değişken gibi bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="007bb-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="007bb-138">Bir nesne oluşturmak ve onunla başvuru atamak kullandığınız `WithEvents` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="007bb-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="007bb-139">Bir nesne oluşturmak ve ona başvuru atamak için</span><span class="sxs-lookup"><span data-stu-id="007bb-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="007bb-140">Seçin **(Form1 olayları)** sol aşağı açılan listeden **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="007bb-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="007bb-141">Seçin `Load` sağda açılan listeden olay.</span><span class="sxs-lookup"><span data-stu-id="007bb-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="007bb-142">**Kod düzenleyicisinde** açılır `Form1_Load` olay yordamı.</span><span class="sxs-lookup"><span data-stu-id="007bb-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="007bb-143">İçin aşağıdaki kodu ekleyip `Form1_Load` oluşturmak için olay yordamı `Widget`:</span><span class="sxs-lookup"><span data-stu-id="007bb-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="007bb-144">Bu kod yürütüldüğünde, Visual Basic oluşturur bir `Widget` nesne ve ilişkili olay yordamları olaylarına bağlanır `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="007bb-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="007bb-145">Noktasındaki, her `Widget` başlatır kendi `PercentDone` olay `mWidget_PercentDone` olay yordamı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="007bb-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="007bb-146">LongTask yöntemini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="007bb-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="007bb-147">Aşağıdaki kodu ekleyin `Button1_Click` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="007bb-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="007bb-148">Önce `LongTask` yöntemi çağrıldığında, tamamlanma görüntüler başlatılmalıdır etiketi ve sınıf düzeyi `Boolean` yöntemi iptal etme ayarlanmalıdır için bayrak `False`.</span><span class="sxs-lookup"><span data-stu-id="007bb-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="007bb-149">`LongTask` görev süresi 12.2 saniye olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="007bb-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="007bb-150">`PercentDone` Olayı kez her üçte birinden bir saniye.</span><span class="sxs-lookup"><span data-stu-id="007bb-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="007bb-151">Olayı, her zaman `mWidget_PercentDone` olay yordamı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="007bb-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="007bb-152">Zaman `LongTask` yapılır, `mblnCancel` olup olmadığını test `LongTask` normal şekilde sona erdi veya çünkü durdurduysanız `mblnCancel` ayarlandı `True`.</span><span class="sxs-lookup"><span data-stu-id="007bb-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="007bb-153">Tamamlanma yüzdesi yalnızca eski durumda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="007bb-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="007bb-154">Programı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="007bb-154">To run the program</span></span>  
  
1.  <span data-ttu-id="007bb-155">Proje çalışma moduna için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="007bb-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="007bb-156">Tıklatın **görevi Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="007bb-156">Click the **Start Task** button.</span></span> <span data-ttu-id="007bb-157">Her zaman `PercentDone` olayı, etiket tamamlandıktan görev yüzdesi güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="007bb-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="007bb-158">Tıklatın **iptal** görevi Durdur düğmesini.</span><span class="sxs-lookup"><span data-stu-id="007bb-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="007bb-159">Dikkat görünümünü **iptal** düğmesini tıklatın zaman hemen değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="007bb-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="007bb-160">`Click` Olamaz olay meydana kadar `My.Application.DoEvents` deyimi olay işleme izin verir.</span><span class="sxs-lookup"><span data-stu-id="007bb-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="007bb-161">`My.Application.DoEvents` Yöntemi form yaptığı gibi tam olarak aynı şekilde olayları işlemez.</span><span class="sxs-lookup"><span data-stu-id="007bb-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="007bb-162">Örneğin, bu kılavuzda, tıklatmalısınız **iptal** iki kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="007bb-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="007bb-163">Formun olayları doğrudan işlemek izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="007bb-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="007bb-164">Daha fazla bilgi için bkz: [parçacıkları](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="007bb-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="007bb-165">İle F11 programını çalıştırın ve kodda bir defada bir satır adım için eğitici bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007bb-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="007bb-166">Yürütme nasıl girer açıkça görebilirsiniz `LongTask`ve ardından kısaca yeniden girer `Form1` her zaman `PercentDone` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="007bb-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="007bb-167">Ne olacağını yürütme geri kodunda ederken IF `Form1`, `LongTask` yönteminden yeniden?</span><span class="sxs-lookup"><span data-stu-id="007bb-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="007bb-168">En kötü senaryoda, bir yığın taşması oluşabilir `LongTask` olayın tetiklendiği her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="007bb-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="007bb-169">Değişkeni neden `mWidget` için farklı bir olayları işlemek için `Widget` yeni başvuru atayarak nesne `Widget` için `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="007bb-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="007bb-170">Aslında, kodda yapabileceğiniz `Button1_Click` düğmesini her zaman bu yapın.</span><span class="sxs-lookup"><span data-stu-id="007bb-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="007bb-171">Farklı bir pencere öğesi için olayları işlemek için</span><span class="sxs-lookup"><span data-stu-id="007bb-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="007bb-172">Aşağıdaki kod satırını ekleyin `Button1_Click` yazan satırı hemen önceki yordamı, `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="007bb-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="007bb-173">Yukarıdaki kod yeni bir oluşturur `Widget` düğmesine tıklandığında her zaman.</span><span class="sxs-lookup"><span data-stu-id="007bb-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="007bb-174">Hemen `LongTask` yöntemi tamamlayan, başvuru `Widget` yayımlandığı ve `Widget` yok.</span><span class="sxs-lookup"><span data-stu-id="007bb-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="007bb-175">A `WithEvents` değişkeni, bir kerede yalnızca bir nesne başvurusu içerebilir bunu farklı bir atarsanız `Widget` nesnesini `mWidget`, önceki `Widget` nesnenin olayları artık işleneceğini.</span><span class="sxs-lookup"><span data-stu-id="007bb-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="007bb-176">Varsa `mWidget` olan eski bir başvuru içeren yalnızca nesne değişkeni `Widget`, nesne yok.</span><span class="sxs-lookup"><span data-stu-id="007bb-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="007bb-177">Birkaç olayları işlemek istiyorsanız `Widget` nesneleri, kullanın `AddHandler` her nesneden olayları ayrı ayrı işlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="007bb-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="007bb-178">Sayıda bildirebilir `WithEvents` değişkenleri, olarak gerekir, dizi `WithEvents` değişkenleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="007bb-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007bb-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="007bb-179">See Also</span></span>  
 [<span data-ttu-id="007bb-180">İzlenecek yol: Olay Bildirme ve Oluşturma</span><span class="sxs-lookup"><span data-stu-id="007bb-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="007bb-181">Olaylar</span><span class="sxs-lookup"><span data-stu-id="007bb-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
