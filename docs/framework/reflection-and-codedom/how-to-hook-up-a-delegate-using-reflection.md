---
title: 'Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: 14a9694708b36b23ecef453d530ad3b939a046ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130126"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="85faa-102">Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama</span><span class="sxs-lookup"><span data-stu-id="85faa-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="85faa-103">Derlemeleri yüklemek ve çalıştırmak için yansıma kullandığınızda, olayları bağlamak için C# `+=` işleci veya Visual Basic [AddHandler ifadesiyle](../../visual-basic/language-reference/statements/addhandler-statement.md) benzer dil özelliklerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="85faa-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="85faa-104">Aşağıdaki yordamlarda, tüm gerekli türleri yansıma aracılığıyla alarak bir olaya mevcut bir yöntemi nasıl yedekleyerek, yansıma yayma kullanarak dinamik bir yöntem oluşturma ve bir olaya bağlama işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85faa-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85faa-105">Bir olay işleme temsilcisini bağlamak için başka bir yöntem için, <xref:System.Reflection.EventInfo> sınıfının <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi için kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="85faa-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="85faa-106">Yansımayı kullanarak bir temsilciyi bağlama</span><span class="sxs-lookup"><span data-stu-id="85faa-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="85faa-107">Olayları başlatan bir tür içeren bir derleme yükleyin.</span><span class="sxs-lookup"><span data-stu-id="85faa-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="85faa-108">Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="85faa-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="85faa-109">Bu örneği basit tutmak için geçerli derlemede bulunan türetilmiş bir form kullanılır, bu nedenle geçerli derlemeyi yüklemek için <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85faa-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="85faa-110">Türü temsil eden bir <xref:System.Type> nesnesi alın ve türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85faa-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="85faa-111"><xref:System.Activator.CreateInstance%28System.Type%29> yöntemi, form parametresiz bir oluşturucuya sahip olduğu için aşağıdaki kodda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85faa-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="85faa-112">Oluşturmakta olduğunuz türün parametresiz bir Oluşturucusu yoksa kullanabileceğiniz <xref:System.Activator.CreateInstance%2A> yönteminin birkaç başka aşırı yüklemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="85faa-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="85faa-113">Yeni örnek, derleme hakkında hiçbir şeyin bilinmediğini belirten derlemeyi sürdürmek için <xref:System.Object> türü olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="85faa-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="85faa-114">(Yansıma, adlarını önceden bilmeden bir derlemede almanızı sağlar.)</span><span class="sxs-lookup"><span data-stu-id="85faa-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="85faa-115">Olayı temsil eden bir <xref:System.Reflection.EventInfo> nesnesi alın ve olayı işlemek için kullanılan temsilcinin türünü almak için <xref:System.Reflection.EventInfo.EventHandlerType%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="85faa-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="85faa-116">Aşağıdaki kodda, <xref:System.Windows.Forms.Control.Click> olayı için bir <xref:System.Reflection.EventInfo> elde edilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="85faa-117">Olayı işleyen yöntemi temsil eden bir <xref:System.Reflection.MethodInfo> nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="85faa-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="85faa-118">Bu konunun ilerleyen kısımlarında örnek bölümünde yer alan tüm program kodu, <xref:System.Windows.Forms.Control.Click> olayını işleyen <xref:System.EventHandler> temsilcisinin imzasıyla eşleşen bir yöntemi içerir, ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85faa-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="85faa-119">Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında olay işleyicisi oluşturmak için eşlik eden yordama bakın.</span><span class="sxs-lookup"><span data-stu-id="85faa-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="85faa-120"><xref:System.Delegate.CreateDelegate%2A> yöntemini kullanarak temsilcinin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85faa-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="85faa-121">Bu yöntem statik (Visual Basic`Shared`), bu nedenle temsilci türü sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85faa-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="85faa-122"><xref:System.Reflection.MethodInfo> alan <xref:System.Delegate.CreateDelegate%2A> aşırı yüklemelerinin kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="85faa-123">`add` erişimci yöntemini alın ve olayı bağlamak için onu çağırın.</span><span class="sxs-lookup"><span data-stu-id="85faa-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="85faa-124">Tüm olayların, üst düzey dillerin sözdizimi tarafından gizlenen bir `add` erişimcisi ve `remove` erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="85faa-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="85faa-125">Örneğin, C# olayları bağlamak için `+=` işlecini kullanır ve Visual Basic [AddHandler ifadesini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır.</span><span class="sxs-lookup"><span data-stu-id="85faa-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="85faa-126">Aşağıdaki kod, <xref:System.Windows.Forms.Control.Click> olayının `add` erişimcisini alır ve ona geç bağlandığını çağırır ve temsilci örneğini geçirir.</span><span class="sxs-lookup"><span data-stu-id="85faa-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="85faa-127">Bağımsız değişkenlerin bir dizi olarak geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="85faa-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="85faa-128">Olayı test edin.</span><span class="sxs-lookup"><span data-stu-id="85faa-128">Test the event.</span></span> <span data-ttu-id="85faa-129">Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir.</span><span class="sxs-lookup"><span data-stu-id="85faa-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="85faa-130">Forma tıklanması olay işleyicisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="85faa-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="85faa-131">Çalışma zamanında dinamik bir yöntem kullanarak olay işleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="85faa-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="85faa-132">Olay işleyici yöntemleri, basit dinamik yöntemler ve yansıma yayma kullanılarak çalışma zamanında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="85faa-133">Bir olay işleyicisi oluşturmak için temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="85faa-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="85faa-134">Bu, temsilcinin `Invoke` yöntemi incelenerek elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="85faa-135">Aşağıdaki kod, bu bilgileri elde etmek için `GetDelegateReturnType` ve `GetDelegateParameterTypes` yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="85faa-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="85faa-136">Bu yöntemlerin kodu, bu konunun ilerleyen kısımlarında örnek bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="85faa-137"><xref:System.Reflection.Emit.DynamicMethod>adlandırmak gerekli değildir, bu nedenle boş dize kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85faa-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="85faa-138">Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirir ve temsilci, `Example` sınıfının tüm ortak ve özel üyelerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="85faa-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="85faa-139">Bir yöntem gövdesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85faa-139">Generate a method body.</span></span> <span data-ttu-id="85faa-140">Bu yöntem bir dize yükler, bir dizeyi alan <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> yönteminin aşırı yüklemesini çağırır, dönüş değerini yığından kapatır (işleyicinin dönüş türü olmadığından) ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="85faa-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="85faa-141">Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tanımlama ve yürütme dinamik yöntemleri](how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="85faa-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="85faa-142"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemini çağırarak dinamik metodu doldurun.</span><span class="sxs-lookup"><span data-stu-id="85faa-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="85faa-143">Olayın çağırma listesine temsilciyi eklemek için `add` erişimcisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="85faa-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="85faa-144">Olayı test edin.</span><span class="sxs-lookup"><span data-stu-id="85faa-144">Test the event.</span></span> <span data-ttu-id="85faa-145">Aşağıdaki kod, kod örneğinde tanımlanan formu yükler.</span><span class="sxs-lookup"><span data-stu-id="85faa-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="85faa-146">Formu tıklatmak, hem önceden tanımlanmış olay işleyicisini hem de yayınlanan olay işleyicisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="85faa-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="85faa-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="85faa-147">Example</span></span>  
 <span data-ttu-id="85faa-148">Aşağıdaki kod örneği, var olan bir yöntemi yansıma kullanarak bir olaya nasıl bağlanacağını ve ayrıca, çalışma zamanında bir yöntemi göstermek ve bir olaya bağlamak için <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="85faa-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="85faa-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85faa-149">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="85faa-150">Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="85faa-150">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="85faa-151">Yansıma</span><span class="sxs-lookup"><span data-stu-id="85faa-151">Reflection</span></span>](reflection.md)
