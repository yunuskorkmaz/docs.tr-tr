---
title: Oluşturucuları - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 0d324cadee556552098710310cce7f192b9b4d9e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975166"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="af516-102">Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="af516-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="af516-103">Olduğunda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan, kendi Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af516-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="af516-104">Oluşturucular sınıf veya yapının aynı ada sahip ve bunlar genellikle yeni nesnenin veri üyeleri başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="af516-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="af516-105">Aşağıdaki örnekte, bir sınıf adlı `Taxi` basit bir oluşturucu kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="af516-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="af516-106">Bu sınıf ile Örneklendirilmiş [yeni](../../../csharp/language-reference/keywords/new.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="af516-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="af516-107">`Taxi` Oluşturucusu tarafından çağrıldığında `new` işleci bellek hemen sonra yeni nesne için ayrılır.</span><span class="sxs-lookup"><span data-stu-id="af516-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="af516-108">Herhangi bir parametre alan bir oluşturucu olarak adlandırılan bir *varsayılan oluşturucu*.</span><span class="sxs-lookup"><span data-stu-id="af516-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="af516-109">Varsayılan Oluşturucu çağrılır kullanarak bir nesne örneği her `new` işleci ve herhangi bir bağımsız değişken için sağlanan `new`.</span><span class="sxs-lookup"><span data-stu-id="af516-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="af516-110">Daha fazla bilgi için [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="af516-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="af516-111">Bir sınıf olmadığı sürece [statik](../../../csharp/language-reference/keywords/static.md), Oluşturucular, sınıf örnekleme etkinleştirmek için C# derleyicisi tarafından genel bir varsayılan oluşturucu verilen olmayan sınıflar.</span><span class="sxs-lookup"><span data-stu-id="af516-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="af516-112">Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="af516-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="af516-113">Bir sınıf oluşturucu özel gibi yaparak oluşturulmasını engelleyebilir:</span><span class="sxs-lookup"><span data-stu-id="af516-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="af516-114">Daha fazla bilgi için [özel oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="af516-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="af516-115">Oluşturucular için [yapı](../../../csharp/language-reference/keywords/struct.md) türleri sınıf oluşturucuları, benzer ancak `structs` bir derleyici tarafından otomatik olarak sağlandığından, açık bir varsayılan oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="af516-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="af516-116">Bu oluşturucu her alanda başlatır `struct` için varsayılan değerleri.</span><span class="sxs-lookup"><span data-stu-id="af516-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="af516-117">Daha fazla bilgi için [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="af516-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="af516-118">Ancak, bu varsayılan oluşturucu yalnızca, çağrılan `struct` ile örneği `new`.</span><span class="sxs-lookup"><span data-stu-id="af516-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="af516-119">Örneğin, bu kod için varsayılan oluşturucu kullanan <xref:System.Int32>, böylece tamsayı başlatıldığından emin olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="af516-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="af516-120">Kullanmaz çünkü aşağıdaki kod, ancak bir derleyici hatasına neden `new`, ve onu başlatılmamış bir nesne kullanmayı dener:</span><span class="sxs-lookup"><span data-stu-id="af516-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="af516-121">Alternatif olarak, nesneler temel `structs` (tüm yerleşik sayısal türler dahil) başlatıldı veya atanabilir ve sonra aşağıdaki örnekte olduğu gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="af516-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="af516-122">Varsayılan Oluşturucu için bir değer türü yöntemini çağırır; dolayısıyla, gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="af516-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="af516-123">Her iki sınıfları ve `structs` parametre oluşturucular tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af516-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="af516-124">Parametre oluşturucular çağırılır, aracılığıyla bir `new` deyimi veya bir [temel](../../../csharp/language-reference/keywords/base.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="af516-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="af516-125">Sınıfları ve `structs` birden çok oluşturucular da tanımlayabilirsiniz ve bunların hiçbiri varsayılan oluşturucuyu tanımlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af516-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="af516-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="af516-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="af516-127">Bu sınıf aşağıdaki deyimleri kullanarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="af516-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="af516-128">Bir oluşturucu kullanabilirsiniz `base` bir taban sınıfın oluşturucuyu çağırmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="af516-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="af516-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="af516-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="af516-130">Blok Oluşturucu için yürütülmeden önce bu örnekte, temel sınıf için oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af516-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="af516-131">`base` Parametrelerle veya parametresiz anahtar sözcüğü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af516-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="af516-132">Oluşturucu herhangi bir parametre için parametre olarak kullanılan `base`, veya bir ifade parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="af516-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="af516-133">Daha fazla bilgi için [temel](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="af516-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="af516-134">Bir temel sınıf oluşturucusu kullanarak açıkça çağrılmaz, türetilmiş bir sınıf içinde `base` anahtar sözcüğü, varsayılan oluşturucusu varsa, çağrıldığında örtük olarak.</span><span class="sxs-lookup"><span data-stu-id="af516-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="af516-135">Bu aşağıdaki Oluşturucusu bildirimleri etkili bir şekilde aynı anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="af516-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="af516-136">Bir temel sınıf varsayılan bir oluşturucu sağlamaz, türetilen sınıfın temel oluşturucu için açık çağrı kullanarak yapmalısınız `base`.</span><span class="sxs-lookup"><span data-stu-id="af516-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="af516-137">Bir kurucu kullanarak aynı nesnede başka bir oluşturucu çağırabilirsiniz [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="af516-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="af516-138">Gibi `base`, `this` parametrelerle veya parametresiz kullanılabilir ve oluşturucu içinde herhangi bir parametre için parametre olarak kullanılabilir `this`, veya bir ifade parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="af516-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="af516-139">Örneğin, önceki örnekte ikinci oluşturucu kullanılarak yazılabilir `this`:</span><span class="sxs-lookup"><span data-stu-id="af516-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="af516-140">Kullanımını `this` önceki örnekte anahtar sözcüğü bu oluşturucunun çağrılması neden olur:</span><span class="sxs-lookup"><span data-stu-id="af516-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="af516-141">Oluşturucular olarak işaretlenebilir [genel](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="af516-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="af516-142">Bu erişim değiştiricileri kullanıcılar sınıfın sınıf nasıl oluşturabilir tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="af516-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="af516-143">Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="af516-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="af516-144">Bir kurucu kullanarak statik bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="af516-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="af516-145">Statik oluşturucular hemen tüm statik alanları erişilir ve statik sınıf üyeleri başlatmak için genellikle kullanılan önce otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af516-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="af516-146">Daha fazla bilgi için [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="af516-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="af516-147">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="af516-147">C# Language Specification</span></span>  

<span data-ttu-id="af516-148">Daha fazla bilgi için [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="af516-148">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="af516-149">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="af516-149">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="af516-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af516-150">See also</span></span>

- [<span data-ttu-id="af516-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af516-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="af516-152">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="af516-152">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="af516-153">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="af516-153">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="af516-154">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="af516-154">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
