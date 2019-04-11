---
title: Kısmi sınıflar ve yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 0d54101badab297457e8d8ecf277898fc6908779
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481061"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="3b7cc-102">Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3b7cc-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="3b7cc-103">Tanımı bölmek mümkündür bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapı](../../../csharp/language-reference/keywords/struct.md)e [arabirimi](../../../csharp/language-reference/keywords/interface.md) ya da iki veya daha fazla kaynak dosyalar üzerinde bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="3b7cc-104">Her kaynak dosyası türü veya yönteminde tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçaları bir araya getirilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="3b7cc-105">Kısmi sınıflar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-105">Partial Classes</span></span>

<span data-ttu-id="3b7cc-106">Bir sınıf tanımı bölmeyi tercih edilir, birkaç durum vardır:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="3b7cc-107">Büyük projeler üzerinde çalışırken, bir sınıf ayrı dosyalar yayılmasını üzerinde aynı anda çalışmak birden çok programcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="3b7cc-108">Otomatik olarak oluşturulan kaynak ile çalışırken kod sınıfa kaynak dosyası yeniden oluşturmak zorunda kalmadan eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="3b7cc-109">Visual Studio, Windows Forms, Web hizmeti sarmalayıcı kodu ve benzeri oluşturduğunda, bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="3b7cc-110">Bu sınıflar, Visual Studio tarafından oluşturulan dosya değiştirmek zorunda kalmadan kullanan kodu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="3b7cc-111">Bir sınıf tanımı bölmek için kullanın [kısmi](../../../csharp/language-reference/keywords/partial-type.md) burada gösterildiği gibi anahtar sözcüğü değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="3b7cc-112">`partial` Anahtar sözcüğü, sınıf, yapı, diğer bölümlerini gösterir veya arabirimi ad alanı içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="3b7cc-113">Tüm parçaları kullanmalısınız `partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="3b7cc-114">Tüm parçaları kullanılabilir son türü oluşturmak için zaman derleyin.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="3b7cc-115">Tüm parçaları gibi aynı erişilebilirliği olmalıdır `public`, `private`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="3b7cc-116">Herhangi bir bölümü soyut olarak bildirilirse, tüm türü soyut olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="3b7cc-117">Tüm tür korumalı olarak kabul edilip sonra herhangi bir bölümü sealed bildirilmişse.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="3b7cc-118">Herhangi bir bölümü bir taban türü bildirirse, tüm tür o sınıf devralır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="3b7cc-119">Bir taban sınıfı belirtin tüm bölümleri kabul etmeniz gerekir, ancak bir temel sınıf atlayın parçaları temel tür hala devralır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="3b7cc-120">Son türü kısmi bildirimleri listelenen tüm arabirimlerini uygular ve bölümleri farklı temel arabirimleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="3b7cc-121">Herhangi bir sınıf, yapı veya arabirim üyeleri bir kısmi tanımda'olarak bildirilen tüm diğer bölümleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="3b7cc-122">Tüm parçaları birleşimi derleme zamanında son türüdür.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="3b7cc-123">`partial` Değiştiricisi, temsilci veya sabit listesi bildirimlerinde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="3b7cc-124">Aşağıdaki örnek, içinde iç içe türü kısmi olmasa bile, iç içe geçmiş türler kendisini kısmi, olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="3b7cc-125">Derleme zamanında öznitelikleri kısmi türü tanımları birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="3b7cc-126">Örneğin, aşağıdaki bildirimleri dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="3b7cc-127">Bunlar, aşağıdaki bildirimi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="3b7cc-128">Aşağıdaki tüm kısmi türü tanımları birleştirilir:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="3b7cc-129">XML açıklamaları</span><span class="sxs-lookup"><span data-stu-id="3b7cc-129">XML comments</span></span>

- <span data-ttu-id="3b7cc-130">arabirimler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-130">interfaces</span></span>

- <span data-ttu-id="3b7cc-131">genel tür parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="3b7cc-132">class öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-132">class attributes</span></span>

- <span data-ttu-id="3b7cc-133">üyeler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-133">members</span></span>

<span data-ttu-id="3b7cc-134">Örneğin, aşağıdaki bildirimleri dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="3b7cc-135">Bunlar, aşağıdaki bildirimi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="3b7cc-136">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-136">Restrictions</span></span>

<span data-ttu-id="3b7cc-137">Kısmi sınıf tanımları ile çalışırken yordamları izlemek için çeşitli kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="3b7cc-138">Bölümleri aynı türde olacak şekilde tasarlanmış tüm kısmi tür tanımları ile değiştirilmelidir `partial`.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="3b7cc-139">Örneğin, aşağıdaki sınıf bildirimleri hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="3b7cc-140">`partial` Değiştiricisi hemen önce anahtar sözcükler yalnızca görüntülenebilir `class`, `struct`, veya `interface`.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="3b7cc-141">Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş kısmi türler kısmi türü tanımlarında izin verilir:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="3b7cc-142">Tüm kısmi tür tanımlarını bölümleri aynı türde olacak şekilde tasarlanmış, aynı derleme ve aynı modülde (.exe veya .dll dosyası) tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="3b7cc-143">Kısmi tanımlar, birden çok modül yayılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="3b7cc-144">Tüm kısmi tür tanımları, genel tür parametreleri ve sınıf adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="3b7cc-145">Genel türler, kısmi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-145">Generic types can be partial.</span></span> <span data-ttu-id="3b7cc-146">Her bir kısmi bildirimi aynı sırada aynı parametre adları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="3b7cc-147">Aşağıdaki anahtar sözcükler kısmi tür tanımında isteğe bağlıdır, ancak bir kısmi tür tanımı varsa, aynı türde başka bir kısmi tanımında belirtilen anahtar sözcüklerle çakışmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="3b7cc-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="3b7cc-148">public</span><span class="sxs-lookup"><span data-stu-id="3b7cc-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)

  - [<span data-ttu-id="3b7cc-149">private</span><span class="sxs-lookup"><span data-stu-id="3b7cc-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)

  - [<span data-ttu-id="3b7cc-150">protected</span><span class="sxs-lookup"><span data-stu-id="3b7cc-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)

  - [<span data-ttu-id="3b7cc-151">internal</span><span class="sxs-lookup"><span data-stu-id="3b7cc-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

  - [<span data-ttu-id="3b7cc-152">abstract</span><span class="sxs-lookup"><span data-stu-id="3b7cc-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)

  - [<span data-ttu-id="3b7cc-153">korumalı</span><span class="sxs-lookup"><span data-stu-id="3b7cc-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)

  - <span data-ttu-id="3b7cc-154">taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="3b7cc-154">base class</span></span>

  - <span data-ttu-id="3b7cc-155">[Yeni](../../../csharp/language-reference/keywords/new.md) değiştirici (iç içe geçmiş parça)</span><span class="sxs-lookup"><span data-stu-id="3b7cc-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="3b7cc-156">Genel sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-156">generic constraints</span></span>

<span data-ttu-id="3b7cc-157">Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3b7cc-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="3b7cc-158">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="3b7cc-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="3b7cc-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b7cc-159">Description</span></span>

<span data-ttu-id="3b7cc-160">Aşağıdaki örnek, alanları ve sınıf oluşturucusunun `Coords`, bir kısmi sınıf tanımı ve üye bildirilir `PrintCoords`, başka bir kısmi sınıf tanımında bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="3b7cc-161">Kod</span><span class="sxs-lookup"><span data-stu-id="3b7cc-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="3b7cc-162">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="3b7cc-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="3b7cc-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b7cc-163">Description</span></span>

<span data-ttu-id="3b7cc-164">Aşağıdaki örnek, ayrıca kısmi yapılar ve arabirimler geliştirebilirsiniz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="3b7cc-165">Kod</span><span class="sxs-lookup"><span data-stu-id="3b7cc-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="3b7cc-166">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-166">Partial Methods</span></span>

<span data-ttu-id="3b7cc-167">Kısmi bir yöntemin kısmi bir sınıf veya yapı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="3b7cc-168">Bir sınıfın parçası yöntem imzası içerir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="3b7cc-169">İsteğe bağlı bir uygulama aynı bölüm veya başka bir parçası tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="3b7cc-170">Uygulama sağlanmazsa, derleme zamanında yöntemi ve yöntemine yönelik tüm çağrılar kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="3b7cc-171">Kısmi yöntemler, bir olay için benzer bir yöntemi tanımlamak bir parçası olan bir sınıf uygulayan etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="3b7cc-172">Uygulayan bir sınıfın parçası, yöntemi veya uygulamamaya karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="3b7cc-173">Yöntem uygulanmadı sonra derleyici yöntemi kaldırır imzası ve yöntemine yapılan tüm çağrıları.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="3b7cc-174">Değerlendirme çağrılarındaki bağımsız değişkenler, ortaya çıkabilecek tüm sonuçları dahil olmak üzere, yöntem çağrıları çalışma zamanında bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="3b7cc-175">Bu nedenle, uygulama sağlanmazsa olsa bile kısmi sınıftaki herhangi bir kod serbestçe kısmi bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="3b7cc-176">Yöntemi çağrılır ancak uygulanmadı hiçbir derleme zamanı veya çalışma zamanı hataları neden olur.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="3b7cc-177">Kısmi yöntemler bir şekilde oluşturulan kod özelleştirmek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="3b7cc-178">İçin bir yöntem adı sağlarlar ve böylece kod oluşturulan ayrılması için imza yöntemi çağırabilirsiniz ancak geliştirici yöntemi uygulamak karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="3b7cc-179">Çok parçalı sınıflar gibi bir kod Oluşturucu tarafından oluşturulan kodu ve çalışma zamanı maliyetleri birlikte çalışmak için bir insan geliştirici tarafından oluşturulan kodu kısmi yöntemler etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="3b7cc-180">Kısmi yöntem bildiriminde iki bölümden oluşur: tanımı ve uygulaması.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="3b7cc-181">Bunlar ayrı bölümlerini kısmi bir sınıf ya da aynı bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="3b7cc-182">Hiçbir uygulama bildirimi yok sonra derleyici, hemen her iki tanımlama iyileştirir ve yöntemine yönelik tüm çağrılar bildirimi.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="3b7cc-183">Kısmi yöntem bildiriminin bağlamsal anahtar sözcüğüyle başlamalı [kısmi](../../../csharp/language-reference/keywords/partial-type.md) ve yöntem döndürmelidir [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="3b7cc-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>

- <span data-ttu-id="3b7cc-184">Kısmi yöntemler olabilir [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) veya [ref](../../../csharp/language-reference/keywords/ref.md) ama [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="3b7cc-185">Kısmi yöntemler dolaylı olarak olan [özel](../../../csharp/language-reference/keywords/private.md), ve bu nedenle olamaz [sanal](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="3b7cc-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="3b7cc-186">Kısmi yöntemler olamaz [extern](../../../csharp/language-reference/keywords/extern.md), Varlık gövdesi bunlar tanımlama uygulama mı olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="3b7cc-187">Kısmi yöntemler olabilir [statik](../../../csharp/language-reference/keywords/static.md) ve [güvenli](../../../csharp/language-reference/keywords/unsafe.md) değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="3b7cc-188">Kısmi yöntemler, genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-188">Partial methods can be generic.</span></span> <span data-ttu-id="3b7cc-189">Kısıtlamaları tanımlayan kısmi yöntem bildiriminde yerleştirilir ve isteğe bağlı olarak uygulayan bir yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="3b7cc-190">Parametre adları parametre ve türü tanımlayan bir olduğu gibi uygulama bildiriminde aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="3b7cc-191">Yapabileceğiniz bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) tanımlanan ve uygulanan kısmi bir yöntem, ancak yalnızca tanımlı bir kısmi yöntem değil.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3b7cc-192">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b7cc-192">C# Language Specification</span></span>

<span data-ttu-id="3b7cc-193">Daha fazla bilgi için [kısmi türlerinden](~/_csharplang/spec/classes.md#partial-types) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b7cc-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="3b7cc-194">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b7cc-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-195">See also</span></span>

- [<span data-ttu-id="3b7cc-196">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b7cc-196">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3b7cc-197">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-197">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="3b7cc-198">Yapılar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-198">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="3b7cc-199">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-199">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="3b7cc-200">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="3b7cc-200">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
