---
title: RaiseEvent deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ccefe07c847c7a356e9ff8da301257bf6a90d1ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655016"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="01759-102">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="01759-102">RaiseEvent Statement</span></span>
<span data-ttu-id="01759-103">Tetikleyiciler bir olay, bir sınıf, form ya da belge içinde Modül düzeyinde bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="01759-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01759-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01759-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="01759-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="01759-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="01759-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="01759-106">Required.</span></span> <span data-ttu-id="01759-107">Tetiklemek için olayın adı.</span><span class="sxs-lookup"><span data-stu-id="01759-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="01759-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="01759-108">Optional.</span></span> <span data-ttu-id="01759-109">Değişkenleri, diziler veya ifadelerin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="01759-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="01759-110">`argumentlist` Bağımsız değişkeni parantezle alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="01759-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="01759-111">Hiçbir bağımsız değişken varsa, parantezler atlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="01759-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01759-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01759-112">Remarks</span></span>  
 <span data-ttu-id="01759-113">Gerekli `eventname` içinde modül olarak bildirilen bir olayın adı.</span><span class="sxs-lookup"><span data-stu-id="01759-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="01759-114">Bu, Visual Basic değişken adlandırma kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="01759-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="01759-115">Olayı ortaya çıkar modülü içinde bildirilmedi, bir hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="01759-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="01759-116">Aşağıdaki kod parçası, bir olay bildirimi ve olay harekete geçirilen bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="01759-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 <span data-ttu-id="01759-117">Kullanamazsınız `RaiseEvent` modülünde açıkça bildirilmeyen olayları yükseltmek için.</span><span class="sxs-lookup"><span data-stu-id="01759-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="01759-118">Örneğin, tüm form devralma bir <xref:System.Windows.Forms.Control.Click> olaydan <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, kullanarak yükseltilemez `RaiseEvent` türetilmiş bir biçimde.</span><span class="sxs-lookup"><span data-stu-id="01759-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="01759-119">Bildirirseniz bir `Click` olay isteğe bağlı olarak form modülünde formun kendi gölgeleri <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="01759-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="01759-120">Formun yine de çağırabilirsiniz <xref:System.Windows.Forms.Control.Click> çağırarak olay <xref:System.Windows.Forms.Control.OnClick%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="01759-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="01759-121">Varsayılan olarak, kendi olay işleyicileri bağlantı kurulur sırada Visual Basic içinde tanımlanan bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="01759-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="01759-122">Olayları olabileceğinden `ByRef` parametreleri, geç bağlanan bir işlem daha önceki bir olay işleyicisi tarafından değiştirilmiş parametreleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01759-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="01759-123">Olay işleyicileri yürüttükten sonra olayı tetikleyen alt yordama döndürülür.</span><span class="sxs-lookup"><span data-stu-id="01759-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01759-124">Olayları paylaşılmayan içinde bildirildikleri sınıf oluşturucusu içinde harekete Geçirilmemesi gereken.</span><span class="sxs-lookup"><span data-stu-id="01759-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="01759-125">Bu tür olayların çalışma zamanı hatalarına neden olmaz ancak ilişkili olay işleyicileri tarafından yakalanması kesin başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="01759-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="01759-126">Kullanım `Shared` değiştiricisi bir oluşturucu bir olaydan bulunmanız, paylaşılan bir olay oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="01759-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01759-127">Özel olay tanımlayarak olayları'nın varsayılan davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01759-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="01759-128">Özel olaylar için `RaiseEvent` deyimi çağırır olayın `RaiseEvent` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="01759-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="01759-129">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="01759-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01759-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="01759-130">Example</span></span>  
 <span data-ttu-id="01759-131">Aşağıdaki örnek, 0, 10 saniye basılı saymak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="01759-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="01759-132">İlgili olay yöntemleri, özellikleri ve ifadeleri dahil olmak üzere, birkaç kod göstermektedir `RaiseEvent` deyimi.</span><span class="sxs-lookup"><span data-stu-id="01759-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="01759-133">Bir olay başlatır sınıf olay kaynağı olan ve olay işleme yöntemleri olay işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="01759-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="01759-134">Olay kaynağı, oluşturduğu olaylar için birden çok işleyiciler olabilir.</span><span class="sxs-lookup"><span data-stu-id="01759-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="01759-135">Olay sınıfı başlatır, nesnenin Bu örneği için olayları işlemek için katılmamayı her sınıfta bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="01759-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="01759-136">Örnek ayrıca bir form kullanır (`Form1`) bir düğme olan (`Button1`) ve bir metin kutusu (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="01759-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="01759-137">Düğmeye tıkladığınızda, 10'dan geri sayım 0 saniyeye ilk metin kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01759-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="01759-138">Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01759-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="01759-139">Kodu `Form1` formun ilk ve terminal durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="01759-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="01759-140">Ayrıca, olaylar oluştuğunda yürütülen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="01759-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="01759-141">Bu örneği kullanmak için yeni bir Windows uygulaması projesi açın, adlı bir düğme ekleyin `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`.</span><span class="sxs-lookup"><span data-stu-id="01759-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="01759-142">Ardından formun sağ tıklatıp **kodu görüntüle** Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="01759-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="01759-143">Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01759-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="01759-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="01759-144">Example</span></span>  
 <span data-ttu-id="01759-145">Aşağıdaki kodu için kod ekleyin `Form1`.</span><span class="sxs-lookup"><span data-stu-id="01759-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="01759-146">Oluşabilecek, gibi yinelenen yordamlarla değiştirin `Form_Load`, veya `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="01759-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 <span data-ttu-id="01759-147">Önceki örneği çalıştırmak ve etiketli düğmeye tıklayın için F5 tuşuna basın **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="01759-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="01759-148">İlk metin kutusuna saniye sayısı başlar.</span><span class="sxs-lookup"><span data-stu-id="01759-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="01759-149">Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01759-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01759-150">`My.Application.DoEvents` Yöntemi form gibi tam olarak aynı şekilde olayları işlemez.</span><span class="sxs-lookup"><span data-stu-id="01759-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="01759-151">Olayları doğrudan işlemeye izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="01759-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="01759-152">Daha fazla bilgi için [yönetilen iş parçacığı](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="01759-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01759-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01759-153">See also</span></span>
- [<span data-ttu-id="01759-154">Olaylar</span><span class="sxs-lookup"><span data-stu-id="01759-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="01759-155">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="01759-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="01759-156">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="01759-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="01759-157">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="01759-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="01759-158">İşleme</span><span class="sxs-lookup"><span data-stu-id="01759-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
