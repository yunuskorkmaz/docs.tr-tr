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
ms.openlocfilehash: cc957b345c1e66059551508f73e37e0f6d69f6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399749"
---
# <a name="viewing-type-information"></a><span data-ttu-id="1eeda-102">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1eeda-102">Viewing Type Information</span></span>
<span data-ttu-id="1eeda-103"><xref:System.Type?displayProperty=nameWithType> Sınıfı için yansıma Merkezi.</span><span class="sxs-lookup"><span data-stu-id="1eeda-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="1eeda-104">Ortak dil çalışma zamanı oluşturur **türü** yansıma istediğinde yüklenen bir türü.</span><span class="sxs-lookup"><span data-stu-id="1eeda-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="1eeda-105">Kullanabileceğiniz bir **türü** nesnenin yöntemleri, alanları, özellikleri ve türü hakkında her şeyi öğrenmek için iç içe geçmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="1eeda-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="1eeda-106">Kullanım <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> almak için **türü** , türü veya türleri istediğiniz adına geçirme yüklenmedi derlemelerden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="1eeda-107">Kullanım <xref:System.Type.GetType%2A?displayProperty=nameWithType> almak için **türü** önceden yüklenen derleme nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="1eeda-108">Kullanım <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> modülü edinme **türü** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1eeda-109">Sağlanan ek bilgileri inceleyin ve genel türler ve yöntemleri değiştirmek istiyorsanız, lütfen bkz [yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) ve [nasıl yapılır: inceleyin ve Instantiate genel türleriyansımaile](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="1eeda-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="1eeda-110">Aşağıdaki örnek sözdizimi almak gerekli gösterir <xref:System.Reflection.Assembly> nesne ve bir derlemenin modülü.</span><span class="sxs-lookup"><span data-stu-id="1eeda-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="1eeda-111">Aşağıdaki örnek, alma gösterir **türü** yüklenen derlemesinden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="1eeda-112">Edindikten sonra bir **türü**, bu türün üyeleri hakkında bilgi bulmak birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1eeda-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="1eeda-113">Örneğin, tüm tür üyeleri hakkında arayarak bulabilirsiniz <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> bir dizi edinir yöntemi <xref:System.Reflection.MemberInfo> her geçerli türü üyelerinin açıklayan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="1eeda-114">Üzerinde yöntemleri kullanabilirsiniz **türü** bir veya daha fazla Oluşturucular, yöntemleri, olayları, alanlar veya ada göre belirten özellikleri hakkında bilgi almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1eeda-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="1eeda-115">Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> geçerli sınıfın belirli bir oluşturucu yalıtır.</span><span class="sxs-lookup"><span data-stu-id="1eeda-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="1eeda-116">Varsa bir **türü**, kullanabileceğiniz <xref:System.Type.Module%2A?displayProperty=nameWithType> özelliği bu türü içeren modülü yalıtan bir nesne elde edilir.</span><span class="sxs-lookup"><span data-stu-id="1eeda-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="1eeda-117">Kullanım <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> modülü içeren derlemenin yalıtan bir nesneyi bulmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="1eeda-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="1eeda-118">Türü kullanılarak doğrudan yalıtır derleme edinebilirsiniz <xref:System.Type.Assembly%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1eeda-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="1eeda-119">System.Type ve ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="1eeda-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="1eeda-120">Aşağıdaki örnek, bir sınıf, bu durumda, Oluşturucular listelemek gösterilmiştir <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1eeda-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="1eeda-121">MemberInfo, MethodInfo, FieldInfo ve PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="1eeda-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="1eeda-122">Tür yöntemler, özellikler, olayları ve alanları kullanma hakkında bilgi edinmek <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, veya <xref:System.Reflection.PropertyInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1eeda-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="1eeda-123">Aşağıdaki örnek kullanır **MemberInfo** üye sayısı listelemek için **System.IO.File** sınıfı ve kullandığı <xref:System.Type.IsPublic%2A> özelliği sınıfı görünürlüğünü belirler.</span><span class="sxs-lookup"><span data-stu-id="1eeda-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="1eeda-124">Aşağıdaki örnek, belirtilen üye türü araştırır.</span><span class="sxs-lookup"><span data-stu-id="1eeda-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="1eeda-125">Yansıma bir üyesi yapar **MemberInfo** sınıfı ve türünü listeler.</span><span class="sxs-lookup"><span data-stu-id="1eeda-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="1eeda-126">Aşağıdaki örnek, tüm yansıma kullanır  **\*bilgisi** ile birlikte sınıfları <xref:System.Reflection.BindingFlags> üyeleri bölme tüm üyelerini (Oluşturucular, alanlar, özellikleri, olayları ve yöntemleri) belirtilen sınıf listelemek için statik içine ve örneği kategoriler.</span><span class="sxs-lookup"><span data-stu-id="1eeda-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1eeda-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1eeda-127">See Also</span></span>  
 <xref:System.Reflection.BindingFlags>  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetFields%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.MemberInfo>  
 <xref:System.Reflection.ConstructorInfo>  
 <xref:System.Reflection.MethodInfo>  
 <xref:System.Reflection.FieldInfo>  
 <xref:System.Reflection.EventInfo>  
 <xref:System.Reflection.ParameterInfo>  
 [<span data-ttu-id="1eeda-128">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="1eeda-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
