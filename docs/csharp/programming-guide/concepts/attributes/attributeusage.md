---
title: ÖznitelikKullanım (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668724"
---
# <a name="attributeusage-c"></a><span data-ttu-id="a427b-102">ÖznitelikKullanım (C#)</span><span class="sxs-lookup"><span data-stu-id="a427b-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="a427b-103">Özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a427b-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="a427b-104"><xref:System.AttributeUsageAttribute>özel öznitelik tanımlarına uyguladığınız bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="a427b-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="a427b-105">Öznitelik, `AttributeUsage` aşağıdakileri denetlemenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="a427b-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="a427b-106">Hangi program öğeleriöze uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a427b-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="a427b-107">Kullanımını kısıtlamadığınız sürece, aşağıdaki program öğelerinden herhangi biri için bir öznitelik uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="a427b-107">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="a427b-108">derleme</span><span class="sxs-lookup"><span data-stu-id="a427b-108">assembly</span></span>
  - <span data-ttu-id="a427b-109">modül</span><span class="sxs-lookup"><span data-stu-id="a427b-109">module</span></span>
  - <span data-ttu-id="a427b-110">alan</span><span class="sxs-lookup"><span data-stu-id="a427b-110">field</span></span>
  - <span data-ttu-id="a427b-111">event</span><span class="sxs-lookup"><span data-stu-id="a427b-111">event</span></span>
  - <span data-ttu-id="a427b-112">method</span><span class="sxs-lookup"><span data-stu-id="a427b-112">method</span></span>
  - <span data-ttu-id="a427b-113">param</span><span class="sxs-lookup"><span data-stu-id="a427b-113">param</span></span>
  - <span data-ttu-id="a427b-114">özellik</span><span class="sxs-lookup"><span data-stu-id="a427b-114">property</span></span>
  - <span data-ttu-id="a427b-115">return</span><span class="sxs-lookup"><span data-stu-id="a427b-115">return</span></span>
  - <span data-ttu-id="a427b-116">type</span><span class="sxs-lookup"><span data-stu-id="a427b-116">type</span></span>
- <span data-ttu-id="a427b-117">Bir öznitelik birden çok kez tek bir program öğesine uygulanabilir olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="a427b-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="a427b-118">Özniteliklerin türetilmiş sınıflar tarafından devralınmış olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="a427b-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="a427b-119">Varsayılan ayarlar açıkça uygulandığında aşağıdaki örnek gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="a427b-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="a427b-120">Bu örnekte, `NewAttribute` sınıf desteklenen herhangi bir program öğesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a427b-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="a427b-121">Ancak her varlık için yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a427b-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="a427b-122">Öznitelik, taban sınıfa uygulandığında türetilmiş sınıflar tarafından devralınan.</span><span class="sxs-lookup"><span data-stu-id="a427b-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="a427b-123">Ve <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenler isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a427b-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="a427b-124">İlk <xref:System.AttributeUsageAttribute> bağımsız değişken numaralandırmanın <xref:System.AttributeTargets> bir veya daha fazla öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a427b-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="a427b-125">Birden çok hedef türü, aşağıdaki örnekte görüldüğü gibi, OR işleciyle birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a427b-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="a427b-126">C# 7.3'ten başlayarak, öznitelikler otomatik olarak uygulanan bir özellik için özellik veya destek alanına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a427b-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="a427b-127">Öznitelik, öznitelikte `field` belirtici belirtmediğiniz sürece özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a427b-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="a427b-128">Her ikisi de aşağıdaki örnekte gösterilir:</span><span class="sxs-lookup"><span data-stu-id="a427b-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="a427b-129"><xref:System.AttributeUsageAttribute.AllowMultiple> Bağımsız değişken `true`ise, aşağıdaki örnekte gösterildiği gibi, ortaya çıkan öznitelik tek bir varlığa birden fazla kez uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="a427b-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="a427b-130">Bu durumda, `MultiUseAttribute` '' olarak `AllowMultiple` `true`ayarlandığı için tekrar tekrar uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a427b-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="a427b-131">Birden çok öznitelik uygulamak için gösterilen her iki biçim de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a427b-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="a427b-132"><xref:System.AttributeUsageAttribute.Inherited> Ise, `false`o zaman öznitelik atfedilen bir sınıftan türetilen sınıflar tarafından devralınan değildir.</span><span class="sxs-lookup"><span data-stu-id="a427b-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="a427b-133">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a427b-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="a427b-134">Bu durumda `NonInheritedAttribute` miras `DClass` yoluyla uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="a427b-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a427b-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a427b-135">Remarks</span></span>

<span data-ttu-id="a427b-136">Öznitelik `AttributeUsage` tek kullanımlık bir özniteliktir, aynı sınıfa birden fazla kez uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a427b-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="a427b-137">`AttributeUsage`<xref:System.AttributeUsageAttribute>için bir takma addır.</span><span class="sxs-lookup"><span data-stu-id="a427b-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="a427b-138">Daha fazla bilgi için bkz: [Yansıma (C#) kullanarak Özniteliklere Erişim.](accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="a427b-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="a427b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="a427b-139">Example</span></span>

<span data-ttu-id="a427b-140">Aşağıdaki örnek, öznitelik ve <xref:System.AttributeUsageAttribute.Inherited> <xref:System.AttributeUsageAttribute> <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkenlerin etkisini ve bir sınıfa uygulanan özel özniteliklerin nasıl numaralandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a427b-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="a427b-141">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="a427b-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="a427b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a427b-142">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="a427b-143">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a427b-143">C# Programming Guide</span></span>](../..//index.md)
- [<span data-ttu-id="a427b-144">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a427b-144">Attributes</span></span>](../../../..//standard/attributes/index.md)
- [<span data-ttu-id="a427b-145">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="a427b-145">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a427b-146">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a427b-146">Attributes</span></span>](index.md)
- [<span data-ttu-id="a427b-147">Özel Öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="a427b-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="a427b-148">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="a427b-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
