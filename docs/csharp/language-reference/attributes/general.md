---
title: 'C# ayrılmış öznitelikleri: koşullu, kullanımdan kalktı, AttributeUsage'
ms.date: 04/09/2020
description: Derleyici tarafından oluşturulan kodu etkilemek için bu öznitelikler derleyici tarafından yorumlanır
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021766"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="833e5-103">Ayrılmış öznitelikler: ConditionalAttribute, kullanımdan kaldırma Teattribute, AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="833e5-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="833e5-104">Bu öznitelikler, kodunuzdaki öğelere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="833e5-105">Bunlar bu öğelere anlam anlam ekler.</span><span class="sxs-lookup"><span data-stu-id="833e5-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="833e5-106">Derleyici, kodunuzu kullanarak geliştiricilerin çıktısını değiştirmek ve olası hataları raporlamak için bu anlamsal anlamları kullanır.</span><span class="sxs-lookup"><span data-stu-id="833e5-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="833e5-107">`Conditional` özniteliği</span><span class="sxs-lookup"><span data-stu-id="833e5-107">`Conditional` attribute</span></span>

<span data-ttu-id="833e5-108">`Conditional`Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="833e5-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="833e5-109">`Conditional`Özniteliği için bir diğer addır <xref:System.Diagnostics.ConditionalAttribute> ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="833e5-110">Aşağıdaki örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="833e5-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="833e5-111">`TRACE_ON`Tanımlayıcı tanımlanmamışsa, izleme çıktısı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="833e5-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="833e5-112">Etkileşimli pencerede kendiniz için araştırma yapın.</span><span class="sxs-lookup"><span data-stu-id="833e5-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="833e5-113">`Conditional`Bu öznitelik, `DEBUG` Aşağıdaki örnekte gösterildiği gibi, genellikle hata ayıklama derlemeleri için izleme ve günlüğe kaydetme özelliklerini etkinleştirmek üzere tanımlayıcıda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="833e5-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="833e5-114">Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="833e5-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="833e5-115">Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="833e5-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="833e5-116">Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve bir `void` dönüş türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="833e5-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="833e5-117">`Conditional`' Yi kullanarak temizleyici, daha zarif ve daha az hata, bloklar içindeki kapsayan metotlardan çok daha açıktır `#if…#endif` .</span><span class="sxs-lookup"><span data-stu-id="833e5-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="833e5-118">Bir yöntemde birden çok `Conditional` öznitelik varsa, bir veya daha fazla koşullu sembol tanımlanmışsa yönteme bir çağrı dahil edilir (semboller, or işleci kullanılarak mantıksal olarak birbirlerine bağlanır).</span><span class="sxs-lookup"><span data-stu-id="833e5-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="833e5-119">Aşağıdaki örnekte, ya da `A` `B` bir yöntem çağrısında oluşur:</span><span class="sxs-lookup"><span data-stu-id="833e5-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="833e5-120">`Conditional`Öznitelik sınıfları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="833e5-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="833e5-121">`Conditional`Öznitelik, öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="833e5-122">Aşağıdaki örnekte, özel öznitelik `Documentation` yalnızca tanımlanmazsa meta verilere bilgi ekler `DEBUG` .</span><span class="sxs-lookup"><span data-stu-id="833e5-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="833e5-123">`Obsolete` özniteliği</span><span class="sxs-lookup"><span data-stu-id="833e5-123">`Obsolete` attribute</span></span>

