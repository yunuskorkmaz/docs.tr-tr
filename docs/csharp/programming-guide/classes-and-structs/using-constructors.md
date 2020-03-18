---
title: Constructors kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626418"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="f84e8-102">Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f84e8-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="f84e8-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="f84e8-104">Oluşturucular sınıf veya yapıyla aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başharfe adaverirler.</span><span class="sxs-lookup"><span data-stu-id="f84e8-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="f84e8-105">Aşağıdaki örnekte, adlı `Taxi` bir sınıf basit bir oluşturucu kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="f84e8-106">Bu sınıf daha sonra [yeni](../../language-reference/operators/new-operator.md) işleç ile anında.</span><span class="sxs-lookup"><span data-stu-id="f84e8-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="f84e8-107">Kurucu, `Taxi` bellek yeni nesne `new` için ayrıldıktan hemen sonra işleç tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="f84e8-108">Parametresiz yapıcı olarak adlandırılan bir oluşturucuya *parametresiz yapıcı*denir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="f84e8-109">Parametresiz yapıcılar, bir nesne `new` işleç kullanılarak anında anında çağrıldığınızda ve `new`hiçbir bağımsız değişken sağlanmadığında.</span><span class="sxs-lookup"><span data-stu-id="f84e8-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="f84e8-110">Daha fazla bilgi için [Bkz. Örnek Oluşturucular.](./instance-constructors.md)</span><span class="sxs-lookup"><span data-stu-id="f84e8-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="f84e8-111">Sınıf [statik](../../language-reference/keywords/static.md)olmadığı sürece, oluşturucuolmayan sınıflara c# derleyicisi tarafından sınıf anlık oluşturmayı etkinleştirmek için ortak parametresiz bir yapıyapıcı verilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="f84e8-112">Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f84e8-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="f84e8-113">Aşağıdaki gibi, oluşturucu özel yaparak bir sınıfın anlık olmasını önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f84e8-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="f84e8-114">Daha fazla bilgi için Bkz. [Özel Yapıcılar.](./private-constructors.md)</span><span class="sxs-lookup"><span data-stu-id="f84e8-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="f84e8-115">[Yapı](../../language-reference/builtin-types/struct.md) türleri için oluşturucular sınıf oluşturucularına `structs` benzer, ancak derleyici tarafından otomatik olarak sağlandığı için açık bir parametresiz oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="f84e8-115">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="f84e8-116">Bu oluşturucu varsayılan `struct` [değerdeki](../../language-reference/builtin-types/default-values.md)her alanı başharfe döndürdü.</span><span class="sxs-lookup"><span data-stu-id="f84e8-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="f84e8-117">Ancak, bu parametresiz oluşturucu yalnızca `struct` `new`.</span><span class="sxs-lookup"><span data-stu-id="f84e8-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="f84e8-118">Örneğin, bu kod parametresiz oluşturucuyu <xref:System.Int32>kullanır, böylece tamsayının baş harfe harfle başharfe atılacağından emin olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f84e8-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="f84e8-119">Ancak, aşağıdaki kod, kullanmadığı `new`ve baş harflere başledilmemiş bir nesneyi kullanmaya çalıştığından derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="f84e8-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="f84e8-120">Alternatif olarak, (tüm `structs` yerleşik sayısal türler dahil) temel alan nesneler baş harflerle başharflere alınabilir veya atanabilir ve aşağıdaki örnekte olduğu gibi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f84e8-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="f84e8-121">Bu nedenle, parametresiz oluşturucuyu bir değer türü için çağırmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="f84e8-122">Her iki `structs` sınıf ve parametreleri alan yapıcılar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f84e8-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="f84e8-123">Parametreleri alan yapıcılar bir `new` deyim veya [temel](../../language-reference/keywords/base.md) deyim aracılığıyla çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="f84e8-124">Sınıflar `structs` ve aynı zamanda birden çok oluşturucu tanımlayabilirsiniz ve ne parametresiz bir oluşturucu tanımlamak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="f84e8-125">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f84e8-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="f84e8-126">Bu sınıf aşağıdaki ifadelerden biri kullanılarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="f84e8-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="f84e8-127">Bir oluşturucu, `base` bir taban sınıfın oluşturucusu aramak için anahtar sözcüğü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f84e8-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="f84e8-128">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f84e8-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="f84e8-129">Bu örnekte, taban sınıf için oluşturucu, oluşturucu için blok yürütülmeden önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="f84e8-130">Anahtar `base` kelime parametreleri ile veya olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="f84e8-131">Oluşturucuya ait parametreler, bir `base`ifadenin parametreleri olarak veya bir ifadenin parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="f84e8-132">Daha fazla bilgi için [temele](../../language-reference/keywords/base.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f84e8-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="f84e8-133">Türemiş bir sınıfta, bir taban sınıf oluşturucu `base` anahtar sözcüğü kullanılarak açıkça çağrılmazsa, parametresiz oluşturucu, varsa, örtülü olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="f84e8-134">Bu, aşağıdaki oluşturucu bildirimlerin etkili bir şekilde aynı olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="f84e8-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="f84e8-135">Taban sınıf parametresiz bir oluşturucu sunmuyorsa, türetilmiş sınıfın kullanarak bir `base`temel oluşturucuya açık bir çağrı yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="f84e8-136">Bir oluşturucu [bu](../../language-reference/keywords/this.md) anahtar sözcüğü kullanarak aynı nesnedeki başka bir oluşturucuyu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="f84e8-137">Gibi `base` `this` , parametreleri ile veya olmadan kullanılabilir ve oluşturucu herhangi `this`bir parametre parametreleri olarak kullanılabilir , ya da bir ifadenin bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="f84e8-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="f84e8-138">Örneğin, önceki örnekteki ikinci oluşturucu aşağıdakiler `this`kullanılarak yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="f84e8-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="f84e8-139">Önceki örnekte `this` anahtar kelimenin kullanımı bu oluşturucunun çağrılmasını neden olur:</span><span class="sxs-lookup"><span data-stu-id="f84e8-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="f84e8-140">Yapıcılar [kamu,](../../language-reference/keywords/public.md) [özel,](../../language-reference/keywords/private.md) [korumalı,](../../language-reference/keywords/protected.md) [dahili,](../../language-reference/keywords/internal.md) [korumalı iç](../../language-reference/keywords/protected-internal.md) veya özel [korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="f84e8-141">Bu erişim değiştiriciler, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f84e8-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="f84e8-142">Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f84e8-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f84e8-143">Bir oluşturucu [statik](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f84e8-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="f84e8-144">Statik oluşturucular, statik alanlara erişilmeden hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmaya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="f84e8-145">Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f84e8-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f84e8-146">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f84e8-146">C# Language Specification</span></span>  

<span data-ttu-id="f84e8-147">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [Statik oluşturucular'a](~/_csharplang/spec/classes.md#static-constructors) bakın.</span><span class="sxs-lookup"><span data-stu-id="f84e8-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f84e8-148">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="f84e8-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f84e8-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f84e8-149">See also</span></span>

- [<span data-ttu-id="f84e8-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f84e8-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f84e8-151">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="f84e8-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f84e8-152">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f84e8-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="f84e8-153">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="f84e8-153">Finalizers</span></span>](./destructors.md)
