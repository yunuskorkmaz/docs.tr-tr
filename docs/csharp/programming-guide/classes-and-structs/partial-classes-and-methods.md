---
title: Kısmi sınıflar ve yöntemler-C# Programlama Kılavuzu
description: C# içindeki kısmi sınıflar ve Yöntemler, bir sınıfın tanımını, yapıyı, arabirimi veya iki ya da daha fazla kaynak dosya üzerinde bir yöntemi böler.
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: cfda3b89bfd9dc046274dfa53d62a0789d4d597e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899106"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="cd6fb-103">Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cd6fb-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="cd6fb-104">Bir [sınıfın](../../language-reference/keywords/class.md)tanımını, bir [yapıyı](../../language-reference/builtin-types/struct.md), [arabirimi](../../language-reference/keywords/interface.md) veya bir yöntemi iki veya daha fazla kaynak dosya üzerinde ayırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="cd6fb-105">Her kaynak dosya, tür veya yöntem tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçalar birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="cd6fb-106">Kısmi sınıflar</span><span class="sxs-lookup"><span data-stu-id="cd6fb-106">Partial Classes</span></span>

<span data-ttu-id="cd6fb-107">Bir sınıf tanımını bölmek istenen birkaç durum vardır:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="cd6fb-108">Büyük projeler üzerinde çalışırken, bir sınıfın ayrı dosyalar üzerinde yayılması, birden fazla programcıların aynı anda üzerinde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="cd6fb-109">Otomatik olarak oluşturulan kaynakla çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan kod sınıfa eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="cd6fb-110">Visual Studio, Windows Forms, Web hizmeti sarmalayıcı kodu vb. oluşturduğunda bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="cd6fb-111">Visual Studio tarafından oluşturulan dosyayı değiştirmek zorunda kalmadan, bu sınıfları kullanan kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="cd6fb-112">Bir sınıf tanımını ayırmak için, burada gösterildiği gibi [kısmi](../../language-reference/keywords/partial-type.md) anahtar sözcük değiştiricisini kullanın:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[EmployeeExample#1](snippets/partial-classes-and-methods/Program.cs#1)]

<span data-ttu-id="cd6fb-113">`partial`Anahtar sözcüğü, sınıf, yapı veya arabirimin diğer bölümlerinin ad alanında tanımlanamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="cd6fb-114">Tüm parçalar `partial` anahtar kelimesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="cd6fb-115">Son türü oluşturmak için tüm parçalar derleme zamanında kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="cd6fb-116">Tüm parçalar, ve gibi aynı erişilebilirliği içermelidir `public` `private` .</span><span class="sxs-lookup"><span data-stu-id="cd6fb-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="cd6fb-117">Herhangi bir bölüm soyut olarak bildirilirse, tüm tür soyut olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="cd6fb-118">Herhangi bir bölüm Sealed olarak bildirilirse, tüm tür Sealed olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="cd6fb-119">Herhangi bir parça bir temel tür bildiriyorsa, tüm tür o sınıfı devralır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="cd6fb-120">Bir temel sınıf belirten tüm parçalar kabul etmelidir, ancak temel bir sınıfı atlayan parçalar hala temel türü miras alır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="cd6fb-121">Parçalar farklı temel arabirimler belirtebilir ve son tür tüm kısmi bildirimlerin listelebileceği tüm arabirimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="cd6fb-122">Kısmi bir tanımda belirtilen herhangi bir sınıf, yapı veya arabirim üyesi diğer tüm parçalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="cd6fb-123">Son tür derleme zamanında tüm parçaların birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="cd6fb-124">`partial`Değiştirici, temsilci veya numaralandırma bildirimlerinde kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="cd6fb-125">Aşağıdaki örnek iç içe geçmiş türlerin kısmen, iç içe yerleştirilmiş olması durumunda bile kısmi bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[NestedPartialTypes#2](snippets/partial-classes-and-methods/Program.cs#2)]

<span data-ttu-id="cd6fb-126">Derleme zamanında, kısmi tür tanımlarının öznitelikleri birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="cd6fb-127">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-127">For example, consider the following declarations:</span></span>

[!code-csharp[PartialMoonDeclarations#3](snippets/partial-classes-and-methods/Program.cs#3)]

<span data-ttu-id="cd6fb-128">Bunlar aşağıdaki bildirimlerle eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleMoonDeclaration#4](snippets/partial-classes-and-methods/Program.cs#4)]

<span data-ttu-id="cd6fb-129">Aşağıdakiler tüm kısmi tür tanımlarından birleştirilir:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="cd6fb-130">XML açıklamaları</span><span class="sxs-lookup"><span data-stu-id="cd6fb-130">XML comments</span></span>

- <span data-ttu-id="cd6fb-131">arabirimler</span><span class="sxs-lookup"><span data-stu-id="cd6fb-131">interfaces</span></span>

- <span data-ttu-id="cd6fb-132">Genel tür parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="cd6fb-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="cd6fb-133">class öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="cd6fb-133">class attributes</span></span>

- <span data-ttu-id="cd6fb-134">üyeler</span><span class="sxs-lookup"><span data-stu-id="cd6fb-134">members</span></span>

<span data-ttu-id="cd6fb-135">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-135">For example, consider the following declarations:</span></span>

[!code-csharp[PartialEarthDeclarations#5](snippets/partial-classes-and-methods/Program.cs#5)]

<span data-ttu-id="cd6fb-136">Bunlar aşağıdaki bildirimlerle eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleEarthDeclaration#6](snippets/partial-classes-and-methods/Program.cs#6)]

### <a name="restrictions"></a><span data-ttu-id="cd6fb-137">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="cd6fb-137">Restrictions</span></span>

<span data-ttu-id="cd6fb-138">Kısmi sınıf tanımlarına çalışırken izlenecek birkaç kural vardır:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="cd6fb-139">Aynı türdeki parçalar olması amaçlanan tüm kısmi tür tanımlarının ile değiştirilmesi gerekir `partial` .</span><span class="sxs-lookup"><span data-stu-id="cd6fb-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="cd6fb-140">Örneğin, aşağıdaki sınıf bildirimleri bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[AllDefinitionsMustBePartials#7](snippets/partial-classes-and-methods/Program.cs#7)]

- <span data-ttu-id="cd6fb-141">`partial`Değiştirici yalnızca, veya anahtar sözcüklerinden hemen önce `class` görünebilir `struct` `interface` .</span><span class="sxs-lookup"><span data-stu-id="cd6fb-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="cd6fb-142">İç içe geçmiş kısmi türlere, aşağıdaki örnekte gösterildiği gibi kısmi tür tanımlarında izin verilir:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[NestedPartialTypes#8](snippets/partial-classes-and-methods/Program.cs#8)]

- <span data-ttu-id="cd6fb-143">Aynı türde parçalar olması gereken tüm kısmi tür tanımlarının aynı derlemede ve aynı modülde (. exe veya. dll dosyası) tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="cd6fb-144">Kısmi tanımlar birden çok modüle yayılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="cd6fb-145">Sınıf adı ve genel tür parametreleri tüm kısmi tür tanımlarında eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="cd6fb-146">Genel türler kısmi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-146">Generic types can be partial.</span></span> <span data-ttu-id="cd6fb-147">Her kısmi bildirimin aynı parametre adlarını aynı sırada kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="cd6fb-148">Kısmi tür tanımında aşağıdaki anahtar sözcükler isteğe bağlıdır, ancak bir kısmi tür tanımında varsa, aynı türde başka bir kısmi tanımda belirtilen anahtar sözcüklerle çakışamaz:</span><span class="sxs-lookup"><span data-stu-id="cd6fb-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="cd6fb-149">genel</span><span class="sxs-lookup"><span data-stu-id="cd6fb-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="cd6fb-150">özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cd6fb-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="cd6fb-151">protected</span><span class="sxs-lookup"><span data-stu-id="cd6fb-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="cd6fb-152">internal</span><span class="sxs-lookup"><span data-stu-id="cd6fb-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="cd6fb-153">Soyut</span><span class="sxs-lookup"><span data-stu-id="cd6fb-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="cd6fb-154">sealed</span><span class="sxs-lookup"><span data-stu-id="cd6fb-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="cd6fb-155">taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="cd6fb-155">base class</span></span>

  - <span data-ttu-id="cd6fb-156">[Yeni](../../language-reference/keywords/new-modifier.md) değiştirici (iç içe yerleştirilmiş parçalar)</span><span class="sxs-lookup"><span data-stu-id="cd6fb-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="cd6fb-157">genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="cd6fb-157">generic constraints</span></span>

<span data-ttu-id="cd6fb-158">Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fb-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="cd6fb-159">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="cd6fb-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="cd6fb-160">Description</span><span class="sxs-lookup"><span data-stu-id="cd6fb-160">Description</span></span>

<span data-ttu-id="cd6fb-161">Aşağıdaki örnekte, sınıfının alanları ve Oluşturucusu, `Coords` bir kısmi sınıf tanımında ve üyesi `PrintCoords` başka bir kısmi sınıf tanımında bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="cd6fb-162">Kod</span><span class="sxs-lookup"><span data-stu-id="cd6fb-162">Code</span></span>

[!code-csharp[CoordsExample#9](snippets/partial-classes-and-methods/Program.cs#9)]

## <a name="example-2"></a><span data-ttu-id="cd6fb-163">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="cd6fb-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="cd6fb-164">Description</span><span class="sxs-lookup"><span data-stu-id="cd6fb-164">Description</span></span>

<span data-ttu-id="cd6fb-165">Aşağıdaki örnek ayrıca kısmi yapılar ve arabirimler geliştirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="cd6fb-166">Kod</span><span class="sxs-lookup"><span data-stu-id="cd6fb-166">Code</span></span>

[!code-csharp[PartialStructsAndInterfaces#10](snippets/partial-classes-and-methods/Program.cs#10)]

## <a name="partial-methods"></a><span data-ttu-id="cd6fb-167">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd6fb-167">Partial Methods</span></span>

<span data-ttu-id="cd6fb-168">Kısmi bir sınıf veya yapı, kısmi bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="cd6fb-169">Sınıfın bir kısmı metodun imzasını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="cd6fb-170">İsteğe bağlı bir uygulama aynı bölümde veya başka bir bölümde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-170">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="cd6fb-171">Uygulama sağlanmazsa, yöntemi ve yöntemine yapılan tüm çağrılar derleme sırasında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="cd6fb-172">Kısmi Yöntemler, bir olaya benzer bir yöntemi tanımlamak için bir sınıfın bir parçasının Uygulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-172">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="cd6fb-173">Sınıfının diğer bölümünün uygulayıcısı, yöntemi uygulayıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-173">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="cd6fb-174">Yöntem uygulanmadığından, derleyici yöntem imzasını ve yönteme yapılan tüm çağrıları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-174">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="cd6fb-175">Çağrılardaki bağımsız değişkenlerin değerlendirmesinden kaynaklanan sonuçlar da dahil olmak üzere yöntemine yapılan çağrılar, çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-175">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="cd6fb-176">Bu nedenle, kısmi sınıftaki herhangi bir kod, uygulama sağlanmasa bile, kısmi bir yöntemi serbestçe kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-176">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="cd6fb-177">Yöntem çağrılırsa ancak uygulanmadığında, derleme zamanı veya çalışma zamanı hataları ortaya alınmaz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-177">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="cd6fb-178">Kısmi Yöntemler özellikle oluşturulan kodu özelleştirmenin bir yolu olarak faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-178">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="cd6fb-179">Bir yöntem adının ve imzasının ayrılmaya izin verir, böylece oluşturulan kod yöntemi çağırabilir, ancak geliştirici yöntemin uygulanıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-179">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="cd6fb-180">Kısmi sınıflara çok benzeyen kısmi Yöntemler, bir kod üreticisi tarafından oluşturulan kodu ve bir insan geliştiricisi tarafından oluşturulan kodu, çalışma zamanı maliyetleri olmadan birlikte çalışmak üzere etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-180">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="cd6fb-181">Kısmi yöntem bildirimi iki bölümden oluşur: tanım ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-181">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="cd6fb-182">Bunlar kısmi bir sınıfın ayrı bölümlerinde veya aynı bölümde olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-182">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="cd6fb-183">Uygulama bildirimi yoksa, derleyici hem tanımlama bildirimini hem de yönteme yapılan tüm çağrıları en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-183">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="cd6fb-184">Kısmi yöntem bildirimleri, bağlamsal anahtar sözcüğüyle [kısmen](../../language-reference/keywords/partial-type.md) başlamalı ve yöntemin [void](../../language-reference/builtin-types/void.md)döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-184">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="cd6fb-185">Kısmi yöntemlerin [içinde](../../language-reference/keywords/in-parameter-modifier.md) veya [ref](../../language-reference/keywords/ref.md) , ancak [Out](../../language-reference/keywords/out-parameter-modifier.md) parametreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-185">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="cd6fb-186">Kısmi Yöntemler örtük olarak [özeldir](../../language-reference/keywords/private.md)ve bu nedenle [sanal](../../language-reference/keywords/virtual.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-186">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="cd6fb-187">Gövde varlığı, tanımlama veya uygulama yapılıp yapılmayacağını belirlerse, kısmi Yöntemler [extern](../../language-reference/keywords/extern.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-187">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="cd6fb-188">Kısmi yöntemlerin [statik](../../language-reference/keywords/static.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-188">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="cd6fb-189">Kısmi yöntemler genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-189">Partial methods can be generic.</span></span> <span data-ttu-id="cd6fb-190">Kısıtlamalar, tanımlayıcı kısmi Yöntem bildirimine konur ve isteğe bağlı olarak uygulama bir tane üzerinde yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-190">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="cd6fb-191">Parametre ve tür parametre adları, uygulama bildiriminde, tanımlanmasıyla aynı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-191">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="cd6fb-192">Tanımlanmış ve uygulanmış, ancak yalnızca tanımlanmış kısmi bir yönteme değil kısmi bir yönteme [temsilci](../../language-reference/builtin-types/reference-types.md) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-192">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cd6fb-193">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="cd6fb-193">C# Language Specification</span></span>

<span data-ttu-id="cd6fb-194">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [kısmi türler](~/_csharplang/spec/classes.md#partial-types) .</span><span class="sxs-lookup"><span data-stu-id="cd6fb-194">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="cd6fb-195">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-195">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd6fb-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd6fb-196">See also</span></span>

- [<span data-ttu-id="cd6fb-197">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cd6fb-197">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd6fb-198">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="cd6fb-198">Classes</span></span>](./classes.md)
- [<span data-ttu-id="cd6fb-199">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="cd6fb-199">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="cd6fb-200">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="cd6fb-200">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="cd6fb-201">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="cd6fb-201">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
