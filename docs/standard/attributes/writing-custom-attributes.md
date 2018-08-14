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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114d24c1fc523d5501deb4aa17f9541c5a918276
ms.sourcegitcommit: c66ba2df2d2ecfb214f85ee0687d298e4941c1a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2018
ms.locfileid: "33574653"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="67ef3-102">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="67ef3-102">Writing Custom Attributes</span></span>
<span data-ttu-id="67ef3-103">Kendi özel öznitelikler tasarlamak için çok sayıda yeni kavramları ana gerekmez.</span><span class="sxs-lookup"><span data-stu-id="67ef3-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="67ef3-104">Nesne odaklı programlama ile ilgili bilgi sahibi olduğunuz ve sınıfları tasarlama ne yapılacağını bildiğiniz, ihtiyacınız olan bilgileri çoğunu zaten vardır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="67ef3-105">Özel öznitelikler sınıflardır doğrudan veya dolaylı olarak türetilen temelde geleneksel <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67ef3-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67ef3-106">Yalnızca geleneksel sınıflar gibi özel öznitelikler, veri depolama ve alma yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="67ef3-107">Özel öznitelik sınıfları düzgün bir şekilde tasarlamak için birincil adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="67ef3-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="67ef3-108">AttributeUsageAttribute uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="67ef3-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="67ef3-109">Öznitelik sınıf bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="67ef3-110">Oluşturucuları bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="67ef3-111">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="67ef3-112">Bu bölümde, bu adımların her biri açıklar ve ile sonucuna bir [özel öznitelik örnek](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="67ef3-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="67ef3-113">AttributeUsageAttribute uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="67ef3-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="67ef3-114">Bir özel özniteliği bildirimi ile başlayan <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, bazı önemli özelliklerinden biri, öznitelik sınıfı tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="67ef3-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="67ef3-115">Örneğin, öznitelik diğer sınıfları tarafından miras veya öznitelik uygulanabilir hangi elementleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67ef3-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="67ef3-116">Aşağıdaki kod parçası nasıl kullanılacağını gösteren <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="67ef3-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="67ef3-117"><xref:System.AttributeUsageAttribute> Özel öznitelikler oluşturmak için önemli olan üç üye vardır: [AttributeTargets](#attributetargets-member), [devralınan](#inherited-property), ve [AttributeUsage](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="67ef3-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="67ef3-118">AttributeTargets üyesi</span><span class="sxs-lookup"><span data-stu-id="67ef3-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="67ef3-119">Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> , bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="67ef3-120">Alternatif olarak, belirtebilirsiniz <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, gösteren, özniteliği yalnızca bir sınıfa uygulanabilir veya <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, gösteren, özniteliği yalnızca bir yöntem için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="67ef3-121">Tüm program öğelerinin açıklaması için bu şekilde özel bir öznitelik tarafından işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="67ef3-122">Ayrıca birden çok geçirebilirsiniz <xref:System.AttributeTargets> değerleri.</span><span class="sxs-lookup"><span data-stu-id="67ef3-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="67ef3-123">Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntemi uygulanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="67ef3-124">Devralınan özellik</span><span class="sxs-lookup"><span data-stu-id="67ef3-124">Inherited Property</span></span>  
 <span data-ttu-id="67ef3-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özelliği, öznitelik, öznitelik uygulandığı sınıflarından türetilen sınıflar tarafından devralınıp alınmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="67ef3-126">Bu özellik ya da gereken bir `true` (varsayılan) veya `false` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="67ef3-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="67ef3-127">Aşağıdaki örnekte, `MyAttribute` bir varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değerini `true`, ancak `YourAttribute` sahip bir <xref:System.AttributeUsageAttribute.Inherited%2A> değerini `false`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="67ef3-128">İki öznitelikleri sonra bir yöntem temel sınıfta uygulanır `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="67ef3-129">Son olarak, sınıf `YourClass` temel sınıftan devralınan `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="67ef3-130">Yöntem `MyMethod` gösterir `MyAttribute`, ama `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="67ef3-131">AllowMultiple özelliği</span><span class="sxs-lookup"><span data-stu-id="67ef3-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="67ef3-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Özelliği, öznitelik birden fazla örneğini bir öğe üzerinde mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="67ef3-133">Varsa kümesine `true`, birden çok örneği; kodlanabilmesi kümesine `false` (varsayılan), yalnızca bir örneğine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="67ef3-134">Aşağıdaki örnekte, `MyAttribute` bir varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerini `false`, ancak `YourAttribute` değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="67ef3-135">Bu öznitelikler birden çok örneğini uygulandığında, `MyAttribute` bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67ef3-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="67ef3-136">Aşağıdaki kod örneği geçerli kullanımını gösterir `YourAttribute` ve geçersiz kullanımı `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="67ef3-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="67ef3-137">Her iki <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği ve <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği ayarlandığında `true`, başka bir sınıftan devralınan bir sınıf özniteliği devralır ve başka bir örneğinin aynı alt sınıf içinde uygulanan aynı özniteliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="67ef3-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="67ef3-138">Varsa <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ayarlanır `false`, üst sınıftaki herhangi bir öznitelik değerleri, aynı öznitelik, alt sınıfın yeni örneklerini tarafından üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="67ef3-139">Öznitelik sınıf bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="67ef3-140">Uygulandıktan sonra <xref:System.AttributeUsageAttribute>, özniteliğinizi özelliklerini tanımlamak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67ef3-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="67ef3-141">Öznitelik sınıfı bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıf bildirimine gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="67ef3-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="67ef3-142">Bu öznitelik tanımı aşağıdaki noktaları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="67ef3-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="67ef3-143">Öznitelik sınıfları, genel sınıf olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="67ef3-144">Kural gereği, öznitelik sınıfı adını word ile sona erer **özniteliği**.</span><span class="sxs-lookup"><span data-stu-id="67ef3-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="67ef3-145">Gerekli olmasa da, bu kuralı okunabilirlik açısından önerilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="67ef3-146">Öznitelik uygulandığında, eklenmesi, öznitelik sözcüğünü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="67ef3-147">Tüm öznitelik sınıfları doğrudan veya dolaylı olarak devralmalıdır <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67ef3-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="67ef3-148">Microsoft Visual Basic'te, tüm özel öznitelik sınıfları olmalıdır <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="67ef3-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="67ef3-149">Oluşturucuları bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-149">Declaring Constructors</span></span>  
 <span data-ttu-id="67ef3-150">Öznitelikleri oluşturucularla geleneksel sınıflar olarak aynı şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="67ef3-151">Aşağıdaki kod parçası, tipik öznitelik oluşturucusunda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="67ef3-152">Bu ortak oluşturucu, bir parametre alır ve bir üye değişkeni değerine eşit olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67ef3-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="67ef3-153">Değer farklı birleşimleri uyum sağlamak için oluşturucu aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="67ef3-154">Ayrıca tanımlarsanız bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) özel öznitelik sınıfınız için bir adlandırılmış ve konumsal parametreler birleşimi öznitelik başlatılırken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67ef3-154">If you also define a [property](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="67ef3-155">Genellikle, gerekli tüm parametreleri konumsal ve tüm isteğe bağlı parametreleri olarak adlandırılan tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="67ef3-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="67ef3-156">Bu durumda, öznitelik gerekli parametresi olmadan başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="67ef3-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="67ef3-157">Diğer tüm parametreler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-157">All other parameters are optional.</span></span> <span data-ttu-id="67ef3-158">Visual Basic'te bir ParamArray bağımsız değişkeni bir öznitelik sınıfı için oluşturucular kullanmamalısınız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="67ef3-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="67ef3-159">Aşağıdaki kod örneği, önceki Oluşturucusu isteğe bağlıdır ve gerekli parametreleri kullanarak uygulanabilir kullanan bir öznitelik nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="67ef3-160">Bu öznitelik gerekli bir Boole değeri ve isteğe bağlı bir dize özelliği olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="67ef3-161">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="67ef3-161">Declaring Properties</span></span>  
 <span data-ttu-id="67ef3-162">İsterseniz adlandırılmış bir parametre tanımlayın veya, özniteliği tarafından depolanan değer döndürmek için kolay bir yol sağlar, bildirmek bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="67ef3-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="67ef3-163">Öznitelik özellikleri ile döndürülecek veri türünün açıklaması genel varlıklar olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="67ef3-164">Özelliğin değerini tutun ve ilişkilendirin değişkeni tanımlamanız **alma** ve **ayarlamak** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="67ef3-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="67ef3-165">Aşağıdaki kod örneği, özniteliğinde basit bir özelliğin uygulanması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="67ef3-166">Özel öznitelik örneği</span><span class="sxs-lookup"><span data-stu-id="67ef3-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="67ef3-167">Bu bölümde, önceki bilgileri içerir ve kodun bir bölümünü Yazar hakkında bilgi belgeleri, basit bir öznitelik tasarlama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="67ef3-168">Bu örnekte öznitelik Programcı düzeyini ve adını depolar ve kod olup olmadığını gözden geçirildi.</span><span class="sxs-lookup"><span data-stu-id="67ef3-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="67ef3-169">Üç özel değişkenlere kaydetmek için gerçek değerleri depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="67ef3-170">Her bir değişken alır ve ayarlar ortak bir özelliği tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="67ef3-171">Son olarak, Oluşturucu iki gerekli parametreler ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="67ef3-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="67ef3-172">Bu öznitelik tam adı kullanılarak uygulayabilirsiniz `DeveloperAttribute`, ya da kısa ad kullanarak `Developer`, aşağıdaki yollardan biriyle.</span><span class="sxs-lookup"><span data-stu-id="67ef3-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="67ef3-173">İlk örnekte, yalnızca gerekli parametreler, hem gerekli ve isteğe bağlı parametrelerle uygulanan öznitelik gösterirken, ikinci örnek adlı ile uygulanan öznitelik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ef3-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ef3-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67ef3-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>  
 [<span data-ttu-id="67ef3-175">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67ef3-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
