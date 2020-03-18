---
title: Kısmi Sınıflar ve Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399821"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="211aa-102">Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="211aa-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="211aa-103">Bir [sınıfın](../../language-reference/keywords/class.md)tanımını, bir [yapıyı,](../../language-reference/builtin-types/struct.md) [arabirimi](../../language-reference/keywords/interface.md) veya yöntemi iki veya daha fazla kaynak dosya üzerinde bölmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="211aa-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="211aa-104">Her kaynak dosya tür veya yöntem tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçalar birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="211aa-105">Kısmi Sınıflar</span><span class="sxs-lookup"><span data-stu-id="211aa-105">Partial Classes</span></span>

<span data-ttu-id="211aa-106">Sınıf tanımının bölünmesi nin arzu edilen birkaç durum vardır:</span><span class="sxs-lookup"><span data-stu-id="211aa-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="211aa-107">Büyük projeler üzerinde çalışırken, bir sınıfı ayrı dosyalara yaymak, birden çok programcının aynı anda üzerinde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="211aa-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="211aa-108">Otomatik olarak oluşturulan kaynakla çalışırken, kod kaynak dosyasını yeniden oluşturmak zorunda kalmadan sınıfa eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="211aa-109">Visual Studio, Windows Formları, Web hizmeti paketleyici kodu ve benzeri oluştururken bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="211aa-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="211aa-110">Visual Studio tarafından oluşturulan dosyayı değiştirmek zorunda kalmadan bu sınıfları kullanan kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="211aa-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="211aa-111">Bir sınıf tanımını bölmek için, burada gösterildiği gibi [kısmi](../../language-reference/keywords/partial-type.md) anahtar kelime değiştiricisini kullanın:</span><span class="sxs-lookup"><span data-stu-id="211aa-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="211aa-112">Anahtar `partial` kelime, sınıfın diğer bölümlerinin, yapının veya arabirimin ad alanında tanımlanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="211aa-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="211aa-113">Tüm parçalar anahtar `partial` kelimeyi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="211aa-114">Tüm parçalar, son türü oluşturmak için derleme zamanında kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="211aa-115">Tüm parçalar , , `public` `private`ve benzeri gibi aynı erişilebilirlik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="211aa-116">Herhangi bir bölüm soyut olarak ilan edilirse, o zaman tüm tür soyut olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="211aa-117">Herhangi bir parça mühürlü olarak ilan edilirse, o zaman tüm türü mühürlü olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="211aa-118">Herhangi bir bölüm bir taban türü bildirirse, tüm tür o sınıfı devralır.</span><span class="sxs-lookup"><span data-stu-id="211aa-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="211aa-119">Taban sınıf belirten tüm bölümler kabul edilmelidir, ancak taban sınıfı atlayan parçalar yine de taban türü devralır.</span><span class="sxs-lookup"><span data-stu-id="211aa-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="211aa-120">Parçalar farklı temel arabirimleri belirtebilir ve son tür tüm kısmi bildirimleri tarafından listelenen tüm arabirimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="211aa-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="211aa-121">Kısmi tanımda bildirilen herhangi bir sınıf, yapı veya arayüz üyesi diğer tüm bölümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="211aa-122">Son tür derleme zamanında tüm parçaların kombinasyonudur.</span><span class="sxs-lookup"><span data-stu-id="211aa-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="211aa-123">`partial` Değiştirici temsilci veya numaralandırma beyannamelerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="211aa-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="211aa-124">Aşağıdaki örnek, iç içe geçtikleri tür kısmi olmasa bile, iç içe geçme türlerinin kısmi olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="211aa-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="211aa-125">Derleme zamanında, kısmi tür tanımlarının öznitelikleri birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="211aa-126">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="211aa-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="211aa-127">Bunlar aşağıdaki beyanlara eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="211aa-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="211aa-128">Aşağıdakitüm kısmi tür tanımlarından birleştirilir:</span><span class="sxs-lookup"><span data-stu-id="211aa-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="211aa-129">XML açıklamaları</span><span class="sxs-lookup"><span data-stu-id="211aa-129">XML comments</span></span>

- <span data-ttu-id="211aa-130">arabirimler</span><span class="sxs-lookup"><span data-stu-id="211aa-130">interfaces</span></span>

- <span data-ttu-id="211aa-131">genel tür parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="211aa-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="211aa-132">class öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="211aa-132">class attributes</span></span>

- <span data-ttu-id="211aa-133">üyeler</span><span class="sxs-lookup"><span data-stu-id="211aa-133">members</span></span>

