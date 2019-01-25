---
title: 'Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dd58cfe0eb448a4bf886eb11b1b2e6375835b05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709188"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="3e346-102">Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme</span><span class="sxs-lookup"><span data-stu-id="3e346-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="3e346-103">Aşağıdaki yordamlar tanımlama ve basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem yürütme işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3e346-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="3e346-104">Dinamik yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve [yansıma yayma dinamik yöntem senaryoları](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="3e346-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="3e346-105">Dinamik bir yöntem tanımlayıp</span><span class="sxs-lookup"><span data-stu-id="3e346-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="3e346-106">Metodunu yürütmek için bir temsilci türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="3e346-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="3e346-107">Genel temsilci bildirmenize gerek temsilci türleri sayısını en aza indirmek için kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="3e346-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="3e346-108">Aşağıdaki kod türleri için kullanılabilecek iki temsilci bildirir `SquareIt` yöntemi ve bunlardan birinin geneldir.</span><span class="sxs-lookup"><span data-stu-id="3e346-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="3e346-109">Dinamik yöntem için parametre türlerini belirten bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e346-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="3e346-110">Bu örnekte, yalnızca bir parametresi olan bir `int` (`Integer` Visual Basic'te), yalnızca bir öğe dizisi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e346-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="3e346-111">Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="3e346-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="3e346-112">Bu örnekte, yöntem adlı `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="3e346-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e346-113">Dinamik yöntemler adlar vermek gerekli değildir ve ada göre çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e346-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="3e346-114">Birden çok dinamik yöntem aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="3e346-115">Ancak, ad çağrı yığınlarıyla görüntülenir ve hata ayıklama için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="3e346-116">Dönüş değerinin türü olarak belirtilen `long`.</span><span class="sxs-lookup"><span data-stu-id="3e346-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="3e346-117">İçeren modül ile ilişkili bir yöntemdir `Example` örnek kod içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="3e346-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="3e346-118">Yüklenen bir modülün belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-118">Any loaded module could be specified.</span></span> <span data-ttu-id="3e346-119">Dinamik yöntem gibi davranır, yalnızca bir modül düzeyinde `static` yöntemi (`Shared` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="3e346-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="3e346-120">Yöntem gövdesini gösterin.</span><span class="sxs-lookup"><span data-stu-id="3e346-120">Emit the method body.</span></span> <span data-ttu-id="3e346-121">Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dilini (MSIL) göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e346-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="3e346-122">Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesini yaymak için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="3e346-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="3e346-123">Bu örnekte MSIL olan bağımsız değişkeni yükleyen bir `int`, yığın üstüne dönüştürür bir `long`, yinelenenleri `long`ve iki sayıyı çarpar.</span><span class="sxs-lookup"><span data-stu-id="3e346-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="3e346-124">Bu kare sonucu yığında bırakır ve dönüş tüm yöntemi yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e346-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="3e346-125">Dinamik yöntem çağırarak temsil eden bir (1. adımda belirtilen) temsilci örneğini oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e346-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="3e346-126">Temsilci oluşturma yöntemi tamamlandıktan ve herhangi ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="3e346-127">Aşağıdaki kod, temsilci oluşturur ve bu, Genel temsilci kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e346-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="3e346-128">Bir nesneye bağımlı dinamik bir yöntem tanımlayıp</span><span class="sxs-lookup"><span data-stu-id="3e346-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="3e346-129">Metodunu yürütmek için bir temsilci türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="3e346-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="3e346-130">Genel temsilci bildirmenize gerek temsilci türleri sayısını en aza indirmek için kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="3e346-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="3e346-131">Aşağıdaki kod, temsilci bir nesneye bağlıysa, herhangi bir yöntemle bir parametre ve dönüş değeri veya iki parametre ile bir yöntem ve bir dönüş değeri yürütmek için kullanılan genel temsilci türünde bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e346-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="3e346-132">Dinamik yöntem için parametre türlerini belirten bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e346-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="3e346-133">Yöntemi temsil eden bir temsilci bir nesneye bağlı ise, ilk parametresinin temsilci bağlı türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e346-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="3e346-134">Bu örnekte, türünün iki parametresi vardır `Example` ve türü `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="3e346-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="3e346-135">Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="3e346-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="3e346-136">Bu örnekte, yöntem adı yok.</span><span class="sxs-lookup"><span data-stu-id="3e346-136">In this example the method has no name.</span></span> <span data-ttu-id="3e346-137">Dönüş değerinin türü olarak belirtilen `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="3e346-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="3e346-138">Yöntem özel ve korumalı üyelerine erişebilir `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e346-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="3e346-139">Yöntem gövdesini gösterin.</span><span class="sxs-lookup"><span data-stu-id="3e346-139">Emit the method body.</span></span> <span data-ttu-id="3e346-140">Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dilini (MSIL) göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e346-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="3e346-141">Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesini yaymak için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="3e346-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="3e346-142">Bu örnekte MSIL bir örneği olan ilk bağımsız değişken, yükler, `Example` sınıfı ve türü özel örnek alanı değerini yüklemek için kullandığı `int`.</span><span class="sxs-lookup"><span data-stu-id="3e346-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="3e346-143">İkinci bağımsız değişkeni yüklenir ve iki sayı çarpılır.</span><span class="sxs-lookup"><span data-stu-id="3e346-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="3e346-144">Sonucu daha büyük ise `int`, değer kesilir ve en önemli bitleri atılır.</span><span class="sxs-lookup"><span data-stu-id="3e346-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="3e346-145">Yöntemi, yığında dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e346-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="3e346-146">Dinamik yöntem çağırarak temsil eden bir (1. adımda belirtilen) temsilci örneğini oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="3e346-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="3e346-147">Temsilci oluşturma yöntemi tamamlandıktan ve herhangi ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e346-148">Çağırabilirsiniz <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi hedef türünün diğer örneklerine bağlı temsilci oluşturmak için birden çok kez.</span><span class="sxs-lookup"><span data-stu-id="3e346-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="3e346-149">Aşağıdaki kod yöntemi yeni bir örneğine bağlanır `Example` sınıfı olan özel test alan, 42'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3e346-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="3e346-150">Diğer bir deyişle, her zaman temsilci örneğini çağrılan `Example` yöntemin ilk parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3e346-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="3e346-151">Temsilci `OneParameter` yönteminin ilk parametresi her zaman örneği aldığından kullanılan `Example`.</span><span class="sxs-lookup"><span data-stu-id="3e346-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="3e346-152">Temsilci çağrıldığında, yalnızca ikinci parametresi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e346-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="3e346-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e346-153">Example</span></span>  
 <span data-ttu-id="3e346-154">Aşağıdaki kod örneği, basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e346-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="3e346-155">Basit bir dinamik yöntem, tek bir bağımsız değişken bir 32 bit tamsayı ve tamsayıyı 64-bit karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e346-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="3e346-156">Genel temsilci yöntemini çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e346-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="3e346-157">İkinci bir dinamik yöntem türünde iki parametre sahip `Example` ve türü `int` (`Integer` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="3e346-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="3e346-158">Dinamik yöntem oluşturulduğunda bir örneğine bağlanır `Example`, bir bağımsız değişken türü olan genel temsilci kullanarak `int`.</span><span class="sxs-lookup"><span data-stu-id="3e346-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="3e346-159">Temsilci türünde bir bağımsız değişken yok `Example` yönteminin ilk parametresi her zaman bağlı örneğini aldığından `Example`.</span><span class="sxs-lookup"><span data-stu-id="3e346-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="3e346-160">Ne zaman temsilcisi çağrıldığında, yalnızca `int` bağımsız değişken sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e346-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="3e346-161">Bu dinamik yöntem, özel bir alan erişen `Example` sınıfı ve özel alan çarpımını döndürür ve `int` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3e346-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="3e346-162">Kod örneği, yöntemi yürütmek için kullanılan temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e346-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e346-163">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3e346-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3e346-164">C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e346-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="3e346-165">Hiçbir ek derleme başvurularını gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e346-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="3e346-166">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="3e346-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="3e346-167">Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.</span><span class="sxs-lookup"><span data-stu-id="3e346-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e346-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e346-168">See also</span></span>
- <xref:System.Reflection.Emit.DynamicMethod>
- [<span data-ttu-id="3e346-169">Yansıma yaymanın</span><span class="sxs-lookup"><span data-stu-id="3e346-169">Using Reflection Emit</span></span>](https://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)
- [<span data-ttu-id="3e346-170">Yansıma yayma dinamik yöntem senaryoları</span><span class="sxs-lookup"><span data-stu-id="3e346-170">Reflection Emit Dynamic Method Scenarios</span></span>](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
