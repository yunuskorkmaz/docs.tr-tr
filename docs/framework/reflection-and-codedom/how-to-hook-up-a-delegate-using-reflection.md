---
title: 'Nasıl yapılır: Yansıma kullanarak temsilci bağlama'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe90542d1ba106dd52e8995afab298b4b9f69899
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644397"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="91c18-102">Nasıl yapılır: Yansıma kullanarak temsilci bağlama</span><span class="sxs-lookup"><span data-stu-id="91c18-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="91c18-103">Yansıma yüklemek ve derlemeleri çalıştırmak için kullandığınız zaman gibi dil özellikleri kullanamazsınız C# `+=` işleci veya Visual Basic [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) olayları yeteneklerinizi.</span><span class="sxs-lookup"><span data-stu-id="91c18-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="91c18-104">Aşağıdaki yordamlar, gerekli tüm türlerin yansıma yoluyla alarak bir olay için varolan bir yöntem denetime nasıl gösterir ve yansıma kullanarak dinamik bir yöntem oluşturma yayma ve en fazla olay bağlama.</span><span class="sxs-lookup"><span data-stu-id="91c18-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91c18-105">Kod örneği için bir olay işleme temsilci bağlama başka bir yol için bkz <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi <xref:System.Reflection.EventInfo> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="91c18-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="91c18-106">Yansıma kullanarak temsilci bağlama için</span><span class="sxs-lookup"><span data-stu-id="91c18-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="91c18-107">Olayları oluşturan bir tür içeren bir bütünleştirilmiş kod yükleme.</span><span class="sxs-lookup"><span data-stu-id="91c18-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="91c18-108">Derlemeler ile yüklenen genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91c18-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="91c18-109">Bu örneği basit tutmak için geçerli derlemedeki türetilmiş bir form kullanılır, böylece <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi geçerli derlemeyi yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91c18-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="91c18-110">Alma bir <xref:System.Type> türünü temsil eden nesne ve türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="91c18-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="91c18-111"><xref:System.Activator.CreateInstance%28System.Type%29> Biçiminde varsayılan bir oluşturucuya sahip olduğundan aşağıdaki kodda yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91c18-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="91c18-112">Birkaç diğer aşırı yüklemeleri vardır <xref:System.Activator.CreateInstance%2A> oluşturmakta olduğunuz türü varsayılan bir oluşturucuya sahip değilse, kullanabileceğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91c18-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="91c18-113">Yeni örnek türü olarak saklanır <xref:System.Object> kurgu korumak için hiçbir şeyin hakkında derleme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="91c18-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="91c18-114">(Yansıma türlerini adlarını önceden farkında olmadan bir derlemede yararlanmanıza olanak sağlar.)</span><span class="sxs-lookup"><span data-stu-id="91c18-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="91c18-115">Alma bir <xref:System.Reflection.EventInfo> olayı temsil eden nesne ve kullanmak <xref:System.Reflection.EventInfo.EventHandlerType%2A> olayı işlemek için kullanılan temsilci türünü alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="91c18-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="91c18-116">Aşağıdaki kodda bir <xref:System.Reflection.EventInfo> için <xref:System.Windows.Forms.Control.Click> olay elde edilir.</span><span class="sxs-lookup"><span data-stu-id="91c18-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="91c18-117">Alma bir <xref:System.Reflection.MethodInfo> olayı işleyen yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="91c18-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="91c18-118">Örnek bölümünde bu konunun ilerleyen bölümlerinde tam program kodunda imzası eşleşen bir yöntem içerir <xref:System.EventHandler> temsilcisi, yürüten <xref:System.Windows.Forms.Control.Click> olay, ancak aynı zamanda oluşturabileceği dinamik yöntemler çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="91c18-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="91c18-119">Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamı, Ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="91c18-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="91c18-120">Kullanarak temsilci örneğini oluşturmak <xref:System.Delegate.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91c18-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="91c18-121">Bu yöntem statiktir (`Shared` Visual Basic'te), temsilci türü sağlanmalı.</span><span class="sxs-lookup"><span data-stu-id="91c18-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="91c18-122">Aşırı yüklemeleri kullanılarak <xref:System.Delegate.CreateDelegate%2A> süren bir <xref:System.Reflection.MethodInfo> önerilir.</span><span class="sxs-lookup"><span data-stu-id="91c18-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="91c18-123">Alma `add` erişimci yöntemi ve bu olay yeteneklerinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="91c18-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="91c18-124">Tüm olayları sahip bir `add` erişimci ve `remove` üst düzey dillerin sözdizimi tarafından gizlenmiş erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="91c18-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="91c18-125">Örneğin, C# kullanan `+=` olayları ve Visual Basic kullanan yeteneklerinizi işleci [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="91c18-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="91c18-126">Aşağıdaki kod alır `add` erişimcisine <xref:System.Windows.Forms.Control.Click> olay ve çağırdığı geç temsilci örneğini geçirerek bağlama,.</span><span class="sxs-lookup"><span data-stu-id="91c18-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="91c18-127">Bağımsız değişken bir dizi olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="91c18-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="91c18-128">Olay test edin.</span><span class="sxs-lookup"><span data-stu-id="91c18-128">Test the event.</span></span> <span data-ttu-id="91c18-129">Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan bir form gösterir.</span><span class="sxs-lookup"><span data-stu-id="91c18-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="91c18-130">Form tıklayarak olay işleyicisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="91c18-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="91c18-131">Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="91c18-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="91c18-132">Olay işleyicisi yöntemleri basit dinamik yöntemler kullanarak çalışma zamanında oluşturulabilir ve yansıma yayma.</span><span class="sxs-lookup"><span data-stu-id="91c18-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="91c18-133">Bir olay işleyicisi oluşturmak için dönüş türü ve parametre türleri temsilci gerekir.</span><span class="sxs-lookup"><span data-stu-id="91c18-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="91c18-134">Bu temsilcinin inceleyerek alınabilir `Invoke` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91c18-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="91c18-135">Aşağıdaki kod `GetDelegateReturnType` ve `GetDelegateParameterTypes` bu bilgileri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="91c18-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="91c18-136">Bu yöntemleri için kod, bu konunun ilerleyen bölümlerinde örnek bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="91c18-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="91c18-137">Ad için gerekli değil bir <xref:System.Reflection.Emit.DynamicMethod>, bu nedenle boş dize kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91c18-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="91c18-138">Aşağıdaki kodda, dinamik yöntem son bağımsız değişken, temsilci erişimi tüm genel ve özel üyelerine vererek geçerli türü ile ilişkilendirir. `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="91c18-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="91c18-139">Bir yöntem gövdesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91c18-139">Generate a method body.</span></span> <span data-ttu-id="91c18-140">Bu yöntem bir dize yükler, aşırı yüklemesini çağırır <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> (işleyicisi yok dönüş türüne sahip olduğundan) yönteminin bir dize alan POP yığından dönüş değeri ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="91c18-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="91c18-141">Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="91c18-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="91c18-142">Dinamik yöntem çağırarak tamamlamak kendi <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91c18-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="91c18-143">Kullanım `add` çağırma listesi olayı için temsilci eklemek için erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="91c18-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="91c18-144">Olay test edin.</span><span class="sxs-lookup"><span data-stu-id="91c18-144">Test the event.</span></span> <span data-ttu-id="91c18-145">Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formu yükler.</span><span class="sxs-lookup"><span data-stu-id="91c18-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="91c18-146">Form tıklayarak, önceden tanımlanmış bir olay işleyicisi hem yayılan olay işleyicisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="91c18-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="91c18-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="91c18-147">Example</span></span>  
 <span data-ttu-id="91c18-148">Aşağıdaki kod örneğinde nasıl yansıma kullanarak bir olay için varolan bir yöntem bağlama ve nasıl kullanılacağını gösterir. <xref:System.Reflection.Emit.DynamicMethod> en fazla olay bağlama ve çalışma zamanında bir yöntem yaymak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="91c18-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="91c18-149">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="91c18-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="91c18-150">C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="91c18-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="91c18-151">Hiçbir ek derleme başvuruları, komut satırından derleme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="91c18-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="91c18-152">Bu örnek bir konsol uygulaması olduğundan, Visual Studio'da System.Windows.Forms.dll'e bir başvuru eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="91c18-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="91c18-153">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="91c18-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="91c18-154">Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.</span><span class="sxs-lookup"><span data-stu-id="91c18-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c18-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91c18-155">See also</span></span>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="91c18-156">Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme</span><span class="sxs-lookup"><span data-stu-id="91c18-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="91c18-157">Yansıma</span><span class="sxs-lookup"><span data-stu-id="91c18-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
