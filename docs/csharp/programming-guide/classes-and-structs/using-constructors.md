---
title: Oluşturucular kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: dab8466b4d40e318bbb9915c06ce4ac836c0ead0
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205436"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="cbfad-102">Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cbfad-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="cbfad-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="cbfad-104">Oluşturucular, sınıf veya struct ile aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="cbfad-105">Aşağıdaki örnekte, adlı `Taxi` bir sınıf basit bir Oluşturucu kullanılarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="cbfad-106">Bu sınıf daha sonra [New](../../language-reference/operators/new-operator.md) işleciyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cbfad-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="cbfad-107">Oluşturucu, yeni nesne için bellek `new` ayrıldıktan hemen sonra operatör tarafından çağrılır. `Taxi`</span><span class="sxs-lookup"><span data-stu-id="cbfad-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="cbfad-108">*Parametresiz Oluşturucu*olarak hiçbir parametre alan bir oluşturucuya.</span><span class="sxs-lookup"><span data-stu-id="cbfad-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="cbfad-109">Parametresiz oluşturucular, `new` bir nesne işleci kullanılarak oluşturulduğunda ve için `new`bağımsız değişken sağlanamadığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="cbfad-110">Daha fazla bilgi için bkz. [örnek oluşturucular](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="cbfad-111">Sınıf [statik](../../language-reference/keywords/static.md)olmadığı takdirde, oluşturucuları olmayan sınıflara sınıf örneğini etkinleştirmek için C# derleyici tarafından ortak parametresiz bir Oluşturucu verilirler.</span><span class="sxs-lookup"><span data-stu-id="cbfad-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="cbfad-112">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="cbfad-113">Aşağıdaki gibi, oluşturucuyu özel yaparak bir sınıfın örneğinin oluşturulmasını engelleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbfad-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="cbfad-114">Daha fazla bilgi için bkz. [özel oluşturucular](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="cbfad-115">[Yapı](../../language-reference/keywords/struct.md) türleri için oluşturucular Sınıf oluşturuculara benzer, ancak `structs` derleyici tarafından otomatik olarak sağlandığı için açık bir parametresiz oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="cbfad-115">Constructors for [struct](../../language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="cbfad-116">Bu Oluşturucu, `struct` içindeki her bir alanı varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="cbfad-117">Daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-117">For more information, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="cbfad-118">Ancak, parametresiz Oluşturucu yalnızca ile `struct` `new`örneği belirtilmişse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-118">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="cbfad-119">Örneğin, bu kod, için <xref:System.Int32>parametresiz oluşturucuyu kullanır, böylece tamsayı başlatılmış olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cbfad-119">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="cbfad-120">Ancak, aşağıdaki kod, bir derleyici hatasına neden olur çünkü kullanmaz `new`ve başlatılmamış bir nesneyi kullanmaya çalışır:</span><span class="sxs-lookup"><span data-stu-id="cbfad-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="cbfad-121">Alternatif olarak, `structs` (tüm yerleşik sayısal türler dahil) tabanlı nesneler başlatılabilir veya atanabilir ve sonra aşağıdaki örnekte olduğu gibi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cbfad-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="cbfad-122">Bu nedenle, bir değer türü için parametresiz oluşturucunun çağrılması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-122">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="cbfad-123">Her iki sınıf `structs` de, parametreleri alan oluşturucular tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="cbfad-124">Parametreleri alan oluşturucuların bir `new` ifade veya bir [temel](../../language-reference/keywords/base.md) deyimden çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-124">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="cbfad-125">Sınıflar ve `structs` Ayrıca birden çok Oluşturucu tanımlayabilir ve parametresiz bir Oluşturucu tanımlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cbfad-125">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="cbfad-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cbfad-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="cbfad-127">Bu sınıf aşağıdaki deyimlerden herhangi biri kullanılarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="cbfad-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="cbfad-128">Bir Oluşturucu, bir temel `base` sınıfın yapıcısını çağırmak için anahtar sözcüğünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="cbfad-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cbfad-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="cbfad-130">Bu örnekte, Oluşturucu için blok yürütülmeden önce temel sınıfın Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="cbfad-131">`base` Anahtar sözcüğü parametresiz ya da olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="cbfad-132">Oluşturucuya yönelik parametreler, bir ifadenin parçası olarak veya için `base`parametre olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="cbfad-133">Daha fazla bilgi için bkz. [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-133">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="cbfad-134">Türetilmiş bir sınıfta, bir temel sınıf Oluşturucu `base` anahtar sözcüğü kullanılarak açıkça çağrılmamasından, varsa parametresiz Oluşturucu örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="cbfad-135">Bu, aşağıdaki Oluşturucu bildirimlerinin etkili bir şekilde aynı olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="cbfad-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="cbfad-136">Bir temel sınıf parametresiz bir Oluşturucu sunmuyor ise, türetilmiş sınıf kullanarak `base`temel oluşturucuya açık bir çağrı yapmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-136">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="cbfad-137">[Bu](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanarak bir Oluşturucu aynı nesnede başka bir Oluşturucu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-137">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="cbfad-138">Benzer `base`şekilde `this` , parametresiz veya parametresiz olarak kullanılabilir ve kurucudaki tüm parametreler, için `this`parametre olarak veya bir ifadenin parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="cbfad-139">Örneğin, önceki örnekteki ikinci Oluşturucu kullanılarak `this`yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="cbfad-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="cbfad-140">Önceki örnekte `this` anahtar sözcüğünün kullanılması, bu oluşturucunun çağrılmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="cbfad-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="cbfad-141">Oluşturucular [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korunan](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="cbfad-141">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="cbfad-142">Bu erişim değiştiricileri, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğinize ilişkin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbfad-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="cbfad-143">Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-143">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="cbfad-144">Bir Oluşturucu [static](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="cbfad-144">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="cbfad-145">Statik oluşturucular, herhangi bir statik alana erişildikten hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="cbfad-146">Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="cbfad-146">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cbfad-147">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="cbfad-147">C# Language Specification</span></span>  

<span data-ttu-id="cbfad-148">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) .</span><span class="sxs-lookup"><span data-stu-id="cbfad-148">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="cbfad-149">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="cbfad-149">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cbfad-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbfad-150">See also</span></span>

- [<span data-ttu-id="cbfad-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbfad-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cbfad-152">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="cbfad-152">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="cbfad-153">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="cbfad-153">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="cbfad-154">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="cbfad-154">Finalizers</span></span>](./destructors.md)