<span data-ttu-id="211aa-134">Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="211aa-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="211aa-135">Bunlar aşağıdaki beyanlara eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="211aa-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="211aa-136">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="211aa-136">Restrictions</span></span>

<span data-ttu-id="211aa-137">Kısmi sınıf tanımlarıyla çalışırken uymanız gereken birkaç kural vardır:</span><span class="sxs-lookup"><span data-stu-id="211aa-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="211aa-138">Aynı türdeki parçalar olması amaçlandığı tüm kısmi tür `partial`tanımları ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="211aa-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="211aa-139">Örneğin, aşağıdaki sınıf bildirimleri bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="211aa-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="211aa-140">`partial` Değiştirici yalnızca anahtar kelimelerden `class`hemen `struct`önce `interface`görünebilir, veya .</span><span class="sxs-lookup"><span data-stu-id="211aa-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="211aa-141">İç içe gelen kısmi türler, aşağıdaki örnekte gösterildiği gibi kısmi tür tanımlarında izin verilir:</span><span class="sxs-lookup"><span data-stu-id="211aa-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="211aa-142">Aynı türde parçalar olması gereken tüm kısmi tür tanımları aynı montaj ve aynı modül (.exe veya .dll dosyası) tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="211aa-143">Kısmi tanımlar birden çok modülü kaplayamaz.</span><span class="sxs-lookup"><span data-stu-id="211aa-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="211aa-144">Sınıf adı ve genel tür parametreleri tüm kısmi tür tanımlarında eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="211aa-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="211aa-145">Genel türleri kısmi olabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-145">Generic types can be partial.</span></span> <span data-ttu-id="211aa-146">Her kısmi bildirim aynı sırada aynı parametre adlarını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="211aa-147">Kısmi tür tanımında aşağıdaki anahtar kelimeler isteğe bağlıdır, ancak bir kısmi tür tanımında mevcutsa, aynı tür için başka bir kısmi tanımda belirtilen anahtar kelimelerle çakışamaz:</span><span class="sxs-lookup"><span data-stu-id="211aa-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="211aa-148">Kamu</span><span class="sxs-lookup"><span data-stu-id="211aa-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="211aa-149">Özel</span><span class="sxs-lookup"><span data-stu-id="211aa-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="211aa-150">protected</span><span class="sxs-lookup"><span data-stu-id="211aa-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="211aa-151">Iç</span><span class="sxs-lookup"><span data-stu-id="211aa-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="211aa-152">Soyut</span><span class="sxs-lookup"><span data-stu-id="211aa-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="211aa-153">sealed</span><span class="sxs-lookup"><span data-stu-id="211aa-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="211aa-154">taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="211aa-154">base class</span></span>

  - <span data-ttu-id="211aa-155">[yeni](../../language-reference/keywords/new-modifier.md) değiştirici (iç içe parçalar)</span><span class="sxs-lookup"><span data-stu-id="211aa-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="211aa-156">genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="211aa-156">generic constraints</span></span>

