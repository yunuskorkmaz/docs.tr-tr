---
title: Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: aa0baf50b9e4aabf0bb5dfa229ecd245db391a8b
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314740"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="fcf54-102">Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fcf54-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="fcf54-103">Tanımını bölme mümkündür bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapısı](../../../csharp/language-reference/keywords/struct.md), bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) veya iki veya daha fazla kaynak dosyalar üzerinde bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="fcf54-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="fcf54-104">Her kaynak dosya türü veya yöntemi tanımının bir bölüm içerir ve uygulamanın derlendiğinde tüm bölümleri birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="fcf54-105">Kısmi sınıflar</span><span class="sxs-lookup"><span data-stu-id="fcf54-105">Partial Classes</span></span>  
 <span data-ttu-id="fcf54-106">Bir sınıf tanımı bölme arzu olduğunda bazı durumlar vardır:</span><span class="sxs-lookup"><span data-stu-id="fcf54-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="fcf54-107">Büyük projeler üzerinde çalışırken, ayrı dosyalar üzerinde bir sınıf yayılmak birden çok programcıların üzerinde aynı anda çalışması olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="fcf54-108">Otomatik olarak oluşturulan kaynağı ile çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan sınıfına kod eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="fcf54-109">Windows Forms, Web hizmeti sarmalayıcı kodu ve benzeri oluşturduğunda, visual Studio bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="fcf54-110">Visual Studio tarafından oluşturulan dosyasını değiştirmek zorunda kalmadan bu sınıfları kullanan kodu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="fcf54-111">Bir sınıf tanımı bölmek için kullanın [kısmi](../../../csharp/language-reference/keywords/partial-type.md) anahtar sözcüğü değiştiricisi, aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="fcf54-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 <span data-ttu-id="fcf54-112">`partial` Arabirimi ad alanında tanımlanabilir veya anahtar sözcüğü sınıf, yapı, diğer parçalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="fcf54-113">Tüm bölümleri kullanmalısınız `partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fcf54-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="fcf54-114">Tüm bölümleri adresinde son türü oluşturmak için zaman derleyin.</span><span class="sxs-lookup"><span data-stu-id="fcf54-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="fcf54-115">Tüm bölümleri aynı erişilebilirlik gibi olmalıdır `public`, `private`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="fcf54-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="fcf54-116">Herhangi bir bölümünü soyut bildirilirse, tüm türünü soyut olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="fcf54-117">Tam tür korumalı olarak kabul edilip sonra herhangi bir bölümünü korumalı, bildirilirse.</span><span class="sxs-lookup"><span data-stu-id="fcf54-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="fcf54-118">Herhangi bir bölümünü bir taban türü bildirirse, tüm türü o sınıfın devralır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-118">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="fcf54-119">Bir taban sınıfı belirtin tüm bölümleri kabul etmeniz gerekir, ancak bir taban sınıf atlayın bölümleri hala temel türü devralır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="fcf54-120">Son türü tarafından tüm kısmi bildirimleri listelenen tüm arabirimlerini uygular ve parça farklı temel arabirimleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="fcf54-121">Herhangi bir sınıf, yapısı veya kısmi tanımında bildirilen arabirim üyeleri için diğer tüm bölümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="fcf54-122">Son türü tüm bölümleri derleme zamanında birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-122">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcf54-123">`partial` Değiştiricisi temsilci ya da numaralandırması bildirimlerinde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="fcf54-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="fcf54-124">Aşağıdaki örnek, içinde iç içe türü kısmi olmasa bile, iç içe geçmiş türler kendisini kısmi, olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 <span data-ttu-id="fcf54-125">Derleme zamanında kısmi tür tanımları özniteliklerini birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="fcf54-126">Örneğin, aşağıdaki bildirimlerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fcf54-126">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 <span data-ttu-id="fcf54-127">Bunlar aşağıdaki bildirimi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="fcf54-127">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 <span data-ttu-id="fcf54-128">Aşağıdaki tüm kısmi türü tanımları birleştirilir:</span><span class="sxs-lookup"><span data-stu-id="fcf54-128">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="fcf54-129">XML açıklamaları</span><span class="sxs-lookup"><span data-stu-id="fcf54-129">XML comments</span></span>  
  
-   <span data-ttu-id="fcf54-130">arabirimler</span><span class="sxs-lookup"><span data-stu-id="fcf54-130">interfaces</span></span>  
  
-   <span data-ttu-id="fcf54-131">genel tür parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="fcf54-131">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="fcf54-132">class öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="fcf54-132">class attributes</span></span>  
  
-   <span data-ttu-id="fcf54-133">üyeler</span><span class="sxs-lookup"><span data-stu-id="fcf54-133">members</span></span>  
  
 <span data-ttu-id="fcf54-134">Örneğin, aşağıdaki bildirimlerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fcf54-134">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 <span data-ttu-id="fcf54-135">Bunlar aşağıdaki bildirimi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="fcf54-135">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a><span data-ttu-id="fcf54-136">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="fcf54-136">Restrictions</span></span>  
 <span data-ttu-id="fcf54-137">Parçalı sınıf tanımları ile çalışırken izlemek için çeşitli kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fcf54-137">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="fcf54-138">Aynı türde bölümleri olma amacını tüm kısmi tür tanımları ile değiştirilmelidir `partial`.</span><span class="sxs-lookup"><span data-stu-id="fcf54-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="fcf54-139">Örneğin, aşağıdaki sınıf bildirimleri bir hata oluştur:</span><span class="sxs-lookup"><span data-stu-id="fcf54-139">For example, the following class declarations generate an error:</span></span>  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   <span data-ttu-id="fcf54-140">`partial` Değiştiricisi yalnızca hemen önce anahtar sözcükleri görünür `class`, `struct`, veya `interface`.</span><span class="sxs-lookup"><span data-stu-id="fcf54-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="fcf54-141">Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş kısmi türler kısmi türü tanımlarına izin verilir:</span><span class="sxs-lookup"><span data-stu-id="fcf54-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   <span data-ttu-id="fcf54-142">Aynı türde bölümleri olma amacını tüm kısmi tür tanımları aynı bütünleştirilmiş kodda ve aynı Modülü (.exe veya .dll dosyası) tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="fcf54-143">Kısmi tanımları birden fazla modülü yayılamaz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-143">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="fcf54-144">Genel tür parametreleri ve sınıf adı tüm kısmi türü tanımlarını eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="fcf54-145">Genel türler kısmi olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-145">Generic types can be partial.</span></span> <span data-ttu-id="fcf54-146">Her kısmi bildirimi aynı parametre adları aynı sırada kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-146">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="fcf54-147">Kısmi tür tanımı aşağıdaki anahtar sözcükler isteğe bağlıdır, ancak varsa bir kısmi tür tanımı, aynı türde başka bir kısmi tanımında belirtilen anahtar sözcükleri çakışmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="fcf54-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="fcf54-148">public</span><span class="sxs-lookup"><span data-stu-id="fcf54-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="fcf54-149">private</span><span class="sxs-lookup"><span data-stu-id="fcf54-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="fcf54-150">protected</span><span class="sxs-lookup"><span data-stu-id="fcf54-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="fcf54-151">internal</span><span class="sxs-lookup"><span data-stu-id="fcf54-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="fcf54-152">abstract</span><span class="sxs-lookup"><span data-stu-id="fcf54-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="fcf54-153">sealed</span><span class="sxs-lookup"><span data-stu-id="fcf54-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="fcf54-154">taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="fcf54-154">base class</span></span>  
  
    -   <span data-ttu-id="fcf54-155">[Yeni](../../../csharp/language-reference/keywords/new.md) değiştiricisi (iç içe geçmiş parça)</span><span class="sxs-lookup"><span data-stu-id="fcf54-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="fcf54-156">Genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="fcf54-156">generic constraints</span></span>  
  
         <span data-ttu-id="fcf54-157">Daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="fcf54-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="fcf54-158">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="fcf54-158">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="fcf54-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcf54-159">Description</span></span>  
 <span data-ttu-id="fcf54-160">Aşağıdaki örnek, alanları ve sınıf `CoOrds`, bir parçalı sınıf tanımı ve üye bildirilen `PrintCoOrds`, başka bir parçalı sınıf tanımı'nda bildirilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-160">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fcf54-161">Kod</span><span class="sxs-lookup"><span data-stu-id="fcf54-161">Code</span></span>  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="fcf54-162">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="fcf54-162">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="fcf54-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcf54-163">Description</span></span>  
 <span data-ttu-id="fcf54-164">Aşağıdaki örnek, ayrıca kısmi yapıları ve arabirimleri geliştirebilirsiniz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-164">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fcf54-165">Kod</span><span class="sxs-lookup"><span data-stu-id="fcf54-165">Code</span></span>  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a><span data-ttu-id="fcf54-166">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fcf54-166">Partial Methods</span></span>  
 <span data-ttu-id="fcf54-167">Kısmi bir yöntem, kısmi sınıfta veya yapı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="fcf54-168">Sınıfının bir parçası yönteminin imza içeriyor.</span><span class="sxs-lookup"><span data-stu-id="fcf54-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="fcf54-169">İsteğe bağlı bir uygulama aynı bölüme veya başka bir parçası tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="fcf54-170">Uygulama sağlanmazsa, derleme zamanında yöntemi ve yöntemine yönelik tüm çağrılar kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="fcf54-171">Kısmi yöntemler, bir olaya benzer bir yöntemi tanımlamak uygulayan bir sınıf bir parçası olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="fcf54-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="fcf54-172">Bir sınıf parçası uygulayan yöntemi veya uygulamak karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="fcf54-173">Yöntem uygulanmadı sonra yöntemi derleyici kaldırır imza ve yöntemine yönelik tüm çağrılar.</span><span class="sxs-lookup"><span data-stu-id="fcf54-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="fcf54-174">Değerlendirme çağrıları bağımsız değişkenleri oluşacak sonuçları dahil olmak üzere yöntem çağrıları çalışma zamanında bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fcf54-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="fcf54-175">Bu nedenle, uygulama sağlanmadı olsa bile bir parçalı sınıf kodda serbestçe kısmi bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="fcf54-176">Yöntemi çağrıldı ancak uygulanmadı içeriyorsa hiçbir derleme zamanı ya da çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="fcf54-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="fcf54-177">Kısmi yöntemler oluşturulan kod özelleştirmek için bir yol olarak özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="fcf54-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="fcf54-178">Bir yöntem adı için izin ve böylece kodu oluşturulan ayrılmasını imza yöntemini çağırabilir ancak geliştirici yöntemi uygulamak karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="fcf54-179">Çok parçalı sınıflar gibi bir kod Oluşturucu tarafından oluşturulan kodu ve birlikte çalışma zamanı maliyetleri çalışacak biçimde İnsan geliştirici tarafından oluşturulan kodu kısmi yöntemler etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="fcf54-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="fcf54-180">Kısmi yöntem bildirimi iki bölümden oluşur: tanımı ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="fcf54-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="fcf54-181">Bunlar, ayrı bir parçalı sınıf bölümlerini ya da aynı bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="fcf54-182">Hiçbir uygulama bildirimi yok sonra derleyici hemen her iki tanımlama en iyi duruma getirir ve yöntemine yönelik tüm çağrılar bildirimi.</span><span class="sxs-lookup"><span data-stu-id="fcf54-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="fcf54-183">Kısmi yöntem bildirimleri bağlamsal anahtar sözcüğü ile başlamalıdır [kısmi](../../../csharp/language-reference/keywords/partial-type.md) ve yöntem döndürmelidir [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="fcf54-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="fcf54-184">Kısmi yöntemler olabilir [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) veya [ref](../../../csharp/language-reference/keywords/ref.md) ama [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="fcf54-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
-   <span data-ttu-id="fcf54-185">Kısmi yöntemler şunlardır örtük olarak [özel](../../../csharp/language-reference/keywords/private.md), ve bu nedenle olamaz [sanal](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="fcf54-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="fcf54-186">Kısmi yöntemler olamaz [extern](../../../csharp/language-reference/keywords/extern.md), çünkü gövdesi varlığını bunlar tanımlama uygulama ya da olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fcf54-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="fcf54-187">Kısmi yöntemler olabilir [statik](../../../csharp/language-reference/keywords/static.md) ve [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="fcf54-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="fcf54-188">Kısmi yöntemler genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-188">Partial methods can be generic.</span></span> <span data-ttu-id="fcf54-189">Kısıtlamaları tanımlayan kısmi yöntemi bildirimde yerleştirilir ve uygulayan bir isteğe bağlı olarak yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="fcf54-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="fcf54-190">Parametre adları parametre ve türünü tanımlayan bir olduğu gibi uygulama bildiriminde aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fcf54-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="fcf54-191">Yapabileceğiniz bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) tanımlanan ve uygulanan bir kısmi yöntemi, ancak yalnızca tanımlı bir kısmi yöntem değil.</span><span class="sxs-lookup"><span data-stu-id="fcf54-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fcf54-192">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fcf54-192">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fcf54-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf54-193">See Also</span></span>  
 [<span data-ttu-id="fcf54-194">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fcf54-194">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fcf54-195">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="fcf54-195">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [<span data-ttu-id="fcf54-196">Yapılar</span><span class="sxs-lookup"><span data-stu-id="fcf54-196">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="fcf54-197">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fcf54-197">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="fcf54-198">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="fcf54-198">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
