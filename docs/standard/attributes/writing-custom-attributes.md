---
title: Özel Öznitelikler Yazma
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140578"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="7977b-102">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="7977b-102">Writing Custom Attributes</span></span>
<span data-ttu-id="7977b-103">Kendi özel özniteliklerinizi tasarlamak için birçok yeni kavramda ustalaşmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7977b-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="7977b-104">Nesne yönelimli programlamaya aşinaysanız ve sınıfları nasıl tasarladığınızı biliyorsanız, zaten gereken bilginin çoğuna sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="7977b-105">Özel öznitelikler, temelde doğrudan veya dolaylı olarak <xref:System.Attribute?displayProperty=nameWithType>türeyen geleneksel sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="7977b-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7977b-106">Geleneksel sınıflar gibi, özel öznitelikler de verileri depolayan ve alınan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="7977b-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="7977b-107">Özel öznitelik sınıflarını düzgün bir şekilde tasarlamak için birincil adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7977b-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="7977b-108">ÖznitelikUygulamaKullanımAttribute</span><span class="sxs-lookup"><span data-stu-id="7977b-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="7977b-109">Öznitelik sınıfını bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="7977b-110">Yapıcıları bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="7977b-111">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="7977b-112">Bu bölümde bu adımların her biri açıklanır ve özel bir [öznitelik örneği](#custom-attribute-example)ile sona erer.</span><span class="sxs-lookup"><span data-stu-id="7977b-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="7977b-113">ÖznitelikUygulamaKullanımAttribute</span><span class="sxs-lookup"><span data-stu-id="7977b-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="7977b-114">Özel öznitelik <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>bildirimi, öznitelik sınıfınızın bazı temel özelliklerini tanımlayan , ile başlar.</span><span class="sxs-lookup"><span data-stu-id="7977b-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="7977b-115">Örneğin, özniteliğinizin diğer sınıflar tarafından devralınıp alınamayacağını veya özniteliğin hangi öğelere uygulanabileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="7977b-116">Aşağıdaki kod <xref:System.AttributeUsageAttribute>parçası.</span><span class="sxs-lookup"><span data-stu-id="7977b-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="7977b-117">Özel <xref:System.AttributeUsageAttribute> özniteliklerin oluşturulması için önemli olan üç üyesi vardır: [AttributeTargets](#attributetargets-member), [Devralınan](#inherited-property)ve [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="7977b-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="7977b-118">ÖznitelikHedef Üye</span><span class="sxs-lookup"><span data-stu-id="7977b-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="7977b-119">Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="7977b-120">Alternatif olarak, <xref:System.AttributeTargets.Class?displayProperty=nameWithType>özniteliğinizin yalnızca bir sınıfa uygulanabileceğini belirten <xref:System.AttributeTargets.Method?displayProperty=nameWithType>veya özniteliğinizin yalnızca bir yönteme uygulanabileceğini belirten bir belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="7977b-121">Tüm program öğeleri bu şekilde özel bir öznitelik ile açıklama için işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="7977b-122">Ayrıca birden çok <xref:System.AttributeTargets> değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="7977b-123">Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntem uygulanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="7977b-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="7977b-124">Devralınan Özellik</span><span class="sxs-lookup"><span data-stu-id="7977b-124">Inherited Property</span></span>  
 <span data-ttu-id="7977b-125">Özellik, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özniteliğinizin uygulandığı sınıflardan türetilen sınıflar tarafından devralınıp alınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="7977b-126">Bu özellik bir `true` (varsayılan) `false` veya bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="7977b-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="7977b-127">Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değeri `true`, `YourAttribute` . <xref:System.AttributeUsageAttribute.Inherited%2A> `false`</span><span class="sxs-lookup"><span data-stu-id="7977b-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="7977b-128">İki öznitelik daha sonra taban sınıftabir `MyClass`yönteme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7977b-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="7977b-129">Son olarak, `YourClass` sınıf taban sınıftan `MyClass`devralır.</span><span class="sxs-lookup"><span data-stu-id="7977b-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="7977b-130">Yöntem, `MyMethod` `MyAttribute`ancak gösterir `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="7977b-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="7977b-131">Birden Fazla Özelliğe İzin Verme</span><span class="sxs-lookup"><span data-stu-id="7977b-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="7977b-132">Özellik, <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> özniteliğinizin birden çok örneğinin bir öğeüzerinde var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="7977b-133">`true`Ayarlanmışsa , birden çok örneğine izin verilir; `false` (varsayılan) olarak ayarlanmışsa, yalnızca bir örneğine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="7977b-134">Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değeri `false`, `YourAttribute` `true`.</span><span class="sxs-lookup"><span data-stu-id="7977b-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="7977b-135">Bu özniteliklerin birden çok `MyAttribute` örneği uygulandığında, derleyici hatası üretir.</span><span class="sxs-lookup"><span data-stu-id="7977b-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="7977b-136">Aşağıdaki kod örneği geçerli kullanımını `YourAttribute` ve `MyAttribute`geçersiz kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="7977b-137">Hem <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özellik hem <xref:System.AttributeUsageAttribute.Inherited%2A> de özellik `true`ayarlanmışsa, başka bir sınıftan devralınan bir sınıf bir öznitelik devralabilir ve aynı alt sınıfta uygulanan aynı öznitelik başka bir örneği olabilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="7977b-138"><xref:System.AttributeUsageAttribute.AllowMultiple%2A> Ayarlanırsa, üst sınıftaki özniteliklerin değerleri alt sınıfta ki aynı özniteliğe sahip yeni örneklertarafından üzerine `false`yazılır.</span><span class="sxs-lookup"><span data-stu-id="7977b-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="7977b-139">Öznitelik Sınıfını Bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="7977b-140"><xref:System.AttributeUsageAttribute>Uyguladıktan sonra, özniteliğinizin özelliklerini tanımlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="7977b-141">Bir öznitelik sınıfının bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıfın bildirimine benzer.</span><span class="sxs-lookup"><span data-stu-id="7977b-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="7977b-142">Bu öznitelik tanımı aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="7977b-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="7977b-143">Öznitelik sınıfları ortak sınıflar olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7977b-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="7977b-144">Öznitelik sınıfının adı, öznitelik sınıfının adı **Öznitelik**sözcüğüyle sona erer.</span><span class="sxs-lookup"><span data-stu-id="7977b-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="7977b-145">Gerekli olmasa da, bu sözleşme okunabilirlik için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="7977b-146">Öznitelik uygulandığında, Öznitelik sözcüğünün eklenmesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7977b-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="7977b-147">Tüm öznitelik sınıfları doğrudan veya <xref:System.Attribute?displayProperty=nameWithType>dolaylı olarak devralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7977b-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="7977b-148">Microsoft Visual Basic'te, tüm özel <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> öznitelik sınıfları özniteliğe sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7977b-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="7977b-149">Yapıcıları Bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-149">Declaring Constructors</span></span>  
 <span data-ttu-id="7977b-150">Öznitelikler, geleneksel sınıflarla aynı şekilde oluşturucularla başharfe alınır.</span><span class="sxs-lookup"><span data-stu-id="7977b-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="7977b-151">Aşağıdaki kod parçası tipik bir öznitelik oluşturucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="7977b-152">Bu ortak oluşturucu bir parametre alır ve değerine eşit bir üye değişken ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7977b-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="7977b-153">Farklı değer kombinasyonlarını karşılamak için oluşturucuyu aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="7977b-154">Özel öznitelik sınıfınız için bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) de tanımlarsanız, özniteliği başolarak alırken adlandırılmış ve konumsal parametrelerin bir birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="7977b-155">Genellikle, gerekli tüm parametreleri konumsal olarak ve tüm isteğe bağlı parametreleri adlandırılmış olarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="7977b-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="7977b-156">Bu durumda, öznitelik gerekli parametre olmadan başharfolamaz.</span><span class="sxs-lookup"><span data-stu-id="7977b-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="7977b-157">Diğer tüm parametreler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7977b-157">All other parameters are optional.</span></span> <span data-ttu-id="7977b-158">Visual Basic'te, öznitelik sınıfı nın oluşturucularının ParamArray bağımsız değişkeni kullanmaması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7977b-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="7977b-159">Aşağıdaki kod örneği, önceki oluşturucuyu kullanan bir özniteliğin isteğe bağlı ve gerekli parametreler kullanılarak nasıl uygulanabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="7977b-160">Bu öznitelik bir gerekli Boolean değeri ve bir isteğe bağlı dize özelliği olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7977b-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="7977b-161">Özellikleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="7977b-161">Declaring Properties</span></span>  
 <span data-ttu-id="7977b-162">Adlandırılmış bir parametre tanımlamak veya özniteliğiniz tarafından depolanan değerleri döndürmek için kolay bir yol sağlamak istiyorsanız, bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))bildirin.</span><span class="sxs-lookup"><span data-stu-id="7977b-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="7977b-163">Öznitelik özellikleri, döndürülecek veri türünün açıklamasıyla birlikte kamu tüzel kişileri olarak beyan edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7977b-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="7977b-164">Mülkünüzün değerini tutacak değişkeni tanımlayın ve **get** ve **set** yöntemleriyle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="7977b-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="7977b-165">Aşağıdaki kod örneği, özniteliğinizde basit bir özelliğin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="7977b-166">Özel Öznitelik Örneği</span><span class="sxs-lookup"><span data-stu-id="7977b-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="7977b-167">Bu bölümde önceki bilgiler içerir ve kod bir bölümünün yazarı hakkında bilgi belgeler basit bir öznitelik nasıl tasarlanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="7977b-168">Bu örnekteki öznitelik, programcının adını ve düzeyini ve kodun gözden geçirilip geçirilemediğini depolar.</span><span class="sxs-lookup"><span data-stu-id="7977b-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="7977b-169">Kaydetmek için gerçek değerleri depolamak için üç özel değişken kullanır.</span><span class="sxs-lookup"><span data-stu-id="7977b-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="7977b-170">Her değişken, değerleri alan ve ayarlayan bir kamu malı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7977b-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="7977b-171">Son olarak, yapıcı iki gerekli parametreleri ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7977b-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="7977b-172">Bu özniteliği tam adı `DeveloperAttribute`kullanarak veya kısaltılmış adı `Developer`kullanarak aşağıdaki yollardan biriyle uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977b-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="7977b-173">İlk örnek, yalnızca gerekli adlandırılmış parametrelerle uygulanan özniteliği gösterirken, ikinci örnek hem gerekli hem de isteğe bağlı parametrelerle uygulanan özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977b-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7977b-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7977b-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="7977b-175">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7977b-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
