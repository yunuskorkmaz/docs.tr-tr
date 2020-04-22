---
title: 'C# ayrılmış öznitelikler: Koşullu, Eski, ÖznitelikKullanım'
ms.date: 04/09/2020
description: Bu öznitelikler derleyici tarafından oluşturulan kodu etkilemek için derleyici tarafından yorumlanır
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021766"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="29cb0-103">Ayrılmış öznitelikler: Koşullu Öznitelik, EskiÖzÖzöz, ÖznitelikKullanımAttribute</span><span class="sxs-lookup"><span data-stu-id="29cb0-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="29cb0-104">Bu öznitelikler, kodunuzdaki öğelere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="29cb0-105">Bu elementlere anlamsal anlam katarlar.</span><span class="sxs-lookup"><span data-stu-id="29cb0-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="29cb0-106">Derleyici, çıktısını değiştirmek ve kodunuzu kullanan geliştiricilerin olası hatalarını bildirmek için bu anlamsal anlamları kullanır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="29cb0-107">`Conditional` özniteliği</span><span class="sxs-lookup"><span data-stu-id="29cb0-107">`Conditional` attribute</span></span>

<span data-ttu-id="29cb0-108">Öznitelik, `Conditional` bir yöntemin yürütülmesini bir ön işleme tanımlayıcısı bağımlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="29cb0-109">Öznitelik, `Conditional` <xref:System.Diagnostics.ConditionalAttribute>bir diğer adıdır ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="29cb0-110">Aşağıdaki örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı etmek için bir yöntem uygulanır:</span><span class="sxs-lookup"><span data-stu-id="29cb0-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="29cb0-111">`TRACE_ON` Tanımlayıcı tanımlanmamışsa, izleme çıktısı görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="29cb0-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="29cb0-112">Etkileşimli pencerede kendiniz keşfedin.</span><span class="sxs-lookup"><span data-stu-id="29cb0-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="29cb0-113">Öznitelik `Conditional` genellikle aşağıdaki örnekte gösterildiği gibi, hata ayıklama yapılar için izleme ve günlük özelliklerini etkinleştirmek için tanımlayıcı ile `DEBUG` kullanılır, ancak sürüm yapılarda değil:</span><span class="sxs-lookup"><span data-stu-id="29cb0-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="29cb0-114">Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme sembolünün varlığı veya yokluğu, çağrının dahil edilip edilmeyeceğini veya atlanıp atlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="29cb0-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="29cb0-115">Sembol tanımlanırsa, çağrı dahil edilir; aksi takdirde, arama atlanır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="29cb0-116">Koşullu yöntem, bir sınıf veya yapı bildiriminde bir yöntem `void` olmalı ve bir dönüş türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="29cb0-117">Kullanma, `Conditional` blokların içine `#if…#endif` girme yöntemlerinden daha temiz, daha zarif ve daha az hataya açıktır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="29cb0-118">Bir yöntemin `Conditional` birden çok özniteliği varsa, bir veya daha fazla koşullu sembol tanımlanırsa (semboller OR işleci kullanılarak mantıksal olarak birbirine bağlanır) yönteme çağrı bulunur.</span><span class="sxs-lookup"><span data-stu-id="29cb0-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="29cb0-119">Aşağıdaki örnekte, bir yöntem `A` `B` çağrısıya neden olan veya bu çağrılardan birinin varlığı:</span><span class="sxs-lookup"><span data-stu-id="29cb0-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="29cb0-120">Öznitelik sınıfları ile kullanma `Conditional`</span><span class="sxs-lookup"><span data-stu-id="29cb0-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="29cb0-121">Öznitelik, `Conditional` öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="29cb0-122">Aşağıdaki örnekte, özel öznitelik `Documentation` yalnızca tanımlanmışsa `DEBUG` meta verilere bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="29cb0-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="29cb0-123">`Obsolete` özniteliği</span><span class="sxs-lookup"><span data-stu-id="29cb0-123">`Obsolete` attribute</span></span>

