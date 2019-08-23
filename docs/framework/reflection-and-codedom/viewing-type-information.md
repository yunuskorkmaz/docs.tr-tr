---
title: Tür Bilgilerini Görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e658b2c86eecdbc45a9adde8d28cfb890dd591b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956655"
---
# <a name="viewing-type-information"></a><span data-ttu-id="5cfd8-102">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5cfd8-102">Viewing Type Information</span></span>
<span data-ttu-id="5cfd8-103"><xref:System.Type?displayProperty=nameWithType> Sınıfı, yansıma için bir merkezidir.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="5cfd8-104">Ortak dil çalışma zamanı, yansıma istediğinde yüklenen bir tür için **türü** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="5cfd8-105">Bu tür hakkındaki her şeyi bulmak için bir **tür** nesnesinin yöntemlerini, alanlarını, özelliklerini ve iç içe geçmiş sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="5cfd8-106">Yüklü <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> olmayan <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> derlemelerden, istediğiniz tür veya türlerin adını geçirerek **tür** nesneleri almak için veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="5cfd8-107">Zaten <xref:System.Type.GetType%2A?displayProperty=nameWithType> yüklü olan bir derlemeden **tür** nesnelerini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="5cfd8-108">Modül <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> türü <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> nesneleri almak için ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cfd8-109">Genel türleri ve yöntemleri incelemek ve işlemek istiyorsanız, lütfen [yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) bölümünde sunulan ek bilgilere ve [nasıl yapılır: Yansıma](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)ile genel türleri Inceleyin ve örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="5cfd8-110">Aşağıdaki örnek, bir derlemenin <xref:System.Reflection.Assembly> nesne ve modülünü almak için gereken söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="5cfd8-111">Aşağıdaki örnekte, yüklü bir derlemeden **tür** nesnelerinin alınması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="5cfd8-112">Bir **türü**edindiğinizde, bu türden Üyeler hakkında bilgi bulmanın birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="5cfd8-113">Örneğin, geçerli türdeki üyelerin her birini açıklayan bir <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.MemberInfo> nesne dizisi elde eden yöntemini çağırarak tüm tür üyeleri hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="5cfd8-114">Ayrıca, bir veya daha fazla Oluşturucu, yöntem, olay, alan veya ada göre belirttiğiniz özellikler hakkında bilgi almak için **tür** sınıfındaki yöntemleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="5cfd8-115">Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> geçerli sınıfın belirli bir oluşturucusunu kapsüller.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="5cfd8-116">Bir **tür**varsa, bu türü içeren modülü kapsülleyen bir <xref:System.Type.Module%2A?displayProperty=nameWithType> nesne almak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="5cfd8-117">Modülünü içeren derlemeyi kapsülleyen bir nesneyi bulmak için özelliğinikullanın.<xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5cfd8-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="5cfd8-118"><xref:System.Type.Assembly%2A?displayProperty=nameWithType> Özelliğini kullanarak türü sarmalayan derlemeyi doğrudan elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="5cfd8-119">System. Type ve ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="5cfd8-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="5cfd8-120">Aşağıdaki örnek, bu <xref:System.String> örnekte sınıfı için oluşturucuların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="5cfd8-121">MemberInfo, MethodInfo, FieldInfo ve PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="5cfd8-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="5cfd8-122">, <xref:System.Reflection.MemberInfo>, Veya <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo>nesnelerini kullanarak türün yöntemleri, özellikleri, olayları ve alanları hakkında bilgi edinin. <xref:System.Reflection.PropertyInfo></span><span class="sxs-lookup"><span data-stu-id="5cfd8-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="5cfd8-123">Aşağıdaki örnek, **System. IO. File** sınıfındaki üye sayısını listelemek için <xref:System.Type.IsPublic%2A> **MemberInfo** kullanır ve sınıfının görünürlüğünü öğrenmek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="5cfd8-124">Aşağıdaki örnek, belirtilen üyenin türünü araştırır.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="5cfd8-125">Bir **MemberInfo** için bir üye üzerinde yansıma gerçekleştirir ve türünü listeler.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="5cfd8-126">Aşağıdaki örnek, belirtilen sınıfın tüm üyelerini (oluşturucular, alanlar <xref:System.Reflection.BindingFlags> , özellikler, olaylar ve Yöntemler) listelemek ve üyeleri statik ve örneğe bölmek için ile birlikte tüm yansıma  **\*bilgileri** sınıflarını kullanır kategorisine.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5cfd8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cfd8-127">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="5cfd8-128">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5cfd8-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
