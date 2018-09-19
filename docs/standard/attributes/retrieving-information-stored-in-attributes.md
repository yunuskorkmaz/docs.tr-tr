---
title: Özniteliklerde Depolanan Bilgileri Alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7021a984f844660c45ae3e2d98569432ab64b657
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003002"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="2200d-102">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="2200d-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="2200d-103">Özel bir öznitelik alma basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2200d-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="2200d-104">Öncelikle, almak istediğiniz öznitelik örneği bildirin.</span><span class="sxs-lookup"><span data-stu-id="2200d-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="2200d-105">Ardından, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> almak istediğiniz özniteliğinin değeri için yeni öznitelik başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2200d-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="2200d-106">Yeni öznitelik başlatıldıktan sonra sadece özellikleri değerlerini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2200d-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2200d-107">Bu konu, kod yürütme bağlamı yüklenen öznitelikleri almak açıklar.</span><span class="sxs-lookup"><span data-stu-id="2200d-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="2200d-108">Salt yansıma bağlamına yüklenen kod öznitelikleri almak için kullanmanız gerekir <xref:System.Reflection.CustomAttributeData> gösterildiği gibi sınıf [nasıl yapılır: derlemeleri Reflection-Only bağlamına](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="2200d-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="2200d-109">Bu bölümde, öznitelikleri almak için aşağıdaki yöntemleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="2200d-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="2200d-110">Tek bir örneği bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="2200d-111">Birden fazla aynı kapsam için uygulanan bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="2200d-112">Birden çok örneğini farklı kapsamlara uygulanan bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="2200d-113">Tek bir örneği bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="2200d-114">Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanmıştır) uygulanan `MainApp` sınıf düzeyinde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2200d-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="2200d-115">`GetAttribute` Yöntemi kullanan **GetCustomAttribute** depolanan değerleri almak için `DeveloperAttribute` bunları konsola göstermeden önce sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="2200d-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="2200d-116">Bu program çalıştırıldığında aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2200d-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="2200d-117">Öznitelik bulunamazsa **GetCustomAttribute** yöntemi başlatır `MyAttribute` bir null değer.</span><span class="sxs-lookup"><span data-stu-id="2200d-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="2200d-118">Bu örnek denetler `MyAttribute` bu tür bir örnek için ve bir öznitelik yok bulunursa kullanıcıyı uyarır.</span><span class="sxs-lookup"><span data-stu-id="2200d-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="2200d-119">Varsa `DeveloperAttribute` bulunamadı sınıf kapsamında aşağıdaki iletiyi konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2200d-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="2200d-120">Bu örnekte, öznitelik tanımı geçerli bir ad alanında olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="2200d-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="2200d-121">Geçerli bir ad alanında değilse, öznitelik tanımı bulunduğu ad alanı almayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2200d-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="2200d-122">Birden fazla aynı kapsam için uygulanan bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="2200d-123">Önceki örnekte, inceleme sınıfı ve bulmak için özel öznitelik geçirilen <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="2200d-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="2200d-124">Bu kod, bir özniteliğin bir örnek sınıf düzeyinde de uygulanır, yalnızca çalışır.</span><span class="sxs-lookup"><span data-stu-id="2200d-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="2200d-125">Ancak, bir özniteliğin birden çok örneği aynı sınıf düzeyinde uygulanmışsa **GetCustomAttribute** yöntemi tüm bilgileri alamadı.</span><span class="sxs-lookup"><span data-stu-id="2200d-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="2200d-126">Aynı öznitelik birden çok örneğini aynı kapsama uygulanır olduğu durumlarda, kullandığınız <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> bir özniteliğin tüm örnekleri bir dizi içine yerleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="2200d-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="2200d-127">Örneğin, iki örneklerini `DeveloperAttribute` aynı sınıfın sınıf düzeyinde uygulanan `GetAttribute` yöntemi, her iki öznitelikleri içinde bulunan bilgileri görüntülemek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2200d-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="2200d-128">Unutmayın aynı düzeyde birden çok öznitelik uygulamak için özniteliği ile tanımlanmalıdır **AttributeUsage** özelliğini **true** içinde <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2200d-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="2200d-129">Aşağıdaki kod örneği kullanma işlemini gösterir **GetCustomAttributes** tüm örneklerini başvuran bir dizi oluşturmak için gereken yöntemini `DeveloperAttribute` birinde sınıfı verilir.</span><span class="sxs-lookup"><span data-stu-id="2200d-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="2200d-130">Tüm özniteliklerinin değerlerini sonra konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2200d-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="2200d-131">Hiç öznitelik bulunamadı, bu kod, kullanıcıyı uyarır.</span><span class="sxs-lookup"><span data-stu-id="2200d-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="2200d-132">Aksi takdirde, bilgileri bulunan iki örneklerine `DeveloperAttribute` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2200d-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="2200d-133">Birden çok örneğini farklı kapsamlara uygulanan bir öznitelik alma</span><span class="sxs-lookup"><span data-stu-id="2200d-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="2200d-134"><xref:System.Attribute.GetCustomAttributes%2A> Ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri değil sınıfının tümüne arayın ve bu sınıfta bir öznitelik tüm örneklerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2200d-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="2200d-135">Bunun yerine, bunlar yalnızca bir belirtilen yöntem veya üye aynı anda arayın.</span><span class="sxs-lookup"><span data-stu-id="2200d-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="2200d-136">Bir sınıf her üyeye uygulanan aynı özniteliğe sahip ve bu üyeler için uygulanan tüm öznitelikleri değerleri almak istediğiniz her bir yöntem veya üye için ayrı ayrı sağlamanız gerekir **GetCustomAttributes** ve  **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="2200d-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="2200d-137">Aşağıdaki kod örneği, bir sınıf bir parametre olarak alır ve arar `DeveloperAttribute` (tanımlanan önceden) Sınıf düzeyinde ve söz konusu sınıfın tek tek her yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2200d-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="2200d-138">Örneği, `DeveloperAttribute` yöntem düzeyine ya da sınıf düzeyinde bulunan `GetAttribute` yöntemi hiçbir öznitelik bulunamadı kullanıcıya bildirir ve yöntem veya özniteliği içermiyor, sınıf adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2200d-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="2200d-139">Bir öznitelik bulunursa `Name`, `Level`, ve `Reviewed` alanları, konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2200d-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="2200d-140">Üyelerinin kullanabileceği <xref:System.Type> geçirilen sınıfı üyeleri ve her bir yöntem almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2200d-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="2200d-141">Bu örnekte ilk sorgular **türü** sınıf düzeyinde için öznitelik bilgileri almak için nesne.</span><span class="sxs-lookup"><span data-stu-id="2200d-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="2200d-142">Ardından, kullanır <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tüm yöntemleri örnekleri bir dizi içine yerleştirmek için <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> nesneleri yöntem düzeyine öznitelik bilgileri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="2200d-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="2200d-143">Ayrıca <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> özellik düzeyinde öznitelikler için denetlenecek yöntemi veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> Oluşturucusu düzeyindeki öznitelikler denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="2200d-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2200d-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2200d-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>  
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="2200d-145">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2200d-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
