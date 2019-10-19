---
title: RaiseEvent ekstresi (Visual Basic)
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
ms.openlocfilehash: efc7da34a297fd01411302b717cfda83aa9f87d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582103"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="35991-102">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="35991-102">RaiseEvent Statement</span></span>
<span data-ttu-id="35991-103">Sınıf, form veya belge içinde modül düzeyinde belirtilen bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="35991-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35991-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35991-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="35991-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="35991-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="35991-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="35991-106">Required.</span></span> <span data-ttu-id="35991-107">Tetiklenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="35991-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="35991-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="35991-108">Optional.</span></span> <span data-ttu-id="35991-109">Değişkenlerin, dizilerin veya ifadelerin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="35991-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="35991-110">@No__t_0 bağımsız değişkeni parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35991-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="35991-111">Bağımsız değişken yoksa, parantezler atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35991-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35991-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35991-112">Remarks</span></span>  
 <span data-ttu-id="35991-113">Gerekli `eventname`, modül içinde belirtilen bir olayın adıdır.</span><span class="sxs-lookup"><span data-stu-id="35991-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="35991-114">Visual Basic değişken adlandırma kuralları ' nı izler.</span><span class="sxs-lookup"><span data-stu-id="35991-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="35991-115">Olayın oluşturulduğu modül içinde bildirilmemiş bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="35991-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="35991-116">Aşağıdaki kod parçası bir olay bildirimini ve olayın oluşturulduğu yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="35991-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="35991-117">Modülde açıkça bildirilmeyen olayları yükseltmek için `RaiseEvent` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="35991-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="35991-118">Örneğin, tüm formlar <xref:System.Windows.Forms.Form?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.Click> bir olayı miras alarak, türetilmiş bir formda `RaiseEvent` kullanılarak gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="35991-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="35991-119">Form modülünde bir `Click` olayı bildirirseniz, formun kendi <xref:System.Windows.Forms.Control.Click> olayını gölgeler.</span><span class="sxs-lookup"><span data-stu-id="35991-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="35991-120">Yine de, <xref:System.Windows.Forms.Control.OnClick%2A> yöntemini çağırarak formun <xref:System.Windows.Forms.Control.Click> olayını çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35991-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="35991-121">Varsayılan olarak, Visual Basic tanımlı bir olay, olay işleyicilerini bağlantıların kurulduğu sırada başlatır.</span><span class="sxs-lookup"><span data-stu-id="35991-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="35991-122">Olaylar `ByRef` parametrelere sahip olabileceğinden, geç bağlanan bir işlem önceki bir olay işleyicisi tarafından değiştirilmiş parametreler alabilir.</span><span class="sxs-lookup"><span data-stu-id="35991-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="35991-123">Olay işleyicileri çalıştırıldıktan sonra, olayı oluşturan alt yordama denetim döndürülür.</span><span class="sxs-lookup"><span data-stu-id="35991-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35991-124">Paylaşılmayan olaylar, bildirildiği sınıfın Oluşturucusu içinde çıkarılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="35991-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="35991-125">Bu tür olaylar çalışma zamanı hatalarına neden olmasa da, ilişkili olay işleyicileri tarafından yakalanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="35991-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="35991-126">Bir oluşturucudan bir olay oluşturmanız gerekiyorsa, paylaşılan bir olay oluşturmak için `Shared` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="35991-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35991-127">Özel bir olay tanımlayarak olayların varsayılan davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35991-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="35991-128">Özel olaylar için `RaiseEvent` ifade, olayın `RaiseEvent` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="35991-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="35991-129">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="35991-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35991-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="35991-130">Example</span></span>  
 <span data-ttu-id="35991-131">Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="35991-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="35991-132">Kod, `RaiseEvent` deyimi de dahil olmak üzere olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35991-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="35991-133">Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="35991-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="35991-134">Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="35991-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="35991-135">Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="35991-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="35991-136">Örnek ayrıca bir düğme (`Button1`) ve metin kutusu (`TextBox1`) içeren bir form (`Form1`) kullanır.</span><span class="sxs-lookup"><span data-stu-id="35991-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="35991-137">Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler.</span><span class="sxs-lookup"><span data-stu-id="35991-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="35991-138">Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="35991-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="35991-139">@No__t_0 kodu, formun başlangıç ve Terminal durumlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35991-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="35991-140">Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="35991-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="35991-141">Bu örneği kullanmak için, yeni bir Windows uygulaması projesi açın, `Button1` adlı bir düğme ve `TextBox1` adlı ana forma `Form1` adlı bir metin kutusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35991-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="35991-142">Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="35991-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="35991-143">@No__t_1 sınıfının bildirimler bölümüne `WithEvents` değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35991-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="35991-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="35991-144">Example</span></span>  
 <span data-ttu-id="35991-145">@No__t_0 koda aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35991-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="35991-146">@No__t_0 veya `Button_Click` gibi, mevcut olabilecek yinelenen yordamları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="35991-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="35991-147">Yukarıdaki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="35991-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="35991-148">İlk metin kutusu, saniyeyi saymaya başlar.</span><span class="sxs-lookup"><span data-stu-id="35991-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="35991-149">Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="35991-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35991-150">@No__t_0 yöntemi, olayları yalnızca formla aynı şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="35991-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="35991-151">Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35991-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="35991-152">Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="35991-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35991-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35991-153">See also</span></span>

- [<span data-ttu-id="35991-154">Olaylar</span><span class="sxs-lookup"><span data-stu-id="35991-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="35991-155">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="35991-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="35991-156">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="35991-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="35991-157">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="35991-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="35991-158">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="35991-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
