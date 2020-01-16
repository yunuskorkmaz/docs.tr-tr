---
title: Oluşturucular kullanma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: faab6ac57629db11c60ee5b563ea95ebb90016dd
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964354"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="83152-102">Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="83152-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="83152-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="83152-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="83152-104">Oluşturucular, sınıf veya struct ile aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="83152-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="83152-105">Aşağıdaki örnekte, `Taxi` adlı bir sınıf basit bir Oluşturucu kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="83152-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="83152-106">Bu sınıf daha sonra [New](../../language-reference/operators/new-operator.md) işleciyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="83152-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="83152-107">`Taxi` Oluşturucusu, yeni nesne için bellek ayrıldıktan hemen sonra `new` işleci tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="83152-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="83152-108">*Parametresiz Oluşturucu*olarak hiçbir parametre alan bir oluşturucuya.</span><span class="sxs-lookup"><span data-stu-id="83152-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="83152-109">Parametresiz oluşturucular, bir nesne `new` işleci kullanılarak örneklendiğinde ve `new`için herhangi bir bağımsız değişken sağlanmadıkça çağrılır.</span><span class="sxs-lookup"><span data-stu-id="83152-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="83152-110">Daha fazla bilgi için bkz. [örnek oluşturucular](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="83152-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="83152-111">Sınıf [statik](../../language-reference/keywords/static.md)olmadığı takdirde, oluşturucuları olmayan sınıflara sınıf örneğini etkinleştirmek için C# derleyici tarafından ortak parametresiz bir Oluşturucu verilirler.</span><span class="sxs-lookup"><span data-stu-id="83152-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="83152-112">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="83152-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="83152-113">Aşağıdaki gibi, oluşturucuyu özel yaparak bir sınıfın örneğinin oluşturulmasını engelleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="83152-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="83152-114">Daha fazla bilgi için bkz. [özel oluşturucular](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="83152-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="83152-115">[Yapı](../../language-reference/keywords/struct.md) türleri için oluşturucular Sınıf oluşturuculara benzer, ancak `structs` derleyici tarafından otomatik olarak sağlandığı için açık parametresiz bir oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="83152-115">Constructors for [struct](../../language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="83152-116">Bu Oluşturucu `struct` her alanı [varsayılan değere](../../language-reference/builtin-types/default-values.md)başlatır.</span><span class="sxs-lookup"><span data-stu-id="83152-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="83152-117">Ancak, bu parametresiz Oluşturucu yalnızca `struct` `new`ile birlikte oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="83152-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="83152-118">Örneğin, bu kod, tamsayının başlatıldığından emin olmak için <xref:System.Int32>parametresiz oluşturucuyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="83152-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="83152-119">Ancak, aşağıdaki kod, bir derleyici hatasına neden olur çünkü `new`kullanmaz ve başlatılmamış bir nesneyi kullanmaya çalışır:</span><span class="sxs-lookup"><span data-stu-id="83152-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="83152-120">Alternatif olarak, `structs` tabanlı nesneler (tüm yerleşik sayısal türler dahil) başlatılabilir veya atanabilir ve daha sonra aşağıdaki örnekte olduğu gibi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="83152-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="83152-121">Bu nedenle, bir değer türü için parametresiz oluşturucunun çağrılması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="83152-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="83152-122">Her iki sınıf ve `structs` de parametre alma oluşturucuları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="83152-123">Parametreleri alan oluşturucuların bir `new` ifadesiyle veya bir [taban](../../language-reference/keywords/base.md) ifadesiyle çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="83152-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="83152-124">Sınıflar ve `structs` de birden çok Oluşturucu tanımlayabilir ve parametresiz bir Oluşturucu tanımlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="83152-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="83152-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="83152-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="83152-126">Bu sınıf aşağıdaki deyimlerden herhangi biri kullanılarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="83152-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="83152-127">Bir Oluşturucu, bir temel sınıfın yapıcısını çağırmak için `base` anahtar sözcüğünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="83152-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="83152-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="83152-129">Bu örnekte, Oluşturucu için blok yürütülmeden önce temel sınıfın Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="83152-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="83152-130">`base` anahtar sözcüğü parametresiz ya da olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="83152-131">Oluşturucuya yönelik tüm parametreler `base`parametre olarak veya bir ifadenin bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="83152-132">Daha fazla bilgi için bkz. [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="83152-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="83152-133">Türetilmiş bir sınıfta, bir temel sınıf oluşturucu açıkça `base` anahtar sözcüğü kullanılarak çağrılmamasından, varsa parametresiz Oluşturucu örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="83152-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="83152-134">Bu, aşağıdaki Oluşturucu bildirimlerinin etkili bir şekilde aynı olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="83152-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="83152-135">Bir temel sınıf parametresiz bir Oluşturucu sunmuyor ise, türetilmiş sınıf `base`kullanarak temel oluşturucuya açık bir çağrı vermelidir.</span><span class="sxs-lookup"><span data-stu-id="83152-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="83152-136">[Bu](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanarak bir Oluşturucu aynı nesnede başka bir Oluşturucu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="83152-137">`base`gibi, `this` parametresiz veya parametresiz olarak kullanılabilir ve kurucudaki herhangi bir parametre `this`parametre olarak veya bir ifadenin parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83152-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="83152-138">Örneğin, önceki örnekteki ikinci Oluşturucu `this`kullanılarak yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="83152-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="83152-139">Önceki örnekte `this` anahtar sözcüğünün kullanılması, bu oluşturucunun çağrılmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="83152-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="83152-140">Oluşturucular [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korunan](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="83152-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="83152-141">Bu erişim değiştiricileri, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğinize ilişkin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83152-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="83152-142">Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="83152-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="83152-143">Bir Oluşturucu [static](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="83152-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="83152-144">Statik oluşturucular, herhangi bir statik alana erişildikten hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83152-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="83152-145">Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="83152-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="83152-146">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="83152-146">C# Language Specification</span></span>  

<span data-ttu-id="83152-147">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) .</span><span class="sxs-lookup"><span data-stu-id="83152-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="83152-148">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="83152-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="83152-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83152-149">See also</span></span>

- [<span data-ttu-id="83152-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="83152-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="83152-151">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="83152-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="83152-152">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="83152-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="83152-153">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="83152-153">Finalizers</span></span>](./destructors.md)
