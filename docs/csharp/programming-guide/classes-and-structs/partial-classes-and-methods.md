---
title: Kısmi sınıflar ve yöntemler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 641c2e3adfb3dabaa300e94b203aa6c4c4b509d2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628195"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="a672b-102">Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a672b-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="a672b-103">Bir [sınıfın](../../language-reference/keywords/class.md)tanımını, bir [yapıyı](../../language-reference/builtin-types/struct.md), [arabirimi](../../language-reference/keywords/interface.md) veya bir yöntemi iki veya daha fazla kaynak dosya üzerinde ayırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a672b-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="a672b-104">Her kaynak dosya, tür veya yöntem tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçalar birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="a672b-105">Kısmi sınıflar</span><span class="sxs-lookup"><span data-stu-id="a672b-105">Partial Classes</span></span>

<span data-ttu-id="a672b-106">Bir sınıf tanımını bölmek istenen birkaç durum vardır:</span><span class="sxs-lookup"><span data-stu-id="a672b-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="a672b-107">Büyük projeler üzerinde çalışırken, bir sınıfın ayrı dosyalar üzerinde yayılması, birden fazla programcıların aynı anda üzerinde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a672b-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="a672b-108">Otomatik olarak oluşturulan kaynakla çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan kod sınıfa eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="a672b-109">Visual Studio, Windows Forms, Web hizmeti sarmalayıcı kodu vb. oluşturduğunda bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a672b-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="a672b-110">Visual Studio tarafından oluşturulan dosyayı değiştirmek zorunda kalmadan, bu sınıfları kullanan kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a672b-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="a672b-111">Bir sınıf tanımını ayırmak için, burada gösterildiği gibi [kısmi](../../language-reference/keywords/partial-type.md) anahtar sözcük değiştiricisini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a672b-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="a672b-112">`partial` anahtar sözcüğü, sınıfın, yapının veya arabirimin diğer bölümlerinin ad alanında tanımlanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a672b-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="a672b-113">Tüm parçaların `partial` anahtar sözcüğünü kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a672b-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="a672b-114">Son türü oluşturmak için tüm parçalar derleme zamanında kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a672b-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="a672b-115">Tüm parçalar `public`, `private`vb. gibi aynı erişilebilirliği içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a672b-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="a672b-116">Herhangi bir bölüm soyut olarak bildirilirse, tüm tür soyut olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="a672b-117">Herhangi bir bölüm Sealed olarak bildirilirse, tüm tür Sealed olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="a672b-118">Herhangi bir parça bir temel tür bildiriyorsa, tüm tür o sınıfı devralır.</span><span class="sxs-lookup"><span data-stu-id="a672b-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="a672b-119">Bir temel sınıf belirten tüm parçalar kabul etmelidir, ancak temel bir sınıfı atlayan parçalar hala temel türü miras alır.</span><span class="sxs-lookup"><span data-stu-id="a672b-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="a672b-120">Parçalar farklı temel arabirimler belirtebilir ve son tür tüm kısmi bildirimlerin listelebileceği tüm arabirimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="a672b-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="a672b-121">Kısmi bir tanımda belirtilen herhangi bir sınıf, yapı veya arabirim üyesi diğer tüm parçalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="a672b-122">Son tür derleme zamanında tüm parçaların birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="a672b-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="a672b-123">`partial` değiştiricisi temsilci veya numaralandırma bildirimlerinde kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a672b-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="a672b-124">Aşağıdaki örnek iç içe geçmiş türlerin kısmen, iç içe yerleştirilmiş olması durumunda bile kısmi bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a672b-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="a672b-125">Derleme zamanında, kısmi tür tanımlarının öznitelikleri birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="a672b-126">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a672b-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="a672b-127">Bunlar aşağıdaki bildirimlerle eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="a672b-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="a672b-128">Aşağıdakiler tüm kısmi tür tanımlarından birleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a672b-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="a672b-129">XML açıklamaları</span><span class="sxs-lookup"><span data-stu-id="a672b-129">XML comments</span></span>

- <span data-ttu-id="a672b-130">arabirimler</span><span class="sxs-lookup"><span data-stu-id="a672b-130">interfaces</span></span>

- <span data-ttu-id="a672b-131">Genel tür parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="a672b-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="a672b-132">class öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="a672b-132">class attributes</span></span>

