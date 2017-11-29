---
title: "Özel Öznitelikler Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="65d98-102">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="65d98-102">Writing Custom Attributes</span></span>
<span data-ttu-id="65d98-103">Kendi özel öznitelikler tasarlamak için birçok yeni kavram ana gerekmez.</span><span class="sxs-lookup"><span data-stu-id="65d98-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="65d98-104">Nesne odaklı programlama ile bilgi sahibiyseniz ve sınıflar tasarlamak nasıl biliyorsanız gerekli bilgi çoğunu zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="65d98-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="65d98-105">Özel öznitelikler sınıflardır doğrudan veya dolaylı olarak türetilen temelde geleneksel <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65d98-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65d98-106">Yalnızca geleneksel sınıfları gibi özel öznitelikler veri depolanıp yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="65d98-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="65d98-107">Özel öznitelik sınıfları düzgün tasarlamak için birincil adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="65d98-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="65d98-108">AttributeUsageAttribute uygulama</span><span class="sxs-lookup"><span data-stu-id="65d98-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="65d98-109">Öznitelik sınıfı bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="65d98-110">Oluşturucuları bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="65d98-111">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="65d98-112">Bu bölümde bu adımların her biri açıklar ve ile sonucuna bir [özel öznitelik örnek](#cpconcustomattributeexample).</span><span class="sxs-lookup"><span data-stu-id="65d98-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="65d98-113">AttributeUsageAttribute uygulama</span><span class="sxs-lookup"><span data-stu-id="65d98-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="65d98-114">Bir özel öznitelik bildirim **AttributeUsageAttribute**, bazı öznitelik sınıfı anahtar özelliklerini tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="65d98-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="65d98-115">Örneğin, özniteliğinizi diğer sınıflar tarafından devralınır veya öznitelik uygulanabilir hangi öğelerin belirtin belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d98-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="65d98-116">Aşağıdaki kod parçası nasıl kullanılacağı ortaya **AttributeUsageAttribute**.</span><span class="sxs-lookup"><span data-stu-id="65d98-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="65d98-117"><xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Özel öznitelikler oluşturma için önemli olan üç üyeler içeriyor: [AttributeTargets](#cpconwritingcustomattributesanchor1), [devralınan](#cpconwritingcustomattributesanchor2), ve [AttributeUsage](#cpconwritingcustomattributesanchor3).</span><span class="sxs-lookup"><span data-stu-id="65d98-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="65d98-118">AttributeTargets üyesi</span><span class="sxs-lookup"><span data-stu-id="65d98-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="65d98-119">Önceki örnekte, **AttributeTargets.All** , bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="65d98-120">Alternatif olarak, belirtebilirsiniz **AttributeTargets.Class**, özniteliğinizi yalnızca bir sınıfa uygulanabilir belirten veya **AttributeTargets.Method**, özniteliğinizi uygulanabilir belirten yalnızca bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="65d98-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="65d98-121">Tüm program öğelerinin açıklaması için bu şekilde özel bir öznitelik tarafından işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="65d98-122">Birden çok örneğini geçebilen <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="65d98-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="65d98-123">Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntemini uygulanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="65d98-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="65d98-124">Devralınan özellik</span><span class="sxs-lookup"><span data-stu-id="65d98-124">Inherited Property</span></span>  
 <span data-ttu-id="65d98-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özelliği, özniteliğinizi özniteliğinizi uygulanan sınıflarından türetilmiş sınıflar tarafından devralınır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="65d98-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="65d98-126">Bu özellik ya da gereken bir **true** (varsayılan) veya **false** bayrağı.</span><span class="sxs-lookup"><span data-stu-id="65d98-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="65d98-127">Örneğin, aşağıdaki örnekte, `MyAttribute` varsayılan sahip <xref:System.AttributeUsageAttribute.Inherited%2A> değerini **true**, sırada `YourAttribute` sahip bir <xref:System.AttributeUsageAttribute.Inherited%2A> değerini **false**.</span><span class="sxs-lookup"><span data-stu-id="65d98-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="65d98-128">İki öznitelik sonra bir yöntem temel sınıfta uygulanır `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="65d98-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="65d98-129">Son olarak, sınıf `YourClass` temel sınıfından devralınan `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="65d98-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="65d98-130">Yöntem `MyMethod` gösterir `MyAttribute`, ama `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="65d98-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="65d98-131">AllowMultiple özelliği</span><span class="sxs-lookup"><span data-stu-id="65d98-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="65d98-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Özelliği, birden çok örneğini özniteliğinizi bir öğede mevcut olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="65d98-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="65d98-133">Varsa kümesine **true**, birden çok örneği; izin verilir kümesine **false** (varsayılan), yalnızca bir örneğine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="65d98-134">Aşağıdaki örnekte, `MyAttribute` varsayılan sahip <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerini **false**, sırada `YourAttribute` değerine sahip **doğru**.</span><span class="sxs-lookup"><span data-stu-id="65d98-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="65d98-135">Bu öznitelikler birden çok örneğini uygulandığında `MyAttribute` derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65d98-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="65d98-136">Aşağıdaki kod örneğinde geçerli kullanımı gösterilmiştir `YourAttribute` ve geçersiz kullanımı `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="65d98-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="65d98-137">Her iki <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği ve <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği ayarlanmış **doğru**, başka bir sınıftan devralınan bir sınıf bir öznitelik devralır ve başka bir örneği aynı alt sınıfta uygulanan aynı özniteliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="65d98-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="65d98-138">Varsa <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ayarlanır **yanlış**, üst sınıfında herhangi bir öznitelik değerleri yeni alt sınıf içinde aynı öznitelik örneklerini üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="65d98-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="65d98-139">Öznitelik sınıfı bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="65d98-140">Uygulandıktan sonra <xref:System.AttributeUsageAttribute>, özniteliğinizi özelliklerini tanımlamak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d98-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="65d98-141">Bir öznitelik sınıfı bildirimi aşağıdaki kodda gösterildiği gibi geleneksel bir sınıf bildirimine benzer.</span><span class="sxs-lookup"><span data-stu-id="65d98-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="65d98-142">Bu öznitelik tanımı aşağıdaki noktaları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="65d98-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="65d98-143">Öznitelik sınıfları ortak sınıfları olarak bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="65d98-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="65d98-144">Kurala göre öznitelik sınıfı adını bitip sözcüğüyle **özniteliği**.</span><span class="sxs-lookup"><span data-stu-id="65d98-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="65d98-145">Gerekli olmasa da, bu kural okunabilirlik için önerilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="65d98-146">Öznitelik uygulandığında, öznitelik word'ün eklenmesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65d98-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="65d98-147">Tüm öznitelik sınıfları öğesinden devralmalıdır doğrudan veya dolaylı olarak **System.Attribute'un**.</span><span class="sxs-lookup"><span data-stu-id="65d98-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="65d98-148">Microsoft Visual Basic'te, tüm özel öznitelik sınıfları olmalıdır **AttributeUsageAttribute** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="65d98-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="65d98-149">Oluşturucuları bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-149">Declaring Constructors</span></span>  
 <span data-ttu-id="65d98-150">Öznitelikleri oluşturucular ile aynı şekilde geleneksel sınıflar olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="65d98-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="65d98-151">Aşağıdaki kod parçası, tipik öznitelik oluşturucunun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="65d98-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="65d98-152">Bu ortak oluşturucu bir parametre alır ve bir üye değişkenine eşittir değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65d98-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="65d98-153">Farklı değerleri birleşimlerini uyum sağlayacak şekilde Oluşturucusu aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="65d98-154">Ayrıca tanımlarsanız bir [özelliği](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) , özel öznitelik sınıfı için adlandırılmış ve konumsal parametreler birleşimi öznitelik başlatırken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d98-154">If you also define a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="65d98-155">Genellikle, gerekli tüm parametreleri olarak konumsal ve tüm isteğe bağlı parametreler olarak adlandırılan tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="65d98-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="65d98-156">Bu durumda, öznitelik gerekli parametresi olmadan başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="65d98-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="65d98-157">Diğer tüm parametreler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65d98-157">All other parameters are optional.</span></span> <span data-ttu-id="65d98-158">Visual Basic'te bir ParamArray bağımsız değişkeni oluşturucuları öznitelik sınıfı için kullanmamalıdır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65d98-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="65d98-159">Aşağıdaki kod örneğinde, önceki Oluşturucusu isteğe bağlıdır ve gerekli parametreleri kullanılarak uygulanabilir kullanan bir öznitelik nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="65d98-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="65d98-160">Bu öznitelik gerekli bir Boole değeri ve isteğe bağlı bir dize özelliği olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="65d98-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="65d98-161">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="65d98-161">Declaring Properties</span></span>  
 <span data-ttu-id="65d98-162">Adlandırılmış bir parametre tanımlayın veya özniteliği tarafından depolanan değer döndürmek için kolay bir yol sağlamak için bildirmek istiyorsanız, bir [özelliği](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="65d98-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="65d98-163">Öznitelik özellikleri döndürülecek veri türünün açıklaması ile genel varlıklar olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="65d98-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="65d98-164">Özelliğin değerini tutun ve bu ilişkilendirmeyi değişkeni tanımlamanız **almak** ve **ayarlamak** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="65d98-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="65d98-165">Aşağıdaki kod örneği, basit bir özellik, özniteliğinde uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="65d98-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="65d98-166">Özel öznitelik örneği</span><span class="sxs-lookup"><span data-stu-id="65d98-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="65d98-167">Bu bölümde, önceki bilgileri bir araya getirir ve kod bölümünün Yazar hakkında bilgi belgeleri basit bir öznitelik tasarlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="65d98-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="65d98-168">Bu örnekte öznitelik Programcı düzeyini ve adını depolar ve kod olup olmadığını gözden.</span><span class="sxs-lookup"><span data-stu-id="65d98-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="65d98-169">Üç özel değişkenleri kaydetmek için gerçek değerlerini depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="65d98-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="65d98-170">Her bir değişken alır ve değerlerini ayarlayan ortak bir özelliği tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="65d98-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="65d98-171">Son olarak, Oluşturucusu iki gerekli parametre ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="65d98-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="65d98-172">Tam adını kullanarak bu öznitelik uygulayabilirsiniz `DeveloperAttribute`, veya kısa ad kullanarak `Developer`, aşağıdaki yollardan biriyle.</span><span class="sxs-lookup"><span data-stu-id="65d98-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="65d98-173">İlk örnek ile yalnızca gerekli hem gerekli ve isteğe bağlı parametreleri ile uygulanan öznitelik gösterirken, ikinci örnek adlandırılmış parametreleri, uygulanan öznitelik gösterir.</span><span class="sxs-lookup"><span data-stu-id="65d98-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d98-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65d98-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="65d98-175">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="65d98-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
