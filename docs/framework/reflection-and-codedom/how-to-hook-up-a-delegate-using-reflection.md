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
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180499"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="7f5d5-102">Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama</span><span class="sxs-lookup"><span data-stu-id="7f5d5-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="7f5d5-103">Yansımayı derlemeleri yüklemek ve çalıştırmak için kullandığınızda, olayları `+=` bağlamak için C# işleci veya Visual Basic [AddHandler deyimi](../../visual-basic/language-reference/statements/addhandler-statement.md) gibi dil özelliklerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="7f5d5-104">Aşağıdaki yordamlar, yansıma yoluyla gerekli tüm türleri alarak varolan bir yöntemi bir olaya nasıl bağlanıncayabildiğini ve yansıma yakılmasını kullanarak dinamik bir yöntem oluşturmanın ve bir olaya nasıl bağlanılacak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f5d5-105">Olay işleme temsilcisini bağlamanın başka bir yolu için, <xref:System.Reflection.EventInfo.AddEventHandler%2A> <xref:System.Reflection.EventInfo> sınıfın yöntemi için kod örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="7f5d5-106">Yansımayı kullanarak bir temsilciyi bağlamak için</span><span class="sxs-lookup"><span data-stu-id="7f5d5-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="7f5d5-107">Olayları yükselten bir tür içeren bir derleme yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="7f5d5-108">Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f5d5-109">Bu örneği basit tutmak için, geçerli derlemede türetilmiş bir form kullanılır, bu nedenle <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntem geçerli derlemeyi yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="7f5d5-110">Türü <xref:System.Type> temsil eden bir nesne alın ve türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="7f5d5-111">Formun parametresiz bir oluşturucusu olduğundan <xref:System.Activator.CreateInstance%28System.Type%29> yöntem aşağıdaki kodda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="7f5d5-112">Oluşturduğunuz tür parametresiz <xref:System.Activator.CreateInstance%2A> bir oluşturucu yoksa kullanabileceğiniz yöntemin birkaç diğer aşırı yükleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="7f5d5-113">Yeni örnek, derleme hakkında <xref:System.Object> hiçbir şeyin bilinmediğini kurgulamak için tür olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="7f5d5-114">(Yansıma önceden adlarını bilmeden bir derleme de türleri almak için izin verir.)</span><span class="sxs-lookup"><span data-stu-id="7f5d5-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="7f5d5-115">Olayı <xref:System.Reflection.EventInfo> temsil eden bir nesne alın <xref:System.Reflection.EventInfo.EventHandlerType%2A> ve olayı işlemek için kullanılan temsilci türünü almak için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="7f5d5-116">Aşağıdaki kodda, <xref:System.Reflection.EventInfo> <xref:System.Windows.Forms.Control.Click> olay için bir elde edilir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="7f5d5-117">Olayı <xref:System.Reflection.MethodInfo> işleyen yöntemi temsil eden bir nesne alın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="7f5d5-118">Bu konunun ilerleyen bölümlerindeki Örnek bölümündeki tam program kodu, <xref:System.EventHandler> <xref:System.Windows.Forms.Control.Click> olayı işleyen temsilcinin imzasıyla eşleşen bir yöntem içerir, ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="7f5d5-119">Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamı bakın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="7f5d5-120">Yöntemi kullanarak temsilcinin bir <xref:System.Delegate.CreateDelegate%2A> örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="7f5d5-121">Bu yöntem statiktir (Visual`Shared` Basic'te), bu nedenle temsilci türü sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="7f5d5-122">Bu almak aşırı <xref:System.Delegate.CreateDelegate%2A> <xref:System.Reflection.MethodInfo> yükleri kullanarak tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="7f5d5-123">Erişimci `add` yöntemini alın ve olayı bağlamak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="7f5d5-124">Tüm olayların `add` bir erişimcisi `remove` ve bir erişimcisi vardır ve bunlar üst düzey dillerin sözdizimi tarafından gizlenir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="7f5d5-125">Örneğin, C# olayları `+=` bağlamak için işleci kullanır ve Visual Basic [AddHandler deyimini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="7f5d5-126">Aşağıdaki kod `add` <xref:System.Windows.Forms.Control.Click> etkinliğin erişimini alır ve temsilci örneğinde geç geç, onu çağırır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="7f5d5-127">Bağımsız değişkenler bir dizi olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="7f5d5-128">Olayı test edin.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-128">Test the event.</span></span> <span data-ttu-id="7f5d5-129">Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="7f5d5-130">Formu tıklattığınızda olay işleyicisi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="7f5d5-131">Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f5d5-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="7f5d5-132">Olay işleyici yöntemleri, hafif dinamik yöntemler ve yansıma yayan kullanılarak çalışma zamanında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="7f5d5-133">Olay işleyicisi oluşturmak için, temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="7f5d5-134">Bunlar, temsilcinin `Invoke` yöntemi incelenerek elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="7f5d5-135">Aşağıdaki kod, `GetDelegateReturnType` bu `GetDelegateParameterTypes` bilgileri elde etmek için yöntemleri ve yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="7f5d5-136">Bu yöntemlerin kodu daha sonra bu konuda Örnek bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="7f5d5-137">Boş dize kullanılabilir, <xref:System.Reflection.Emit.DynamicMethod>böylece bir , bir adlandırma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="7f5d5-138">Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirerek temsilciye `Example` sınıfın tüm ortak ve özel üyelerine erişim verir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="7f5d5-139">Bir yöntem gövdesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-139">Generate a method body.</span></span> <span data-ttu-id="7f5d5-140">Bu yöntem bir dize yükler, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> dize alan yöntemin aşırı yüklenmesini çağırır, yığından geri dönüş değerini çıkarır (işleyicinin dönüş türü olmadığından) ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="7f5d5-141">Dinamik yöntemler yayma hakkında daha fazla bilgi edinmek [için bkz.](how-to-define-and-execute-dynamic-methods.md)</span><span class="sxs-lookup"><span data-stu-id="7f5d5-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="7f5d5-142">Yöntemini çağırarak dinamik <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="7f5d5-143">Olay `add` için çağırma listesine temsilci eklemek için aksesuarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="7f5d5-144">Olayı test edin.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-144">Test the event.</span></span> <span data-ttu-id="7f5d5-145">Aşağıdaki kod, kod örneğinde tanımlanan formu yükler.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="7f5d5-146">Formu tıklattığınızda hem önceden tanımlanmış olay işleyicisi hem de yayılan olay işleyicisi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="7f5d5-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f5d5-147">Example</span></span>  
 <span data-ttu-id="7f5d5-148">Aşağıdaki kod örneği, varolan bir yöntemi yansımayı kullanarak bir olaya nasıl <xref:System.Reflection.Emit.DynamicMethod> bağlayın ve ayrıca çalışma zamanında bir yöntem yaydı ve bir olaya bağlamak için sınıfın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7f5d5-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f5d5-149">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="7f5d5-150">Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="7f5d5-150">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="7f5d5-151">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7f5d5-151">Reflection</span></span>](reflection.md)