- <span data-ttu-id="a672b-133">üyeler</span><span class="sxs-lookup"><span data-stu-id="a672b-133">members</span></span>

<span data-ttu-id="a672b-134">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a672b-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="a672b-135">Bunlar aşağıdaki bildirimlerle eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="a672b-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="a672b-136">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="a672b-136">Restrictions</span></span>

<span data-ttu-id="a672b-137">Kısmi sınıf tanımlarına çalışırken izlenecek birkaç kural vardır:</span><span class="sxs-lookup"><span data-stu-id="a672b-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="a672b-138">Aynı türdeki parçalar olması amaçlanan tüm kısmi tür tanımlarının `partial`ile değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a672b-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="a672b-139">Örneğin, aşağıdaki sınıf bildirimleri bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a672b-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="a672b-140">`partial` değiştirici yalnızca, `class`, `struct`veya `interface`anahtar kelimeleriyle hemen önce yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="a672b-141">İç içe geçmiş kısmi türlere, aşağıdaki örnekte gösterildiği gibi kısmi tür tanımlarında izin verilir:</span><span class="sxs-lookup"><span data-stu-id="a672b-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="a672b-142">Aynı türde parçalar olması gereken tüm kısmi tür tanımlarının aynı derlemede ve aynı modülde (. exe veya. dll dosyası) tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a672b-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="a672b-143">Kısmi tanımlar birden çok modüle yayılamaz.</span><span class="sxs-lookup"><span data-stu-id="a672b-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="a672b-144">Sınıf adı ve genel tür parametreleri tüm kısmi tür tanımlarında eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a672b-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="a672b-145">Genel türler kısmi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-145">Generic types can be partial.</span></span> <span data-ttu-id="a672b-146">Her kısmi bildirimin aynı parametre adlarını aynı sırada kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a672b-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="a672b-147">Kısmi tür tanımında aşağıdaki anahtar sözcükler isteğe bağlıdır, ancak bir kısmi tür tanımında varsa, aynı türde başka bir kısmi tanımda belirtilen anahtar sözcüklerle çakışamaz:</span><span class="sxs-lookup"><span data-stu-id="a672b-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="a672b-148">public</span><span class="sxs-lookup"><span data-stu-id="a672b-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="a672b-149">private</span><span class="sxs-lookup"><span data-stu-id="a672b-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="a672b-150">protected</span><span class="sxs-lookup"><span data-stu-id="a672b-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="a672b-151">internal</span><span class="sxs-lookup"><span data-stu-id="a672b-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="a672b-152">abstract</span><span class="sxs-lookup"><span data-stu-id="a672b-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="a672b-153">sealed</span><span class="sxs-lookup"><span data-stu-id="a672b-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="a672b-154">taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="a672b-154">base class</span></span>

  - <span data-ttu-id="a672b-155">[Yeni](../../language-reference/keywords/new-modifier.md) değiştirici (iç içe yerleştirilmiş parçalar)</span><span class="sxs-lookup"><span data-stu-id="a672b-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="a672b-156">genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="a672b-156">generic constraints</span></span>

<span data-ttu-id="a672b-157">Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a672b-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="a672b-158">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a672b-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="a672b-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a672b-159">Description</span></span>

<span data-ttu-id="a672b-160">Aşağıdaki örnekte, `Coords`sınıfının alanları ve Oluşturucusu tek bir kısmi sınıf tanımında ve `PrintCoords`üyesi başka bir kısmi sınıf tanımında bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a672b-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="a672b-161">Kod</span><span class="sxs-lookup"><span data-stu-id="a672b-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="a672b-162">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a672b-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="a672b-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a672b-163">Description</span></span>

<span data-ttu-id="a672b-164">Aşağıdaki örnek ayrıca kısmi yapılar ve arabirimler geliştirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a672b-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="a672b-165">Kod</span><span class="sxs-lookup"><span data-stu-id="a672b-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="a672b-166">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a672b-166">Partial Methods</span></span>

