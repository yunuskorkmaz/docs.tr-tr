---
title: RaiseEvent Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6ba5ce4b009e0d8c675db07b56b9811c595ae2f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="raiseevent-statement"></a><span data-ttu-id="72a6d-102">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="72a6d-102">RaiseEvent Statement</span></span>
<span data-ttu-id="72a6d-103">Tetikleyiciler bir olay sınıfı, form veya belge içinde modülü düzeyinde bildirildi.</span><span class="sxs-lookup"><span data-stu-id="72a6d-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72a6d-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="72a6d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="72a6d-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="72a6d-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="72a6d-106">Required.</span></span> <span data-ttu-id="72a6d-107">Tetiklemek için olayın adı.</span><span class="sxs-lookup"><span data-stu-id="72a6d-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="72a6d-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="72a6d-108">Optional.</span></span> <span data-ttu-id="72a6d-109">Virgülle ayrılmış listesi değişkenleri, dizileri veya ifade.</span><span class="sxs-lookup"><span data-stu-id="72a6d-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="72a6d-110">`argumentlist` Bağımsız değişkeni tarafından parantez içine gerekir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="72a6d-111">Bağımsız değişkenler varsa, parantez atlanmış gerekir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72a6d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72a6d-112">Remarks</span></span>  
 <span data-ttu-id="72a6d-113">Gerekli `eventname` bir olayın adı modülü içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="72a6d-114">Visual Basic değişken adlandırma kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="72a6d-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="72a6d-115">Olay ortaya çıkar modül içinde bildirilen değil, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="72a6d-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="72a6d-116">Aşağıdaki kod parçası, bir olay bildirimi ve olay yükseltildiği bir yordam gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 <span data-ttu-id="72a6d-117">Kullanamazsınız `RaiseEvent` modülünde açıkça bildirilmemiş olayları yükseltmek için.</span><span class="sxs-lookup"><span data-stu-id="72a6d-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="72a6d-118">Örneğin, tüm form devralma bir <xref:System.Windows.Forms.Control.Click> olayından <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, kullanarak yükseltilemez `RaiseEvent` türetilmiş bir biçimde.</span><span class="sxs-lookup"><span data-stu-id="72a6d-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="72a6d-119">Bildirirseniz bir `Click` olay isteğe bağlı olarak form modülünde formun kendi shadows <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="72a6d-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="72a6d-120">Formun hala çağırabileceği <xref:System.Windows.Forms.Control.Click> çağırarak olay <xref:System.Windows.Forms.Control.OnClick%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72a6d-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="72a6d-121">Varsayılan olarak, kendi olay işleyicileri bağlantıları kurulduğundan emin sırayla Visual Basic'te tanımlı bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="72a6d-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="72a6d-122">Olayları olabileceğinden `ByRef` parametreleri geç bağlanan bir işlem önceki olay işleyici tarafından değiştirilmiş parametreleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72a6d-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="72a6d-123">Olay işleyicileri yürüttükten sonra denetim olayı alt yordama döndürülür.</span><span class="sxs-lookup"><span data-stu-id="72a6d-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a6d-124">Olayları paylaşılmayan bildirilen sınıf oluşturucu içinde oluşmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="72a6d-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="72a6d-125">Bu gibi olaylar çalışma zamanı hataları neden olmaz ancak ilişkili olay işleyicileri tarafından yakalanan başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="72a6d-126">Kullanım `Shared` bir olayı bir oluşturucusundan gerekiyorsa, paylaşılan bir olay oluşturmak için değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="72a6d-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a6d-127">Özel bir olay tanımlayarak olayları varsayılan davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72a6d-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="72a6d-128">Özel olaylar için `RaiseEvent` deyimi çağırır olayın `RaiseEvent` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="72a6d-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="72a6d-129">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="72a6d-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72a6d-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="72a6d-130">Example</span></span>  
 <span data-ttu-id="72a6d-131">Aşağıdaki örnek, 10 saniyeden 0 aşağı saymak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="72a6d-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="72a6d-132">Kod olayla ilgili yöntemler, özellikler ve ifadeleri de dahil olmak üzere, çeşitli gösterir `RaiseEvent` deyimi.</span><span class="sxs-lookup"><span data-stu-id="72a6d-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="72a6d-133">Olay kaynağı bir olay başlatır sınıf olduğunu ve olay işleme yöntemleri olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="72a6d-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="72a6d-134">Bir olay kaynağı ürettiği olaylar için birden çok işleyicileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="72a6d-135">Olay sınıfı başlatır, bu olay nesnesinin bu örneği için olayları işlemek için katılmamayı her bir sınıf üzerinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="72a6d-136">Bu örnek ayrıca bir form kullanır (`Form1`) bir düğme ile (`Button1`) ve bir metin kutusu (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="72a6d-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="72a6d-137">Düğmeye tıkladığınızda, ilk metin kutusunu 0 saniye 10 geri sayım görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72a6d-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="72a6d-138">Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72a6d-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="72a6d-139">Kodunu `Form1` formun ilk ve terminal durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="72a6d-140">Ayrıca, olayları ortaya çıktığında yürütülen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="72a6d-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="72a6d-141">Bu örneği kullanmak için yeni bir Windows uygulama projesi açın, adlı bir düğme ekleme `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`.</span><span class="sxs-lookup"><span data-stu-id="72a6d-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="72a6d-142">Ardından formu sağ tıklatın ve **görünümü kodu** Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="72a6d-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="72a6d-143">Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="72a6d-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="72a6d-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="72a6d-144">Example</span></span>  
 <span data-ttu-id="72a6d-145">Aşağıdaki kodu için kod ekleme `Form1`.</span><span class="sxs-lookup"><span data-stu-id="72a6d-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="72a6d-146">Aşağıdaki gibi bulunabilecek yinelenen yordamlarla Değiştir `Form_Load`, veya `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="72a6d-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 <span data-ttu-id="72a6d-147">Önceki örnekte çalıştırın ve etiketli düğmesini tıklatın için F5 tuşuna basın **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="72a6d-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="72a6d-148">Saniye sayısı ilk metin kutusunu başlatır.</span><span class="sxs-lookup"><span data-stu-id="72a6d-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="72a6d-149">Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72a6d-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a6d-150">`My.Application.DoEvents` Yöntemi form yaptığı gibi tam olarak aynı şekilde olayları işlemez.</span><span class="sxs-lookup"><span data-stu-id="72a6d-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="72a6d-151">Formun olayları doğrudan işlemek izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="72a6d-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="72a6d-152">Daha fazla bilgi için bkz: [parçacıkları](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="72a6d-152">For more information, see [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a6d-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72a6d-153">See Also</span></span>  
 [<span data-ttu-id="72a6d-154">Olaylar</span><span class="sxs-lookup"><span data-stu-id="72a6d-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="72a6d-155">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="72a6d-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="72a6d-156">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="72a6d-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="72a6d-157">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="72a6d-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="72a6d-158">İşleme</span><span class="sxs-lookup"><span data-stu-id="72a6d-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
