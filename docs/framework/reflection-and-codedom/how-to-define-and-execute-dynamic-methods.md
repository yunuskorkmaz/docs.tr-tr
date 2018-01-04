---
title: "Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme"
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
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7384f625a6d1609294297645bebc335e72d1e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="c2ad9-102">Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="c2ad9-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="c2ad9-103">Aşağıdaki yordamlar, tanımlayın ve basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik yöntemi yürütme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="c2ad9-104">Dinamik yöntemleri hakkında daha fazla bilgi için bkz: <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve [yansıma yayma dinamik yöntemi senaryoları](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="c2ad9-105">Dinamik bir yöntem yürütülmeye ve tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c2ad9-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="c2ad9-106">Execute yöntemi için bir temsilci türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="c2ad9-107">Temsilci türleri bildirmeniz gerekir sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="c2ad9-108">Aşağıdaki kod, iki temsilci için kullanılabilir türleri bildirir `SquareIt` yöntemi ve bunlardan biri genel.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="c2ad9-109">Dinamik yöntemi için parametre türleri belirten bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="c2ad9-110">Bu örnekte, yalnızca parametredir bir `int` (`Integer` Visual Basic'te), dizi yalnızca tek bir öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="c2ad9-111">Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="c2ad9-112">Bu örnekte, yöntem adlı `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2ad9-113">Dinamik yöntemler adlar vermek gerekli değildir ve ada göre çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="c2ad9-114">Birden çok dinamik yöntemleri aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="c2ad9-115">Ancak, ad içinde çağrı yığınları görünür ve hata ayıklama için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="c2ad9-116">Dönüş değeri türü olarak belirtildiğinde `long`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="c2ad9-117">İçeren modülü ile ilişkili bir yöntemdir `Example` örnek kodu içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="c2ad9-118">Herhangi bir yüklenen modül belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-118">Any loaded module could be specified.</span></span> <span data-ttu-id="c2ad9-119">Modül düzeyi gibi dinamik yöntemi davranır `static` yöntemi (`Shared` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="c2ad9-120">Yöntem gövdesi yayma.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-120">Emit the method body.</span></span> <span data-ttu-id="c2ad9-121">Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dili (MSIL) yaymak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="c2ad9-122">Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesi yayma için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="c2ad9-123">Bu örnekte MSIL olan bağımsız değişkeni yükler bir `int`, yığına dönüştürür bir `long`, yinelenen `long`ve iki sayının çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="c2ad9-124">Bu squared sonuç yığında bırakır ve dönüş tüm yapmak için yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="c2ad9-125">Dinamik yöntemini çağırarak temsil eden örnek (1. adımda bildirilen) temsilcisi oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="c2ad9-126">Temsilci oluşturma yöntemi tamamlar ve herhangi bir ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="c2ad9-127">Aşağıdaki kod temsilci oluşturur ve onu, genel bir temsilci kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="c2ad9-128">Nesneye bağlı dinamik bir yöntem yürütülmeye ve tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c2ad9-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="c2ad9-129">Execute yöntemi için bir temsilci türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="c2ad9-130">Temsilci türleri bildirmeniz gerekir sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="c2ad9-131">Aşağıdaki kod, bir nesneye temsilci bağlıysa herhangi bir yöntemle bir parametre ve dönüş değeri veya iki parametrelere sahip bir yöntem ve dönüş değeri yürütmek için kullanılan bir genel temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="c2ad9-132">Dinamik yöntemi için parametre türleri belirten bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="c2ad9-133">Yöntemi temsil eden temsilci nesneye bağlı ise, ilk parametre temsilci bağlı türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="c2ad9-134">Bu örnekte, türünde iki parametre vardır `Example` ve türü `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="c2ad9-135">Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="c2ad9-136">Bu örnekte, yöntem adı yok.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-136">In this example the method has no name.</span></span> <span data-ttu-id="c2ad9-137">Dönüş değeri türü olarak belirtildiğinde `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="c2ad9-138">Yöntemi özel ve korumalı üye erişimi `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="c2ad9-139">Yöntem gövdesi yayma.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-139">Emit the method body.</span></span> <span data-ttu-id="c2ad9-140">Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dili (MSIL) yaymak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="c2ad9-141">Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesi yayma için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="c2ad9-142">Bir örneği olan ilk bağımsız değişkeni, bu örnekte MSIL yükler, `Example` sınıfı ve türünde bir özel örneği alan değeri yüklemek için kullandığı `int`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="c2ad9-143">İkinci bağımsız değişkeni yüklenir ve iki sayının çarpılmasıyla hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="c2ad9-144">Sonuç daha büyük ise `int`, değer kesilir ve en önemli BITS atılır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="c2ad9-145">Yöntemi, yığında dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="c2ad9-146">Dinamik yöntemini çağırarak temsil eden örnek (1. adımda bildirilen) temsilcisi oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> yöntemi aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="c2ad9-147">Temsilci oluşturma yöntemi tamamlar ve herhangi bir ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2ad9-148">Çağırabilirsiniz <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi birden çok kez hedef türü diğer örneklerine bağlı temsilciler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="c2ad9-149">Aşağıdaki kod yöntemi yeni bir örneğine bağlar `Example` sınıfı olan özel bir test alan 42'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="c2ad9-150">Diğer bir deyişle, her zaman temsilci örneğini çağrılan `Example` yöntemi ilk parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="c2ad9-151">Temsilci `OneParameter` yönteminin ilk parametresi her zaman örneğini aldığından kullanılan `Example`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="c2ad9-152">Temsilci çağrıldığında, yalnızca ikinci parametresi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="c2ad9-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2ad9-153">Example</span></span>  
 <span data-ttu-id="c2ad9-154">Aşağıdaki kod örneği, basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="c2ad9-155">Basit dinamik yöntemi tek bir bağımsız değişken bir 32 bit tamsayı ve 64-bit tamsayıyı karesini verir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="c2ad9-156">Genel temsilci yöntemini çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="c2ad9-157">İkinci dinamik yöntemi türü iki parametreye sahip `Example` ve türü `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="c2ad9-158">Dinamik yöntemi oluşturduğunuzda bir örneğine bağlanır `Example`, türünde bir bağımsız değişken sahip genel bir temsilci kullanarak `int`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="c2ad9-159">Temsilci türünde bir bağımsız değişken yok `Example` yönteminin ilk parametresi her zaman bağlı örneğini aldığından `Example`.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="c2ad9-160">Ne zaman temsilci çağrılır, yalnızca `int` bağımsız değişkeni sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="c2ad9-161">Dinamik bu yöntem, özel bir alan erişir `Example` sınıfı ve özel alan çarpımını döndürür ve `int` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="c2ad9-162">Kod örneği yöntemleri yürütmek için kullanılan temsilciler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2ad9-163">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c2ad9-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c2ad9-164">C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="c2ad9-165">Hiçbir ek derleme başvurularını gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="c2ad9-166">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="c2ad9-167">Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ad9-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="c2ad9-169">Yansıma kullanarak yayma</span><span class="sxs-lookup"><span data-stu-id="c2ad9-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="c2ad9-170">Yansıma yayma dinamik yöntemi senaryoları</span><span class="sxs-lookup"><span data-stu-id="c2ad9-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