<span data-ttu-id="833e5-124">`Obsolete`Öznitelik, artık kullanım için önerilmeyen bir kod öğesini işaretler.</span><span class="sxs-lookup"><span data-stu-id="833e5-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="833e5-125">Kullanımdan kaldırılmış olarak işaretlenmiş bir varlığın kullanımı bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="833e5-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="833e5-126">`Obsolete`Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="833e5-127">`Obsolete` , için bir diğer addır <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="833e5-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="833e5-128">Aşağıdaki örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine uygulanır `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="833e5-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="833e5-129">Öğesine uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni `B.OldMethod` olarak ayarlandığından `true` , bu yöntem bir derleyici hatasına neden olur, ancak sınıf kullanımı `A` yalnızca bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="833e5-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="833e5-130">Ancak çağırma, `B.NewMethod` hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="833e5-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="833e5-131">Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="833e5-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="833e5-132">Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="833e5-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="833e5-133">Sınıf için iki uyarı `A` oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.</span><span class="sxs-lookup"><span data-stu-id="833e5-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="833e5-134">`Obsolete`Özniteliği bağımsız değişkenler olmadan kullanılabilir, ancak bunun yerine kullanılacak bir açıklama dahil edilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="833e5-135">`AttributeUsage` özniteliği</span><span class="sxs-lookup"><span data-stu-id="833e5-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="833e5-136">`AttributeUsage`Özniteliği özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="833e5-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="833e5-137"><xref:System.AttributeUsageAttribute> , özel öznitelik tanımlarına uyguladığınız bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="833e5-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="833e5-138">`AttributeUsage`Özniteliği şunları denetlemenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="833e5-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="833e5-139">Hangi program öğeleri özniteliği uygulanabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="833e5-140">Kullanımını kısıtlamadığınız takdirde, aşağıdaki program öğelerinden birine bir öznitelik uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="833e5-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="833e5-141">derleme</span><span class="sxs-lookup"><span data-stu-id="833e5-141">assembly</span></span>
  - <span data-ttu-id="833e5-142">modül</span><span class="sxs-lookup"><span data-stu-id="833e5-142">module</span></span>
  - <span data-ttu-id="833e5-143">alan</span><span class="sxs-lookup"><span data-stu-id="833e5-143">field</span></span>
  - <span data-ttu-id="833e5-144">event</span><span class="sxs-lookup"><span data-stu-id="833e5-144">event</span></span>
  - <span data-ttu-id="833e5-145">method</span><span class="sxs-lookup"><span data-stu-id="833e5-145">method</span></span>
  - <span data-ttu-id="833e5-146">larına</span><span class="sxs-lookup"><span data-stu-id="833e5-146">param</span></span>
  - <span data-ttu-id="833e5-147">özellik</span><span class="sxs-lookup"><span data-stu-id="833e5-147">property</span></span>
  - <span data-ttu-id="833e5-148">return</span><span class="sxs-lookup"><span data-stu-id="833e5-148">return</span></span>
  - <span data-ttu-id="833e5-149">tür</span><span class="sxs-lookup"><span data-stu-id="833e5-149">type</span></span>
- <span data-ttu-id="833e5-150">Bir özniteliğin tek bir program öğesine birden çok kez uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="833e5-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="833e5-151">Özniteliklerin türetilmiş sınıflar tarafından devralınıp alınmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="833e5-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="833e5-152">Varsayılan ayarlar, açıkça uygulandığında aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="833e5-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="833e5-153">Bu örnekte, `NewAttribute` sınıfı desteklenen herhangi bir program öğesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="833e5-154">Ancak, her bir varlığa yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="833e5-155">Öznitelik, bir temel sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="833e5-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="833e5-156"><xref:System.AttributeUsageAttribute.AllowMultiple>Ve <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenleri isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="833e5-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="833e5-157">İlk <xref:System.AttributeUsageAttribute> bağımsız değişken, numaralandırmanın bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> .</span><span class="sxs-lookup"><span data-stu-id="833e5-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="833e5-158">Aşağıdaki örnekte gösterildiği gibi birden çok hedef türü OR işleciyle birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="833e5-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="833e5-159">C# 7,3 ' den başlayarak, öznitelikler bir otomatik uygulanan özelliğin özelliğine veya yedekleme alanına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="833e5-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="833e5-160">Özniteliği, özniteliğinde tanımlayıcı belirtmediğiniz müddetçe özelliği için geçerlidir `field` .</span><span class="sxs-lookup"><span data-stu-id="833e5-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="833e5-161">Her ikisi de aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="833e5-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="833e5-162"><xref:System.AttributeUsageAttribute.AllowMultiple>Bağımsız değişken ise `true` , aşağıdaki örnekte gösterildiği gibi, sonuç özniteliği tek bir varlığa birden çok kez uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="833e5-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="833e5-163">Bu durumda, `MultiUseAttribute` olarak ayarlandığı için tekrar tekrar uygulanabilir `AllowMultiple` `true` .</span><span class="sxs-lookup"><span data-stu-id="833e5-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="833e5-164">Birden çok özniteliği uygulamak için gösterilen her iki biçim de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="833e5-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="833e5-165"><xref:System.AttributeUsageAttribute.Inherited>İse `false` öznitelik, öznitelikli bir sınıftan türetilmiş sınıflar tarafından devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="833e5-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="833e5-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="833e5-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="833e5-167">Bu durumda `NonInheritedAttribute` devralma aracılığıyla öğesine uygulanmaz `DClass` .</span><span class="sxs-lookup"><span data-stu-id="833e5-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="833e5-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="833e5-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="833e5-169">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="833e5-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="833e5-170">Yansıma</span><span class="sxs-lookup"><span data-stu-id="833e5-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