<span data-ttu-id="a672b-167">Kısmi bir sınıf veya yapı, kısmi bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="a672b-168">Sınıfın bir kısmı metodun imzasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a672b-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="a672b-169">İsteğe bağlı bir uygulama aynı bölümde veya başka bir bölümde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="a672b-170">Uygulama sağlanmazsa, yöntemi ve yöntemine yapılan tüm çağrılar derleme sırasında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="a672b-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="a672b-171">Kısmi Yöntemler, bir olaya benzer bir yöntemi tanımlamak için bir sınıfın bir parçasının Uygulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a672b-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="a672b-172">Sınıfının diğer bölümünün uygulayıcısı, yöntemi uygulayıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="a672b-173">Yöntem uygulanmadığından, derleyici yöntem imzasını ve yönteme yapılan tüm çağrıları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a672b-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="a672b-174">Çağrılardaki bağımsız değişkenlerin değerlendirmesinden kaynaklanan sonuçlar da dahil olmak üzere yöntemine yapılan çağrılar, çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a672b-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="a672b-175">Bu nedenle, kısmi sınıftaki herhangi bir kod, uygulama sağlanmasa bile, kısmi bir yöntemi serbestçe kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="a672b-176">Yöntem çağrılırsa ancak uygulanmadığında, derleme zamanı veya çalışma zamanı hataları ortaya alınmaz.</span><span class="sxs-lookup"><span data-stu-id="a672b-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="a672b-177">Kısmi Yöntemler özellikle oluşturulan kodu özelleştirmenin bir yolu olarak faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a672b-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="a672b-178">Bir yöntem adının ve imzasının ayrılmaya izin verir, böylece oluşturulan kod yöntemi çağırabilir, ancak geliştirici yöntemin uygulanıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="a672b-179">Kısmi sınıflara çok benzeyen kısmi Yöntemler, bir kod üreticisi tarafından oluşturulan kodu ve bir insan geliştiricisi tarafından oluşturulan kodu, çalışma zamanı maliyetleri olmadan birlikte çalışmak üzere etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a672b-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="a672b-180">Kısmi yöntem bildirimi iki bölümden oluşur: tanım ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="a672b-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="a672b-181">Bunlar kısmi bir sınıfın ayrı bölümlerinde veya aynı bölümde olabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="a672b-182">Uygulama bildirimi yoksa, derleyici hem tanımlama bildirimini hem de yönteme yapılan tüm çağrıları en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="a672b-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="a672b-183">Kısmi yöntem bildirimleri, bağlamsal anahtar sözcüğüyle [kısmen](../../language-reference/keywords/partial-type.md) başlamalı ve yöntemin [void](../../language-reference/builtin-types/void.md)döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a672b-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="a672b-184">Kısmi yöntemlerin [içinde](../../language-reference/keywords/in-parameter-modifier.md) veya [ref](../../language-reference/keywords/ref.md) , ancak [Out](../../language-reference/keywords/out-parameter-modifier.md) parametreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="a672b-185">Kısmi Yöntemler örtük olarak [özeldir](../../language-reference/keywords/private.md)ve bu nedenle [sanal](../../language-reference/keywords/virtual.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="a672b-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="a672b-186">Gövde varlığı, tanımlama veya uygulama yapılıp yapılmayacağını belirlerse, kısmi Yöntemler [extern](../../language-reference/keywords/extern.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="a672b-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="a672b-187">Kısmi yöntemlerin [statik](../../language-reference/keywords/static.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler olabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="a672b-188">Kısmi yöntemler genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-188">Partial methods can be generic.</span></span> <span data-ttu-id="a672b-189">Kısıtlamalar, tanımlayıcı kısmi Yöntem bildirimine konur ve isteğe bağlı olarak uygulama bir tane üzerinde yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="a672b-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="a672b-190">Parametre ve tür parametre adları, uygulama bildiriminde, tanımlanmasıyla aynı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="a672b-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="a672b-191">Tanımlanmış ve uygulanmış, ancak yalnızca tanımlanmış kısmi bir yönteme değil kısmi bir yönteme [temsilci](../../language-reference/builtin-types/reference-types.md) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a672b-191">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a672b-192">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a672b-192">C# Language Specification</span></span>

<span data-ttu-id="a672b-193">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [kısmi türler](~/_csharplang/spec/classes.md#partial-types) .</span><span class="sxs-lookup"><span data-stu-id="a672b-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a672b-194">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="a672b-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a672b-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a672b-195">See also</span></span>

- [<span data-ttu-id="a672b-196">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a672b-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a672b-197">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="a672b-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="a672b-198">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a672b-198">Structs</span></span>](./structs.md)
- [<span data-ttu-id="a672b-199">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a672b-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="a672b-200">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="a672b-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
