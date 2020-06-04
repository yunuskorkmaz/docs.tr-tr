---
title: RaiseEvent Deyimi
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
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404297"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="8e87b-102">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e87b-102">RaiseEvent Statement</span></span>
<span data-ttu-id="8e87b-103">Sınıf, form veya belge içinde modül düzeyinde belirtilen bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="8e87b-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e87b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e87b-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="8e87b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e87b-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="8e87b-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-106">Required.</span></span> <span data-ttu-id="8e87b-107">Tetiklenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="8e87b-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="8e87b-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8e87b-108">Optional.</span></span> <span data-ttu-id="8e87b-109">Değişkenlerin, dizilerin veya ifadelerin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="8e87b-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="8e87b-110">`argumentlist`Bağımsız değişkenin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="8e87b-111">Bağımsız değişken yoksa, parantezler atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e87b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e87b-112">Remarks</span></span>  
 <span data-ttu-id="8e87b-113">Gerekli, `eventname` modül içinde belirtilen bir olayın adıdır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="8e87b-114">Visual Basic değişken adlandırma kuralları ' nı izler.</span><span class="sxs-lookup"><span data-stu-id="8e87b-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="8e87b-115">Olayın oluşturulduğu modül içinde bildirilmemiş bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="8e87b-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="8e87b-116">Aşağıdaki kod parçası bir olay bildirimini ve olayın oluşturulduğu yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="8e87b-117">`RaiseEvent`Modülde açıkça bildirilmeyen olayları yükseltmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8e87b-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="8e87b-118">Örneğin, tüm formlar <xref:System.Windows.Forms.Control.Click> öğesinden bir olay devraldığı için <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , `RaiseEvent` türetilmiş bir formda kullanılarak gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8e87b-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="8e87b-119">`Click`Form modülünde bir olay bildirirseniz, formun kendi <xref:System.Windows.Forms.Control.Click> olayını gölgeler.</span><span class="sxs-lookup"><span data-stu-id="8e87b-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="8e87b-120">Yöntemini çağırarak formun olayını yine de çağırabilirsiniz <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Control.OnClick%2A> .</span><span class="sxs-lookup"><span data-stu-id="8e87b-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="8e87b-121">Varsayılan olarak, Visual Basic tanımlı bir olay, olay işleyicilerini bağlantıların kurulduğu sırada başlatır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="8e87b-122">Olayların `ByRef` parametreleri olabileceğinden, geç bağlanan bir işlem önceki bir olay işleyicisi tarafından değiştirilmiş parametreler alabilir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="8e87b-123">Olay işleyicileri çalıştırıldıktan sonra, olayı oluşturan alt yordama denetim döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8e87b-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e87b-124">Paylaşılmayan olaylar, bildirildiği sınıfın Oluşturucusu içinde çıkarılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="8e87b-125">Bu tür olaylar çalışma zamanı hatalarına neden olmasa da, ilişkili olay işleyicileri tarafından yakalanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="8e87b-126">`Shared`Bir oluşturucudan bir olay oluşturmanız gerekiyorsa paylaşılan bir olay oluşturmak için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e87b-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e87b-127">Özel bir olay tanımlayarak olayların varsayılan davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e87b-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="8e87b-128">Özel olaylar için, `RaiseEvent` ifade olayın `RaiseEvent` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="8e87b-129">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8e87b-129">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e87b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e87b-130">Example</span></span>  
 <span data-ttu-id="8e87b-131">Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e87b-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="8e87b-132">Kod, deyimi dahil olmak üzere olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir `RaiseEvent` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="8e87b-133">Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="8e87b-134">Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="8e87b-135">Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e87b-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="8e87b-136">Örnek ayrıca bir `Form1` düğme ( `Button1` ) ve metin kutusu () içeren bir form () kullanır `TextBox1` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="8e87b-137">Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e87b-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="8e87b-138">Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="8e87b-139">Kodu, `Form1` formun ilk ve Terminal durumlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="8e87b-140">Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="8e87b-141">Bu örneği kullanmak için yeni bir Windows uygulaması projesi açın, adlı bir düğme ve adlı `Button1` ana forma adlı bir metin kutusu ekleyin `TextBox1` `Form1` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="8e87b-142">Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="8e87b-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="8e87b-143">`WithEvents`Sınıfının bildirimler bölümüne bir değişken ekleyin `Form1` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="8e87b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e87b-144">Example</span></span>  
 <span data-ttu-id="8e87b-145">Koduna aşağıdaki kodu ekleyin `Form1` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="8e87b-146">Veya gibi mevcut olabilecek yinelenen yordamları değiştirin `Form_Load` `Button_Click` .</span><span class="sxs-lookup"><span data-stu-id="8e87b-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="8e87b-147">Yukarıdaki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e87b-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="8e87b-148">İlk metin kutusu, saniyeyi saymaya başlar.</span><span class="sxs-lookup"><span data-stu-id="8e87b-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="8e87b-149">Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8e87b-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e87b-150">`My.Application.DoEvents`Yöntemi, olayları yalnızca formla aynı şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="8e87b-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="8e87b-151">Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e87b-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="8e87b-152">Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e87b-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e87b-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e87b-153">See also</span></span>

- [<span data-ttu-id="8e87b-154">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8e87b-154">Events</span></span>](../../programming-guide/language-features/events/index.md)
- [<span data-ttu-id="8e87b-155">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e87b-155">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="8e87b-156">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e87b-156">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="8e87b-157">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e87b-157">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="8e87b-158">Handles</span><span class="sxs-lookup"><span data-stu-id="8e87b-158">Handles</span></span>](handles-clause.md)
