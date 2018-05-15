---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="attributeusage-c"></a><span data-ttu-id="5dd80-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="5dd80-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="5dd80-103">Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5dd80-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="5dd80-104"><xref:System.AttributeUsageAttribute> özel öznitelik tanımları için uygulamanıza bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="5dd80-105">`AttributeUsage` Özniteliği denetimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="5dd80-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="5dd80-106">Hangi program öğeleri öznitelik için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="5dd80-107">Kısıtlama sürece, kullanımdır herhangi bir program öğesi için bir öznitelik uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="5dd80-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="5dd80-108">derleme</span><span class="sxs-lookup"><span data-stu-id="5dd80-108">assembly</span></span>
  - <span data-ttu-id="5dd80-109">modül</span><span class="sxs-lookup"><span data-stu-id="5dd80-109">module</span></span>
  - <span data-ttu-id="5dd80-110">alan</span><span class="sxs-lookup"><span data-stu-id="5dd80-110">field</span></span>
  - <span data-ttu-id="5dd80-111">olay</span><span class="sxs-lookup"><span data-stu-id="5dd80-111">event</span></span>
  - <span data-ttu-id="5dd80-112">yöntemi</span><span class="sxs-lookup"><span data-stu-id="5dd80-112">method</span></span>
  - <span data-ttu-id="5dd80-113">Param</span><span class="sxs-lookup"><span data-stu-id="5dd80-113">param</span></span>
  - <span data-ttu-id="5dd80-114">özellik</span><span class="sxs-lookup"><span data-stu-id="5dd80-114">property</span></span>
  - <span data-ttu-id="5dd80-115">return</span><span class="sxs-lookup"><span data-stu-id="5dd80-115">return</span></span>
  - <span data-ttu-id="5dd80-116">türü</span><span class="sxs-lookup"><span data-stu-id="5dd80-116">type</span></span>
- <span data-ttu-id="5dd80-117">Olup bir öznitelik birden çok kez tek bir program öğesi için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="5dd80-118">Olup öznitelikleri türetilmiş sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="5dd80-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="5dd80-119">Varsayılan ayarları açıkça uygulandığında aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="5dd80-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="5dd80-120">Bu örnekte, `NewAttribute` sınıfı, tüm desteklenen bir program öğesi için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="5dd80-121">Ancak yalnızca bir kez her varlık için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="5dd80-122">Öznitelik, bir temel sınıf uygulandığında türetilen sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="5dd80-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="5dd80-123"><xref:System.AttributeUsageAttribute.AllowMultiple> Ve <xref:System.AttributeUsageAttribute.Inherited> değişkenleridir isteğe bağlı, aşağıdaki kodu aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5dd80-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="5dd80-124">İlk <xref:System.AttributeUsageAttribute> bağımsız değişkeni, bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="5dd80-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="5dd80-125">Birden çok hedef türleri, aşağıdaki örnekte gösterildiği gibi OR işleci birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="5dd80-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="5dd80-126">C# 7.3 içinde başlayarak, öznitelikler özelliği veya yedekleme alanını otomatik uygulanan bir özellik için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="5dd80-127">Belirtmediğiniz sürece öznitelik özelliğine uygular `field` öznitelikte tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5dd80-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="5dd80-128">Her ikisi de aşağıdaki örnekte gösterilir:</span><span class="sxs-lookup"><span data-stu-id="5dd80-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="5dd80-129">Varsa <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkeni `true`, sonuçta elde edilen özniteliği birden çok kez tek bir varlık için aşağıdaki örnekte gösterildiği gibi uygulanabilir sonra:</span><span class="sxs-lookup"><span data-stu-id="5dd80-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="5dd80-130">Bu durumda, `MultiUseAttribute` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="5dd80-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="5dd80-131">Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5dd80-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="5dd80-132">Varsa <xref:System.AttributeUsageAttribute.Inherited> olan `false`, öznitelik öznitelikli sınıfından türetilen sınıflar tarafından devralınır değil sonra.</span><span class="sxs-lookup"><span data-stu-id="5dd80-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="5dd80-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5dd80-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="5dd80-134">Bu durumda `NonInheritedAttribute` için uygulanmaz `DClass` devralma aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="5dd80-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dd80-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5dd80-135">Remarks</span></span>

<span data-ttu-id="5dd80-136">`AttributeUsage` Özniteliktir tek kullanımlık özniteliği--birden çok kez aynı sınıfa uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="5dd80-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="5dd80-137">`AttributeUsage` bir diğer adı için <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5dd80-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="5dd80-138">Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5dd80-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="5dd80-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dd80-139">Example</span></span>

<span data-ttu-id="5dd80-140">Aşağıdaki örnek, etkisini gösterir <xref:System.AttributeUsageAttribute.Inherited> ve <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkenleri <xref:System.AttributeUsageAttribute> özniteliğini ve bir sınıfa uygulanan özel öznitelikler nasıl listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="5dd80-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="5dd80-141">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="5dd80-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="5dd80-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dd80-142">See Also</span></span>
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="5dd80-143">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5dd80-143">C# Programming Guide</span></span>](../..//index.md)  
 [<span data-ttu-id="5dd80-144">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5dd80-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
 [<span data-ttu-id="5dd80-145">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="5dd80-145">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="5dd80-146">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5dd80-146">Attributes</span></span>](index.md)  
 [<span data-ttu-id="5dd80-147">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="5dd80-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
 [<span data-ttu-id="5dd80-148">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="5dd80-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
