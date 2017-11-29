---
title: "Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72d2061d8e4432422eeb2a30c916af7e254b4f81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="b6e6f-102">Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama</span><span class="sxs-lookup"><span data-stu-id="b6e6f-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="b6e6f-103">Yük ve derlemeler çalıştırmak için yansıma kullandığınızda gibi C# dil özellikleri kullanamazsınız `+=` işleci veya Visual Basic [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) olaylarını bağlanmanıza.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="b6e6f-104">Aşağıdaki yordamlar nasıl yansıma yoluyla tüm gerekli türlerin alarak varolan bir yöntemi bir olaya bağlanacağını gösterir ve yansıma kullanarak dinamik bir yöntemi nasıl oluşturulacağını yayma ve olaya kadar bağlayın.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6e6f-105">Kod örneği için bir olay işleme temsilci bağlama başka bir yol için bkz <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi <xref:System.Reflection.EventInfo> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="b6e6f-106">Yansıma kullanarak temsilci bağlama için</span><span class="sxs-lookup"><span data-stu-id="b6e6f-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="b6e6f-107">Olayları başlatır türünü içeren bütünleştirilmiş yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="b6e6f-108">Derlemeler ile yüklenen genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b6e6f-109">Bu örneği basit tutmak için geçerli derleme türetilmiş bir formda kullanılır, böylece <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi geçerli derlemesini yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="b6e6f-110">Alma bir <xref:System.Type> türünü temsil eden nesne ve türünün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="b6e6f-111"><xref:System.Activator.CreateInstance%28System.Type%29> Biçiminde varsayılan bir oluşturucu olduğundan yöntemi aşağıdaki kodda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="b6e6f-112">Diğer birçok aşırı <xref:System.Activator.CreateInstance%2A> oluşturmakta türü varsayılan bir oluşturucu yoksa kullanabileceğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="b6e6f-113">Yeni örnek türü olarak depolanır <xref:System.Object> kurgu korumak için hiçbir şeyin hakkında derleme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="b6e6f-114">(Yansıma adlarını önceden bilmeden bir derlemede türleri almanızı sağlar.)</span><span class="sxs-lookup"><span data-stu-id="b6e6f-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="b6e6f-115">Alma bir <xref:System.Reflection.EventInfo> olayı temsil eden nesne ve kullanmak <xref:System.Reflection.EventInfo.EventHandlerType%2A> olayını işlemek için kullanılan temsilci türü alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="b6e6f-116">Aşağıdaki kodda bir <xref:System.Reflection.EventInfo> için <xref:System.Windows.Forms.Control.Click> olay elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="b6e6f-117">Alma bir <xref:System.Reflection.MethodInfo> olayını işler yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="b6e6f-118">Bu konunun ilerleyen bölümlerinde örnek bölümüne tam program kodunda imzası eşleşen bir yöntem içerir <xref:System.EventHandler> temsilci, yürüten <xref:System.Windows.Forms.Control.Click> olay, ancak aynı zamanda üretebilir dinamik yöntemler çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="b6e6f-119">Ayrıntılar için dinamik bir yöntemi kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="b6e6f-120">Kullanarak temsilci bir örneğini oluşturmak <xref:System.Delegate.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="b6e6f-121">Bu yöntem statik (`Shared` Visual Basic'te), temsilci türü sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="b6e6f-122">Aşırı kullanarak <xref:System.Delegate.CreateDelegate%2A> süren bir <xref:System.Reflection.MethodInfo> önerilir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="b6e6f-123">Alma `add` erişimci yöntemi ve olay kanca kendisine çağırma.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="b6e6f-124">Tüm olayları sahip bir `add` erişimcisi ve `remove` üst düzey dilleri sözdizimi tarafından gizli erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="b6e6f-125">Örneğin, C# kullanan `+=` olaylar ve Visual Basic kullanan kanca işleci [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6e6f-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="b6e6f-126">Aşağıdaki kod alır `add` erişimcisine <xref:System.Windows.Forms.Control.Click> olay ve onu çağırır geç temsilci örneğinde geçirme bağlama,.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="b6e6f-127">Bağımsız değişkenler, bir dizi olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="b6e6f-128">Olay sınayın.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-128">Test the event.</span></span> <span data-ttu-id="b6e6f-129">Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formun gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="b6e6f-130">Formun tıklatarak olay işleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="b6e6f-131">Dinamik bir yöntemi kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b6e6f-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="b6e6f-132">Olay işleyici yöntemleri basit dinamik yöntemleri kullanarak çalışma zamanında oluşturulabilir ve yansıma yayma.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="b6e6f-133">Olay işleyici oluşturmak için dönüş türü ve temsilci parametre türleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="b6e6f-134">Bunlar temsilcinin incelenerek alınabilir `Invoke` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="b6e6f-135">Aşağıdaki kod `GetDelegateReturnType` ve `GetDelegateParameterTypes` bu bilgileri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="b6e6f-136">Bu yöntemler için kod, bu konunun ilerleyen bölümlerinde örnek bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="b6e6f-137">Ad için gerekli değil bir <xref:System.Reflection.Emit.DynamicMethod>, böylece boş dize kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="b6e6f-138">Aşağıdaki kodda son bağımsız değişken dinamik yöntemi erişim tüm genel ve özel üyelerine temsilci vermiş geçerli türüyle ilişkilendiren `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="b6e6f-139">Yöntem gövdesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-139">Generate a method body.</span></span> <span data-ttu-id="b6e6f-140">Bu yöntem bir dize yükler, aşırı yüklemesini çağırır <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> yönteminin bir dize alan POP yığından dönüş değeri (işleyicisi hiçbir dönüş türüne sahip olduğundan) ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="b6e6f-141">Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz: [nasıl yapılır: tanımlayın ve dinamik yöntemleri yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b6e6f-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="b6e6f-142">Dinamik yöntemi çağrılarak tamamlamak kendi <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="b6e6f-143">Kullanım `add` çağırma listesine olayı için temsilci eklemek için erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="b6e6f-144">Olay sınayın.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-144">Test the event.</span></span> <span data-ttu-id="b6e6f-145">Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formun yükler.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="b6e6f-146">Formun tıklatarak verilmiş olay işleyicisi ve önceden tanımlanmış olay işleyici çağırır.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="b6e6f-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6e6f-147">Example</span></span>  
 <span data-ttu-id="b6e6f-148">Aşağıdaki kod örneğinde nasıl yansıma kullanarak bir olay için varolan bir yöntemi bağlanacağını ve aynı zamanda nasıl kullanılacağını gösterir <xref:System.Reflection.Emit.DynamicMethod> çalışma zamanında bir yöntem yayma ve olaya kadar kanca sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6e6f-149">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b6e6f-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b6e6f-150">C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="b6e6f-151">Hiçbir ek derleme başvurularını komut satırından derleme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="b6e6f-152">Visual Studio'da bu örnek bir konsol uygulaması olduğundan System.Windows.Forms.dll'e bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="b6e6f-153">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="b6e6f-154">Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e6f-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6e6f-155">See Also</span></span>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [<span data-ttu-id="b6e6f-156">Nasıl yapılır: dinamik yöntemleri çalıştırma ve tanımlayın</span><span class="sxs-lookup"><span data-stu-id="b6e6f-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [<span data-ttu-id="b6e6f-157">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b6e6f-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