<span data-ttu-id="29cb0-124">Öznitelik `Obsolete` artık kullanım için önerilen bir kod öğesi işaretler.</span><span class="sxs-lookup"><span data-stu-id="29cb0-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="29cb0-125">Eski işaretlenmiş bir varlığın kullanımı bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29cb0-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="29cb0-126">Öznitelik `Obsolete` tek kullanımlık bir özniteliktir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="29cb0-127">`Obsolete`<xref:System.ObsoleteAttribute>için bir takma addır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="29cb0-128">Aşağıdaki örnekte `Obsolete` öznitelik sınıfa `A` ve yönteme `B.OldMethod`uygulanır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="29cb0-129">Öznitelik oluşturucu uygulanan ikinci bağımsız `B.OldMethod` değişken için `true`ayarlanmış olduğundan, bu yöntem derleyici hatasına neden olurken, sınıf `A` kullanarak sadece bir uyarı üretecektir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="29cb0-130">Ancak `B.NewMethod`arama, hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="29cb0-131">Örneğin, önceki tanımlarla kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29cb0-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="29cb0-132">Öznitelik oluşturucuya ilk bağımsız değişken olarak sağlanan dize, uyarı veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="29cb0-133">Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvuru bildirimi için, diğeri sınıf oluşturucusu için.</span><span class="sxs-lookup"><span data-stu-id="29cb0-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="29cb0-134">Öznitelik `Obsolete` bağımsız değişkenler olmadan kullanılabilir, ancak bunun yerine ne kullanılacağı bir açıklama da dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="29cb0-135">`AttributeUsage` özniteliği</span><span class="sxs-lookup"><span data-stu-id="29cb0-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="29cb0-136">Öznitelik, özel bir öznitelik sınıfının `AttributeUsage` nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="29cb0-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="29cb0-137"><xref:System.AttributeUsageAttribute>özel öznitelik tanımlarına uyguladığınız bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="29cb0-138">Öznitelik, `AttributeUsage` aşağıdakileri denetlemenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="29cb0-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="29cb0-139">Hangi program öğeleriöze uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="29cb0-140">Kullanımını kısıtlamadığınız sürece, aşağıdaki program öğelerinden herhangi biri için bir öznitelik uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="29cb0-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="29cb0-141">derleme</span><span class="sxs-lookup"><span data-stu-id="29cb0-141">assembly</span></span>
  - <span data-ttu-id="29cb0-142">modül</span><span class="sxs-lookup"><span data-stu-id="29cb0-142">module</span></span>
  - <span data-ttu-id="29cb0-143">alan</span><span class="sxs-lookup"><span data-stu-id="29cb0-143">field</span></span>
  - <span data-ttu-id="29cb0-144">event</span><span class="sxs-lookup"><span data-stu-id="29cb0-144">event</span></span>
  - <span data-ttu-id="29cb0-145">method</span><span class="sxs-lookup"><span data-stu-id="29cb0-145">method</span></span>
  - <span data-ttu-id="29cb0-146">param</span><span class="sxs-lookup"><span data-stu-id="29cb0-146">param</span></span>
  - <span data-ttu-id="29cb0-147">özellik</span><span class="sxs-lookup"><span data-stu-id="29cb0-147">property</span></span>
  - <span data-ttu-id="29cb0-148">return</span><span class="sxs-lookup"><span data-stu-id="29cb0-148">return</span></span>
  - <span data-ttu-id="29cb0-149">type</span><span class="sxs-lookup"><span data-stu-id="29cb0-149">type</span></span>
- <span data-ttu-id="29cb0-150">Bir öznitelik birden çok kez tek bir program öğesine uygulanabilir olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="29cb0-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="29cb0-151">Özniteliklerin türetilmiş sınıflar tarafından devralınmış olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="29cb0-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="29cb0-152">Varsayılan ayarlar açıkça uygulandığında aşağıdaki örnek gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="29cb0-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="29cb0-153">Bu örnekte, `NewAttribute` sınıf desteklenen herhangi bir program öğesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="29cb0-154">Ancak her varlık için yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="29cb0-155">Öznitelik, taban sınıfa uygulandığında türetilmiş sınıflar tarafından devralınan.</span><span class="sxs-lookup"><span data-stu-id="29cb0-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="29cb0-156">Ve <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenler isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="29cb0-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="29cb0-157">İlk <xref:System.AttributeUsageAttribute> bağımsız değişken numaralandırmanın <xref:System.AttributeTargets> bir veya daha fazla öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29cb0-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="29cb0-158">Birden çok hedef türü, aşağıdaki örnekte görüldüğü gibi, OR işleciyle birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="29cb0-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="29cb0-159">C# 7.3'ten başlayarak, öznitelikler otomatik olarak uygulanan bir özellik için özellik veya destek alanına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="29cb0-160">Öznitelik, öznitelikte `field` belirtici belirtmediğiniz sürece özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="29cb0-161">Her ikisi de aşağıdaki örnekte gösterilir:</span><span class="sxs-lookup"><span data-stu-id="29cb0-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="29cb0-162"><xref:System.AttributeUsageAttribute.AllowMultiple> Bağımsız değişken `true`ise, aşağıdaki örnekte gösterildiği gibi, ortaya çıkan öznitelik tek bir varlığa birden fazla kez uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="29cb0-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="29cb0-163">Bu durumda, `MultiUseAttribute` '' olarak `AllowMultiple` `true`ayarlandığı için tekrar tekrar uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="29cb0-164">Birden çok öznitelik uygulamak için gösterilen her iki biçim de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="29cb0-165"><xref:System.AttributeUsageAttribute.Inherited> Ise, `false`o zaman öznitelik atfedilen bir sınıftan türetilen sınıflar tarafından devralınan değildir.</span><span class="sxs-lookup"><span data-stu-id="29cb0-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="29cb0-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="29cb0-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="29cb0-167">Bu durumda `NonInheritedAttribute` miras `DClass` yoluyla uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="29cb0-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="29cb0-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29cb0-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="29cb0-169">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29cb0-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="29cb0-170">Yansıma</span><span class="sxs-lookup"><span data-stu-id="29cb0-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
