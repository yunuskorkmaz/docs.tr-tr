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
ms.openlocfilehash: 8873b4938f654213bd659631175ba4526a35dcc3
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957337"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="22364-102">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="22364-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="22364-103">Özel bir özniteliğin alınması basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="22364-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="22364-104">İlk olarak, almak istediğiniz özniteliğin bir örneğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="22364-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="22364-105">Ardından, yeni özniteliğini almak istediğiniz özniteliğin değerine başlatmak için <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="22364-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="22364-106">Yeni özniteliği başlatıldıktan sonra, değerlerini almak için özelliklerini kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="22364-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="22364-107">Bu konu, yürütme bağlamına yüklenen kodun özniteliklerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="22364-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="22364-108">Yalnızca yansıma bağlamına yüklenen kodun özniteliklerini almak için <xref:System.Reflection.CustomAttributeData> sınıfını, [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)bölümünde gösterildiği gibi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="22364-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="22364-109">Bu bölümde özniteliklerin alınması için aşağıdaki yollar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="22364-109">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="22364-110">Bir özniteliğin tek bir örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="22364-111">Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="22364-112">Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="22364-113">Bir özniteliğin tek bir örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="22364-114">Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanan) sınıf düzeyindeki `MainApp` sınıfına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="22364-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="22364-115">@No__t-0 yöntemi, konsola görüntülemeden önce sınıf düzeyinde @no__t içinde depolanan değerleri almak için **GetCustomAttribute** kullanır.</span><span class="sxs-lookup"><span data-stu-id="22364-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="22364-116">Bu program yürütüldüğünde aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22364-116">This program displays the following text when executed.</span></span>  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="22364-117">Öznitelik bulunamazsa **GetCustomAttribute** yöntemi `MyAttribute` değerini null bir değere başlatır.</span><span class="sxs-lookup"><span data-stu-id="22364-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="22364-118">Bu örnek, böyle bir örnek için `MyAttribute` ' i denetler ve bir öznitelik bulunmazsa kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="22364-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="22364-119">@No__t-0 sınıf kapsamında bulunmazsa, aşağıdaki ileti konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22364-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```console  
The attribute was not found.   
```  
  
 <span data-ttu-id="22364-120">Bu örnek, öznitelik tanımının geçerli ad alanında olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="22364-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="22364-121">Geçerli ad alanında değilse öznitelik tanımının bulunduğu ad alanını içeri aktarmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22364-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="22364-122">Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="22364-123">Önceki örnekte, incelenecek sınıf ve bulunacak özel öznitelik <xref:System.Attribute.GetCustomAttribute%2A> ' a geçirilir.</span><span class="sxs-lookup"><span data-stu-id="22364-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="22364-124">Bu kod, sınıf düzeyinde bir özniteliğin yalnızca bir örneği uygulandığında iyi bir şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="22364-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="22364-125">Ancak, aynı sınıf düzeyinde bir özniteliğin birden çok örneği uygulanırsa **GetCustomAttribute** yöntemi tüm bilgileri almaz.</span><span class="sxs-lookup"><span data-stu-id="22364-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="22364-126">Aynı özniteliğin birden fazla örneğinin aynı kapsama uygulandığı durumlarda, bir özniteliğin tüm örneklerini bir diziye yerleştirmek için <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> ' ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22364-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="22364-127">Örneğin, `DeveloperAttribute` ' ın iki örneği aynı sınıfın sınıf düzeyinde uygulanırsa, `GetAttribute` yöntemi her iki özniteliklerde bulunan bilgileri görüntüleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="22364-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="22364-128">Aynı düzeyde birden fazla öznitelik uygulamak için, özniteliğin <xref:System.AttributeUsageAttribute> ' de **true** olarak ayarlanmış **AllowMultiple** özelliği ile tanımlanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22364-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="22364-129">Aşağıdaki kod örneği, belirli bir sınıftaki `DeveloperAttribute` ' in tüm örneklerine başvuran bir dizi oluşturmak için **GetCustomAttributes** yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22364-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="22364-130">Tüm özniteliklerin değerleri daha sonra konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22364-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="22364-131">Hiçbir öznitelik bulunamazsa, bu kod kullanıcıyı uyarır.</span><span class="sxs-lookup"><span data-stu-id="22364-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="22364-132">Aksi takdirde, `DeveloperAttribute` ' ın her iki örneğinde bulunan bilgiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22364-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="22364-133">Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma</span><span class="sxs-lookup"><span data-stu-id="22364-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="22364-134">@No__t-0 ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri bir sınıfın tamamını aramaz ve bu sınıftaki bir özniteliğin tüm örneklerini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="22364-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="22364-135">Bunun yerine, tek seferde yalnızca bir belirtilen yöntemi veya üyeyi arar.</span><span class="sxs-lookup"><span data-stu-id="22364-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="22364-136">Her üyeye uygulanmış aynı özniteliğe sahip bir sınıfınız varsa ve bu üyelere uygulanan tüm özniteliklerin değerlerini almak istiyorsanız, her yöntemi veya üyeyi **GetCustomAttributes** ve GetCustomAttribute için tek tek sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="22364-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="22364-137">Aşağıdaki kod örneği bir sınıfı parametre olarak alır ve sınıf düzeyinde ve bu sınıfın her bir yöntemi üzerinde `DeveloperAttribute` (daha önceden tanımlanmış) arar.</span><span class="sxs-lookup"><span data-stu-id="22364-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="22364-138">Yöntem düzeyinde veya sınıf düzeyinde `DeveloperAttribute` ' ın bir örneği bulunmazsa, `GetAttribute` yöntemi kullanıcıya hiçbir öznitelik bulunamadığını bildirir ve özniteliği içermeyen yöntemin veya sınıfın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22364-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="22364-139">Bir öznitelik bulunursa, `Name`, `Level` ve `Reviewed` alanları konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22364-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="22364-140">Geçirilen sınıftaki tek tek yöntemleri ve üyeleri almak için <xref:System.Type> sınıfının üyelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22364-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="22364-141">Bu örnek öncelikle sınıf düzeyi için öznitelik bilgilerini almak üzere **tür** nesnesini sorgular.</span><span class="sxs-lookup"><span data-stu-id="22364-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="22364-142">Sonra, yöntem düzeyi için öznitelik bilgilerini almak üzere tüm yöntemlerin örneklerini bir <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> nesneleri dizisine yerleştirmek için <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> kullanır.</span><span class="sxs-lookup"><span data-stu-id="22364-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="22364-143">Ayrıca, özellik düzeyindeki öznitelikleri denetlemek için <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> yöntemini veya Oluşturucu düzeyindeki öznitelikleri denetlemek için-1 ' i @no__t de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22364-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22364-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22364-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="22364-145">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="22364-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