<span data-ttu-id="211aa-157">Daha fazla bilgi [için, Tür Parametreleri üzerindeki Kısıtlamalar'a](../generics/constraints-on-type-parameters.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="211aa-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="211aa-158">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="211aa-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="211aa-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="211aa-159">Description</span></span>

<span data-ttu-id="211aa-160">Aşağıdaki örnekte, alanların ve sınıfın oluşturucusu, `Coords`bir kısmi sınıf tanımında beyan `PrintCoords`edilir ve üye, başka bir kısmi sınıf tanımında bildirilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="211aa-161">Kod</span><span class="sxs-lookup"><span data-stu-id="211aa-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="211aa-162">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="211aa-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="211aa-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="211aa-163">Description</span></span>

<span data-ttu-id="211aa-164">Aşağıdaki örnek, kısmi yapı ve arabirimler de geliştirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="211aa-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="211aa-165">Kod</span><span class="sxs-lookup"><span data-stu-id="211aa-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="211aa-166">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="211aa-166">Partial Methods</span></span>

<span data-ttu-id="211aa-167">Kısmi bir sınıf veya yapı kısmi bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="211aa-168">Sınıfın bir bölümü yöntemin imzasını içerir.</span><span class="sxs-lookup"><span data-stu-id="211aa-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="211aa-169">İsteğe bağlı bir uygulama aynı parçada veya başka bir bölümde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="211aa-170">Uygulama sağlanmıyorsa, yöntem ve yönteme yapılan tüm çağrılar derleme zamanında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="211aa-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="211aa-171">Kısmi yöntemler, bir sınıfın bir bölümünün uygulayıcısının bir olaya benzer bir yöntem tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="211aa-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="211aa-172">Sınıfın diğer bölümünün uygulayıcısı yöntemi uygulayıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="211aa-173">Yöntem uygulanmazsa, derleyici yöntem imzasını ve yönteme yapılan tüm çağrıları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="211aa-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="211aa-174">Çağrılardaki bağımsız değişkenlerin değerlendirilmesinden kaynaklanan sonuçlar da dahil olmak üzere yönteme yapılan çağrıların çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="211aa-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="211aa-175">Bu nedenle, kısmi sınıftaki herhangi bir kod, uygulama sağlanmasa bile kısmi bir yöntemi serbestçe kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="211aa-176">Yöntem çağrıldıysa ancak uygulanmazsa derleme zamanı veya çalışma zamanı hataları olmaz.</span><span class="sxs-lookup"><span data-stu-id="211aa-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="211aa-177">Kısmi yöntemler, özellikle oluşturulan kodu özelleştirmenin bir yolu olarak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="211aa-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="211aa-178">Oluşturulan kodun yöntemi çağırabilmesi için bir yöntem adı ve imzasının ayrılmasına izin verirler, ancak geliştirici yöntemi uygulayıp uygulamamaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="211aa-179">Kısmi sınıflar gibi, kısmi yöntemler de bir kod oluşturucusu tarafından oluşturulan kodu ve insan geliştirici tarafından oluşturulan kodun çalışma süresi maliyetleri olmadan birlikte çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="211aa-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="211aa-180">Kısmi yöntem bildirimi iki bölümden oluşur: tanım ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="211aa-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="211aa-181">Bunlar kısmi sınıfın ayrı bölümlerinde veya aynı bölümde olabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="211aa-182">Uygulama bildirimi yoksa, derleyici hem tanımlayıcı bildirimi hem de yönteme yapılan tüm çağrıları en iyi duruma getirerek uzaklara gider.</span><span class="sxs-lookup"><span data-stu-id="211aa-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="211aa-183">Kısmi yöntem bildirimleri bağlamsal anahtar kelime [kısmi](../../language-reference/keywords/partial-type.md) ile başlamalı ve yöntem [geçersiz](../../language-reference/builtin-types/void.md)dönmelidir.</span><span class="sxs-lookup"><span data-stu-id="211aa-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="211aa-184">Kısmi yöntemler [olabilir](../../language-reference/keywords/in-parameter-modifier.md) veya [ref](../../language-reference/keywords/ref.md) ama [parametreleri dışarı](../../language-reference/keywords/out-parameter-modifier.md) değil.</span><span class="sxs-lookup"><span data-stu-id="211aa-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="211aa-185">Kısmi yöntemler örtülü olarak [özeldir](../../language-reference/keywords/private.md)ve bu nedenle [sanal](../../language-reference/keywords/virtual.md)olamazlar.</span><span class="sxs-lookup"><span data-stu-id="211aa-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="211aa-186">Kısmi yöntemler [extern](../../language-reference/keywords/extern.md)olamaz , çünkü vücudun varlığı onlar tanımlayan veya uygulayan olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="211aa-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="211aa-187">Kısmi [yöntemlerstatik](../../language-reference/keywords/static.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiriciler olabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="211aa-188">Kısmi yöntemler genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-188">Partial methods can be generic.</span></span> <span data-ttu-id="211aa-189">Kısıtlamalar tanımlayıcı kısmi yöntem bildirimine konur ve isteğe bağlı olarak uygulama bildiriminde yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="211aa-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="211aa-190">Parametre ve tür parametresi adları, uygulama bildiriminde tanımlayıcı dakiyle aynı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="211aa-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="211aa-191">Tanımlanmış ve uygulanmış kısmi bir yönteme [temsilci](../../language-reference/builtin-types/reference-types.md) atayabilirsiniz, ancak yalnızca tanımlanmış kısmi bir yönteme temsilci yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="211aa-191">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="211aa-192">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="211aa-192">C# Language Specification</span></span>

<span data-ttu-id="211aa-193">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Kısmi türleri](~/_csharplang/spec/classes.md#partial-types) görün.</span><span class="sxs-lookup"><span data-stu-id="211aa-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="211aa-194">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="211aa-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="211aa-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="211aa-195">See also</span></span>

- [<span data-ttu-id="211aa-196">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="211aa-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="211aa-197">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="211aa-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="211aa-198">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="211aa-198">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="211aa-199">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="211aa-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="211aa-200">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="211aa-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
