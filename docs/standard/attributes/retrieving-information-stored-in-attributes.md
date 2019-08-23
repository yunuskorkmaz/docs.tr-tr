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
ms.openlocfilehash: 298ac8eae0a8b125ddf5f1ff35658f426f6b10aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968591"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="45af5-102">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="45af5-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="45af5-103">Özel bir özniteliğin alınması basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="45af5-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="45af5-104">İlk olarak, almak istediğiniz özniteliğin bir örneğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="45af5-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="45af5-105">Ardından, yeni özniteliğini <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> almak istediğiniz özniteliğin değerine başlatmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="45af5-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="45af5-106">Yeni özniteliği başlatıldıktan sonra, değerlerini almak için özelliklerini kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="45af5-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45af5-107">Bu konu, yürütme bağlamına yüklenen kodun özniteliklerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="45af5-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="45af5-108">Yalnızca yansıma bağlamına yüklenen kodun özniteliklerini almak için, <xref:System.Reflection.CustomAttributeData> sınıfını [şöyle gösterildiği gibi kullanmanız gerekir: Derlemeleri yalnızca yansıma bağlamına](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="45af5-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="45af5-109">Bu bölümde özniteliklerin alınması için aşağıdaki yollar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="45af5-109">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="45af5-110">Bir özniteliğin tek bir örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="45af5-111">Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="45af5-112">Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="45af5-113">Bir özniteliğin tek bir örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="45af5-114">Aşağıdaki örnekte, `DeveloperAttribute` sınıf düzeyindeki `MainApp` sınıfına (önceki bölümde açıklanan) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="45af5-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="45af5-115">Yöntemi, içinde`DeveloperAttribute` depolanan değerleri konsola görüntülemeden önce sınıf düzeyinde elde etmek için **GetCustomAttribute kullanır.** `GetAttribute`</span><span class="sxs-lookup"><span data-stu-id="45af5-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="45af5-116">Bu program yürütüldüğünde aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45af5-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="45af5-117">Özniteliği bulunamazsa **GetCustomAttribute** yöntemi null değer olarak başlatılır `MyAttribute` .</span><span class="sxs-lookup"><span data-stu-id="45af5-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="45af5-118">Bu örnek, `MyAttribute` böyle bir örnek olup olmadığını denetler ve bir öznitelik bulunmazsa kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="45af5-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="45af5-119">`DeveloperAttribute` Sınıf kapsamında bulunmazsa, aşağıdaki ileti konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45af5-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="45af5-120">Bu örnek, öznitelik tanımının geçerli ad alanında olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="45af5-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="45af5-121">Geçerli ad alanında değilse öznitelik tanımının bulunduğu ad alanını içeri aktarmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="45af5-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="45af5-122">Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="45af5-123">Önceki örnekte, incelenecek sınıf ve bulunacak özel öznitelik geçirilir <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="45af5-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="45af5-124">Bu kod, sınıf düzeyinde bir özniteliğin yalnızca bir örneği uygulandığında iyi bir şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="45af5-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="45af5-125">Ancak, aynı sınıf düzeyinde bir özniteliğin birden çok örneği uygulanırsa **GetCustomAttribute** yöntemi tüm bilgileri almaz.</span><span class="sxs-lookup"><span data-stu-id="45af5-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="45af5-126">Aynı özniteliğin birden fazla örneğinin aynı kapsama uygulandığı durumlarda, bir özniteliğin tüm örneklerini bir diziye yerleştirmek için kullanabilirsiniz <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45af5-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="45af5-127">Örneğin, iki örneği `DeveloperAttribute` aynı sınıfın sınıf düzeyinde uygulanırsa `GetAttribute` , yöntemi her iki öznitelik de bulunan bilgileri görüntüleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="45af5-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="45af5-128">Aynı düzeyde birden fazla öznitelik uygulamak için, özniteliğinin **AllowMultiple** özelliği içinde <xref:System.AttributeUsageAttribute> **true** olarak ayarlanmış şekilde tanımlanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="45af5-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="45af5-129">Aşağıdaki kod örneği, belirli bir sınıftaki tüm örneklere `DeveloperAttribute` başvuran bir dizi oluşturmak için **GetCustomAttributes** yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45af5-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="45af5-130">Tüm özniteliklerin değerleri daha sonra konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45af5-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="45af5-131">Hiçbir öznitelik bulunamazsa, bu kod kullanıcıyı uyarır.</span><span class="sxs-lookup"><span data-stu-id="45af5-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="45af5-132">Aksi halde, her iki örneğinde `DeveloperAttribute` bulunan bilgiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45af5-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="45af5-133">Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="45af5-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="45af5-134"><xref:System.Attribute.GetCustomAttributes%2A> Ve<xref:System.Attribute.GetCustomAttribute%2A> yöntemleri bir sınıfın tamamını aramaz ve bu sınıftaki bir özniteliğin tüm örneklerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="45af5-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="45af5-135">Bunun yerine, tek seferde yalnızca bir belirtilen yöntemi veya üyeyi arar.</span><span class="sxs-lookup"><span data-stu-id="45af5-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="45af5-136">Her üyeye uygulanmış aynı özniteliğe sahip bir sınıfınız varsa ve bu üyelere uygulanan tüm özniteliklerin değerlerini almak istiyorsanız, her yöntemi veya üyeyi **GetCustomAttributes** ve GetCustomAttribute için tek tek sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="45af5-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="45af5-137">Aşağıdaki kod örneği, bir sınıfı parametre olarak alır ve sınıf düzeyinde ve bu `DeveloperAttribute` sınıfın her bir yöntemi üzerinde (daha önceden tanımlanmış) için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="45af5-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="45af5-138">Yöntem düzeyinde veya sınıf düzeyinde `DeveloperAttribute` bir örneği bulunamazsa `GetAttribute` , yöntemi kullanıcıya hiçbir öznitelik bulunamadığını bildirir ve özniteliği içermeyen yöntemin veya sınıfın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45af5-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="45af5-139">Bir öznitelik bulunursa `Name` `Level`,, ve `Reviewed` alanları konsoluna görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45af5-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="45af5-140">Geçirilen sınıftaki bireysel yöntemleri ve üyeleri almak <xref:System.Type> için sınıfının üyelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45af5-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="45af5-141">Bu örnek öncelikle sınıf düzeyi için öznitelik bilgilerini almak üzere **tür** nesnesini sorgular.</span><span class="sxs-lookup"><span data-stu-id="45af5-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="45af5-142">Sonra, yöntem düzeyi <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> için öznitelik bilgilerini almak üzere tüm yöntemlerin örneklerini bir <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> nesne dizisine yerleştirmek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="45af5-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="45af5-143">Ayrıca, <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> Özellik düzeyindeki öznitelikleri denetlemek veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> Oluşturucu düzeyindeki öznitelikleri denetlemek için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45af5-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45af5-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45af5-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="45af5-145">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45af5-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
