---
title: "Oluşturucular Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb9fcd1e4090da300de17c7fd808669ba51767c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="b5acb-102">Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b5acb-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="b5acb-103">Zaman bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan kurucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b5acb-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="b5acb-104">Oluşturucular sınıfta veya yapı aynı ada sahip ve bunlar genellikle yeni nesnenin veri üyeleri başlatma.</span><span class="sxs-lookup"><span data-stu-id="b5acb-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="b5acb-105">Aşağıdaki örnekte, adlı bir sınıf `Taxi` basit bir oluşturucu kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b5acb-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="b5acb-106">Bu sınıf sonra ile örneği [yeni](../../../csharp/language-reference/keywords/new.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="b5acb-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="b5acb-107">`Taxi` Oluşturucusu tarafından çağrıldığında `new` işleci bellek hemen sonra yeni nesne için ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b5acb-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="b5acb-108">Parametre almayan bir oluşturucu adlı bir *varsayılan oluşturucu*.</span><span class="sxs-lookup"><span data-stu-id="b5acb-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="b5acb-109">Varsayılan Oluşturucu kullanarak bir nesne örneği olduğunda çağrılır `new` işleci ve bağımsız değişkenler için sağlanan `new`.</span><span class="sxs-lookup"><span data-stu-id="b5acb-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="b5acb-110">Daha fazla bilgi için bkz: [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="b5acb-111">Bir sınıf olmadığı sürece [statik](../../../csharp/language-reference/keywords/static.md), Oluşturucular, sınıf örneklemesi etkinleştirmek için C# Derleyici tarafından ortak varsayılan bir oluşturucu verilir olmadan sınıfları.</span><span class="sxs-lookup"><span data-stu-id="b5acb-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="b5acb-112">Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="b5acb-113">Bir sınıf oluşturucu özel, aşağıdaki gibi yaparak oluşturulmasını engelleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b5acb-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="b5acb-114">Daha fazla bilgi için bkz: [özel oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="b5acb-115">Oluşturucuları için [yapısı](../../../csharp/language-reference/keywords/struct.md) türleri sınıf Oluşturucular, benzer ancak `structs` bir derleyici tarafından otomatik olarak sağlandığından açık varsayılan bir oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="b5acb-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="b5acb-116">Bu oluşturucu, her bir alan başlatır `struct` varsayılan değerlere.</span><span class="sxs-lookup"><span data-stu-id="b5acb-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="b5acb-117">Daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="b5acb-118">Ancak, bu varsayılan kurucu yalnızca, çağrılan `struct` ile örneği `new`.</span><span class="sxs-lookup"><span data-stu-id="b5acb-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="b5acb-119">Örneğin, bu kod için varsayılan oluşturucu kullanır <xref:System.Int32>, böylece tamsayı başlatıldığını garanti:</span><span class="sxs-lookup"><span data-stu-id="b5acb-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="b5acb-120">Kullanmaz aşağıdaki kod, ancak bir derleyici hatasına neden olur `new`, ve başlatılmamış bir nesne kullanmayı dener:</span><span class="sxs-lookup"><span data-stu-id="b5acb-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="b5acb-121">Alternatif olarak, nesneleri temel alarak `structs` (tüm yerleşik sayısal türler dahil) başlatıldı veya atanabilir ve aşağıdaki örnekte olduğu gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b5acb-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="b5acb-122">Bu nedenle bir değer türü için varsayılan oluşturucu çağırma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b5acb-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="b5acb-123">Her iki sınıfları ve `structs` parametre almaz oluşturucular tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5acb-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="b5acb-124">Parametre almaz oluşturucular çağrılır, üzerinden bir `new` deyimi veya [temel](../../../csharp/language-reference/keywords/base.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="b5acb-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="b5acb-125">Sınıfları ve `structs` hiçbiri varsayılan bir oluşturucu tanımlamak için gereklidir ve birden çok oluşturucular de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5acb-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="b5acb-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5acb-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="b5acb-127">Bu sınıf, aşağıdaki deyimleri birini kullanarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="b5acb-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="b5acb-128">Bir oluşturucu kullanın `base` bir temel sınıf aranacak anahtar.</span><span class="sxs-lookup"><span data-stu-id="b5acb-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="b5acb-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5acb-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="b5acb-130">Blok Oluşturucu için yürütülmeden önce bu örnekte, temel sınıfın Oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b5acb-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="b5acb-131">`base` Anahtar sözcüğü ile veya olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5acb-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="b5acb-132">Oluşturucuya herhangi bir parametre için parametre olarak kullanılan `base`, veya bir ifadenin bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="b5acb-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="b5acb-133">Daha fazla bilgi için bkz: [temel](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="b5acb-134">Bir temel sınıf oluşturucu açıkça kullanarak çağrılmazsa türetilmiş bir sınıf içinde `base` anahtar sözcüğü, varsayılan oluşturucu varsa, adlandırılan örtük olarak.</span><span class="sxs-lookup"><span data-stu-id="b5acb-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="b5acb-135">Bu aşağıdaki Oluşturucusu bildirimlerini etkili bir şekilde aynı anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="b5acb-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="b5acb-136">Bir temel sınıf varsayılan bir oluşturucu vermiyorsa türetilmiş sınıf temel oluşturucu için açık bir çağrı kullanılarak olmalısınız `base`.</span><span class="sxs-lookup"><span data-stu-id="b5acb-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="b5acb-137">Bir Oluşturucu kullanarak aynı nesnede başka bir oluşturucuyu çağırabileceği [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b5acb-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="b5acb-138">Gibi `base`, `this` ile veya parametresiz kullanılabilir ve oluşturucuda herhangi bir parametre için parametre olarak kullanılabilir `this`, veya bir ifadenin bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="b5acb-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="b5acb-139">Örneğin, önceki örnekte ikinci oluşturucu kullanılarak yazılabilir `this`:</span><span class="sxs-lookup"><span data-stu-id="b5acb-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="b5acb-140">Kullanımını `this` anahtar sözcüğü önceki örnekte çağrılacak bu oluşturucuyu neden olur:</span><span class="sxs-lookup"><span data-stu-id="b5acb-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="b5acb-141">Oluşturucular işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="b5acb-142">Bu erişim değiştiricileri sınıfı kullanıcılarının sınıfı nasıl oluşturabileceğiniz tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b5acb-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="b5acb-143">Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="b5acb-144">Bir Oluşturucu kullanarak statik bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b5acb-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="b5acb-145">Statik oluşturucular hemen statik alanları erişilen ve statik sınıf üyeleri başlatmak için genellikle kullanılan önce otomatik olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5acb-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="b5acb-146">Daha fazla bilgi için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b5acb-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b5acb-147">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b5acb-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5acb-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5acb-148">See Also</span></span>  
 [<span data-ttu-id="b5acb-149">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b5acb-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b5acb-150">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="b5acb-150">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="b5acb-151">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b5acb-151">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="b5acb-152">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="b5acb-152">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
