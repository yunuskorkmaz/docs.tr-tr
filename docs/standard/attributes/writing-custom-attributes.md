---
title: Özel Öznitelikler Yazma
description: .NET ' te kendi özel öznitelerinizi tasarlayın. Özel öznitelikler temelde doğrudan veya dolaylı olarak System. Attribute 'dan türetilmiş sınıflardır.
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
ms.openlocfilehash: 3cae8de9b76aa9953b21ad2e23ad003e97555aa9
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768488"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="83c63-104">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="83c63-104">Writing Custom Attributes</span></span>
<span data-ttu-id="83c63-105">Kendi özel öznitelerinizi tasarlamak için çok sayıda yeni kavram oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="83c63-105">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="83c63-106">Nesne odaklı programlama hakkında bilgi sahibiyseniz ve sınıfların nasıl tasarlanacağını biliyorsanız, daha fazla bilgiye sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="83c63-106">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="83c63-107">Özel öznitelikler temelde doğrudan veya dolaylı olarak türetilmiş geleneksel sınıflardır <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="83c63-107">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83c63-108">Geleneksel sınıflar gibi özel öznitelikler ise verileri depolayan ve alan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="83c63-108">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="83c63-109">Özel öznitelik sınıflarını doğru şekilde tasarlamak için birincil adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83c63-109">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="83c63-110">AttributeUsageAttribute uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="83c63-110">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="83c63-111">Öznitelik sınıfını bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-111">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="83c63-112">Oluşturucu bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-112">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="83c63-113">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-113">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="83c63-114">Bu bölümde, bu adımların her biri açıklanmakta ve özel bir [öznitelik örneği](#custom-attribute-example)ile sonlanır.</span><span class="sxs-lookup"><span data-stu-id="83c63-114">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="83c63-115">AttributeUsageAttribute uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="83c63-115">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="83c63-116">Özel bir öznitelik bildirimi, <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> öznitelik sınıfınızın bazı anahtar özelliklerini tanımlayan ile başlar.</span><span class="sxs-lookup"><span data-stu-id="83c63-116">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="83c63-117">Örneğin, özniteetin diğer sınıfların devralınıp alınmayacağını belirtebilir veya özniteliğin hangi öğeleri uygulanacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c63-117">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="83c63-118">Aşağıdaki kod parçası, ' nin nasıl kullanılacağını göstermektedir <xref:System.AttributeUsageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="83c63-118">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="83c63-119">, <xref:System.AttributeUsageAttribute> Özel özniteliklerin oluşturulması için önemli olan üç üyeye sahiptir: [AttributeTargets](#attributetargets-member), [devralınan](#inherited-property)ve [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="83c63-119">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="83c63-120">AttributeTargets üyesi</span><span class="sxs-lookup"><span data-stu-id="83c63-120">AttributeTargets Member</span></span>  
 <span data-ttu-id="83c63-121">Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> Bu özniteliğin tüm program öğelerine uygulanabileceğini belirten belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83c63-121">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="83c63-122">Alternatif olarak, <xref:System.AttributeTargets.Class?displayProperty=nameWithType> özniteliğiyle yalnızca bir sınıfa uygulanabileceğini veya <xref:System.AttributeTargets.Method?displayProperty=nameWithType> özniteliğiyle yalnızca bir yönteme uygulanabileceğini belirten belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c63-122">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="83c63-123">Tüm program öğeleri, bu şekilde özel bir öznitelik tarafından açıklama için işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="83c63-123">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="83c63-124">Ayrıca birden çok değer geçirebilirsiniz <xref:System.AttributeTargets> .</span><span class="sxs-lookup"><span data-stu-id="83c63-124">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="83c63-125">Aşağıdaki kod parçası, özel bir özniteliğin herhangi bir sınıfa veya yönteme uygulanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="83c63-125">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="83c63-126">Devralınan Özellik</span><span class="sxs-lookup"><span data-stu-id="83c63-126">Inherited Property</span></span>  
 <span data-ttu-id="83c63-127"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>Özelliği, özniteettiğiniz özniteliğin uygulandığı sınıflardan türetilmiş sınıflar tarafından devralınıp alınmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="83c63-127">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="83c63-128">Bu özellik bir `true` (varsayılan) ya da bayrağını alır `false` .</span><span class="sxs-lookup"><span data-stu-id="83c63-128">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="83c63-129">Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değerine sahiptir `true` , ancak `YourAttribute` <xref:System.AttributeUsageAttribute.Inherited%2A> değerini içerir `false` .</span><span class="sxs-lookup"><span data-stu-id="83c63-129">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="83c63-130">Bu iki öznitelik daha sonra temel sınıftaki bir yönteme uygulanır `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="83c63-130">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="83c63-131">Son olarak, sınıfı `YourClass` temel sınıftan devralınır `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="83c63-131">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="83c63-132">Yöntemi `MyMethod` gösterir `MyAttribute` , ancak değil `YourAttribute` .</span><span class="sxs-lookup"><span data-stu-id="83c63-132">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="83c63-133">AllowMultiple özelliği</span><span class="sxs-lookup"><span data-stu-id="83c63-133">AllowMultiple Property</span></span>  
 <span data-ttu-id="83c63-134"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType>Özelliği, özniteliğinde birden çok özniteliğin bir öğede mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-134">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="83c63-135">Olarak ayarlanırsa `true` , birden çok örneğe izin verilir; `false` (varsayılan) olarak ayarlandıysa, yalnızca bir örneğe izin verilir.</span><span class="sxs-lookup"><span data-stu-id="83c63-135">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="83c63-136">Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerine sahiptir `false` , ancak `YourAttribute` değerini içerir `true` .</span><span class="sxs-lookup"><span data-stu-id="83c63-136">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="83c63-137">Bu özniteliklerin birden çok örneği uygulandığında `MyAttribute` bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83c63-137">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="83c63-138">Aşağıdaki kod örneği, öğesinin geçerli kullanımını `YourAttribute` ve geçersiz kullanımını gösterir `MyAttribute` .</span><span class="sxs-lookup"><span data-stu-id="83c63-138">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="83c63-139">Hem <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği hem de <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği olarak ayarlandıysa `true` , başka bir sınıftan devralınan bir sınıf bir özniteliği devralınabilir ve aynı özniteliğin aynı alt sınıfta uygulanan başka bir örneğine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="83c63-139">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="83c63-140"><xref:System.AttributeUsageAttribute.AllowMultiple%2A>Olarak ayarlanırsa `false` , üst sınıftaki özniteliklerin değerlerinin, alt sınıfta aynı özniteliğin yeni örnekleri tarafından üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="83c63-140">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="83c63-141">Öznitelik sınıfını bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-141">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="83c63-142">Uygulamasını uyguladıktan sonra <xref:System.AttributeUsageAttribute> , öznitedefinizin ayrıntılarını tanımlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c63-142">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="83c63-143">Bir öznitelik sınıfının bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıfın bildirimine benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="83c63-143">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="83c63-144">Bu öznitelik tanımı aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="83c63-144">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="83c63-145">Öznitelik sınıfları ortak sınıf olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="83c63-145">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="83c63-146">Kural gereği, öznitelik sınıfının adı Word **özniteliğiyle**biter.</span><span class="sxs-lookup"><span data-stu-id="83c63-146">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="83c63-147">Gerekli olmasa da, bu kural okunabilirlik için önerilir.</span><span class="sxs-lookup"><span data-stu-id="83c63-147">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="83c63-148">Özniteliği uygulandığında, Word özniteliğinin eklenmesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83c63-148">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="83c63-149">Tüm öznitelik sınıflarının doğrudan veya dolaylı olarak devralması gerekir <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="83c63-149">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="83c63-150">Microsoft Visual Basic 'de tüm özel öznitelik sınıflarının <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> özniteliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83c63-150">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="83c63-151">Oluşturucu bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-151">Declaring Constructors</span></span>  
 <span data-ttu-id="83c63-152">Öznitelikler, geleneksel sınıflarla aynı şekilde oluşturucular ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="83c63-152">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="83c63-153">Aşağıdaki kod parçası tipik bir öznitelik oluşturucusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-153">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="83c63-154">Bu ortak Oluşturucu bir parametre alır ve değerine eşit bir üye değişkenini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="83c63-154">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="83c63-155">Oluşturucuyu farklı değer kombinasyonlarını kapsayacak şekilde aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c63-155">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="83c63-156">Özel öznitelik sınıfınız için bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) de tanımlarsanız, özniteliği başlatırken adlandırılmış ve Konumsal parametrelerin birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c63-156">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="83c63-157">Genellikle, tüm gerekli parametreleri Konumsal olarak ve tüm isteğe bağlı parametreleri adlandırılmış olarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="83c63-157">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="83c63-158">Bu durumda, öznitelik gerekli parametre olmadan başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="83c63-158">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="83c63-159">Diğer tüm parametreler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83c63-159">All other parameters are optional.</span></span> <span data-ttu-id="83c63-160">Visual Basic bir öznitelik sınıfı için oluşturucuların bir ParamArray bağımsız değişkeni kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="83c63-160">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="83c63-161">Aşağıdaki kod örneği, önceki oluşturucuyu kullanan bir özniteliğin isteğe bağlı ve gerekli parametreler kullanılarak nasıl uygulanabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-161">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="83c63-162">Özniteliğin bir zorunlu Boole değeri ve bir isteğe bağlı dize özelliği olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="83c63-162">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="83c63-163">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="83c63-163">Declaring Properties</span></span>  
 <span data-ttu-id="83c63-164">Adlandırılmış bir parametre tanımlamak veya öznitedefinizin tarafından depolanan değerleri döndürmek için kolay bir yol sağlamak istiyorsanız, bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))bildirin.</span><span class="sxs-lookup"><span data-stu-id="83c63-164">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="83c63-165">Öznitelik özellikleri döndürülecek veri türü açıklamasına sahip ortak varlıklar olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="83c63-165">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="83c63-166">Özelliğin değerini tutacak değişkeni tanımlayın ve **Get** ve **set** yöntemleriyle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="83c63-166">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="83c63-167">Aşağıdaki kod örneği, öznitelikinizdeki basit bir özelliğin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-167">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="83c63-168">Özel öznitelik örneği</span><span class="sxs-lookup"><span data-stu-id="83c63-168">Custom Attribute Example</span></span>  
 <span data-ttu-id="83c63-169">Bu bölüm önceki bilgileri içerir ve bir kod bölümünün yazarı hakkındaki bilgileri belgeleyen basit bir özniteliğin nasıl tasarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-169">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="83c63-170">Bu örnekteki özniteliği, programcının adını ve düzeyini ve kodun gözden geçirilip geçirilmediğini depolar.</span><span class="sxs-lookup"><span data-stu-id="83c63-170">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="83c63-171">Bu, kaydedilecek gerçek değerleri depolamak için üç özel değişken kullanır.</span><span class="sxs-lookup"><span data-stu-id="83c63-171">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="83c63-172">Her değişken, değerleri alıp ayarlayan ortak bir özellik tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="83c63-172">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="83c63-173">Son olarak, Oluşturucu iki gerekli parametre ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="83c63-173">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="83c63-174">Bu özniteliği, aşağıdaki yollarla tam adı, `DeveloperAttribute` veya kısaltılmış adı kullanarak uygulayabilirsiniz `Developer` .</span><span class="sxs-lookup"><span data-stu-id="83c63-174">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="83c63-175">İlk örnek, yalnızca gerekli adlandırılmış parametrelerle uygulanan özniteliği gösterir, ikinci örnek, hem gerekli hem de isteğe bağlı parametrelerle uygulanan özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="83c63-175">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c63-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83c63-176">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="83c63-177">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83c63-177">Attributes</span></span>](index.md)
