---
title: "Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28203dc428db6a2dd06e9c1e85b64ef80e81ffbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="type-equivalence-and-embedded-interop-types"></a><span data-ttu-id="5cda8-102">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="5cda8-102">Type Equivalence and Embedded Interop Types</span></span>
<span data-ttu-id="5cda8-103">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], doğrudan birlikte çalışma derlemeleri COM türleri için tür bilgisi almak Yönetilen derlemeler gerektirmek yerine Yönetilen derlemeler içine COM türleri için tür bilgilerini katıştırma ortak dil çalışma zamanı destekler.</span><span class="sxs-lookup"><span data-stu-id="5cda8-103">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the common language runtime supports embedding type information for COM types directly into managed assemblies, instead of requiring the managed assemblies to obtain type information for COM types from interop assemblies.</span></span> <span data-ttu-id="5cda8-104">Gömülü tür bilgileri yalnızca türleri ve gerçekte yönetilen derlemesi tarafından kullanılan üyeler içerdiği için iki Yönetilen derlemeler çok farklı görünümleri aynı COM türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cda8-104">Because the embedded type information includes only the types and members that are actually used by a managed assembly, two managed assemblies might have very different views of the same COM type.</span></span> <span data-ttu-id="5cda8-105">Her yönetilen derleme farklı bir sahip <xref:System.Type> COM türünün kendi görünümünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5cda8-105">Each managed assembly has a different <xref:System.Type> object to represent its view of the COM type.</span></span> <span data-ttu-id="5cda8-106">Ortak dil çalışma zamanı tür denkliği arabirimleri, yapıları, numaralandırmalar ve temsilciler için bu farklı görünümleri arasında destekler.</span><span class="sxs-lookup"><span data-stu-id="5cda8-106">The common language runtime supports type equivalence between these different views for interfaces, structures, enumerations, and delegates.</span></span>  
  
 <span data-ttu-id="5cda8-107">Tür denkliği yönetilen alıcı derlemesindeki türü bir yönetilen derleme başka bir uygun atanabilecek geçirilen bir COM nesnesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5cda8-107">Type equivalence means that a COM object that is passed from one managed assembly to another can be cast to the appropriate managed type in the receiving assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cda8-108">Uygulamaları ile birlikte çalışma derlemeleri dağıtmak gerekli olmadığından, uygulamaların dağıtımını ve COM bileşenlerini kullanmak eklentiler tür eşdeğerliği ve katıştırılmış birlikte çalışma türlerini basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="5cda8-108">Type equivalence and embedded interop types simplify the deployment of applications and add-ins that use COM components, because it is not necessary to deploy interop assemblies with the applications.</span></span> <span data-ttu-id="5cda8-109">Paylaşılan COM bileşenlerini geliştiricileri yine .NET Framework'ün önceki sürümleri tarafından kullanılacak bileşenleri istiyorsanız birincil birlikte çalışma derlemeleri (PIA) oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cda8-109">Developers of shared COM components still have to create primary interop assemblies (PIAs) if they want their components to be used by earlier versions of the .NET Framework.</span></span>  
  
## <a name="type-equivalence"></a><span data-ttu-id="5cda8-110">Tür denkliği</span><span class="sxs-lookup"><span data-stu-id="5cda8-110">Type Equivalence</span></span>  
 <span data-ttu-id="5cda8-111">COM türlerinin eşdeğer arabirimleri, yapıları, numaralandırmalar ve temsilciler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5cda8-111">Equivalence of COM types is supported for interfaces, structures, enumerations, and delegates.</span></span> <span data-ttu-id="5cda8-112">Aşağıdakilerin tümü doğruysa, COM türlerini eşdeğer olarak nitelemek:</span><span class="sxs-lookup"><span data-stu-id="5cda8-112">COM types qualify as equivalent if all of the following are true:</span></span>  
  
-   <span data-ttu-id="5cda8-113">, Hem arabirimleri veya hem yapıları veya hem numaralandırmalar veya her iki temsilciler türleridir.</span><span class="sxs-lookup"><span data-stu-id="5cda8-113">The types are both interfaces, or both structures, or both enumerations, or both delegates.</span></span>  
  
-   <span data-ttu-id="5cda8-114">Türleri, sonraki bölümde açıklandığı gibi aynı kimliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="5cda8-114">The types have the same identity, as described in the next section.</span></span>  
  
-   <span data-ttu-id="5cda8-115">Bölümünde açıklandığı gibi her iki tür denkliği için uygun olan [COM türlerinde işaretleme tür denkliği](#type_equiv) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5cda8-115">Both types are eligible for type equivalence, as described in the [Marking COM Types for Type Equivalence](#type_equiv) section.</span></span>  
  
### <a name="type-identity"></a><span data-ttu-id="5cda8-116">Tür kimliği</span><span class="sxs-lookup"><span data-stu-id="5cda8-116">Type Identity</span></span>  
 <span data-ttu-id="5cda8-117">İki tür kendi kapsamları ve kimlikler, diğer bir deyişle, eşleştiğinde her varsa aynı kimliğe sahip belirlenir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliğine ve iki özelliklere sahip eşleşen <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ve <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5cda8-117">Two types are determined to have the same identity when their scopes and identities match, in other words, if they each have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, and the two attributes have matching <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> and <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> properties.</span></span> <span data-ttu-id="5cda8-118">Karşılaştırma için <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> büyük küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cda8-118">The comparison for <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> is case-insensitive.</span></span>  
  
 <span data-ttu-id="5cda8-119">Bir tür yoksa <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği veya varsa bir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> belirtmiyor kapsamı ve tanımlayıcı olarak türü özniteliği hala sayılabileceğini için eşdeğer gibi:</span><span class="sxs-lookup"><span data-stu-id="5cda8-119">If a type does not have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, or if it has a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute that does not specify scope and identifier, the type can still be considered for equivalence as follows:</span></span>  
  
-   <span data-ttu-id="5cda8-120">Arabirimler, değeri için <xref:System.Runtime.InteropServices.GuidAttribute> yerine kullanılan <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği (ad alanı dahil diğer bir deyişle, tür adını) yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5cda8-120">For interfaces, the value of the <xref:System.Runtime.InteropServices.GuidAttribute> is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property (that is, the type name, including the namespace) is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="5cda8-121">Yapılar, numaralandırmalar ve Temsilciler <xref:System.Runtime.InteropServices.GuidAttribute> içeren derlemenin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5cda8-121">For structures, enumerations, and delegates, the <xref:System.Runtime.InteropServices.GuidAttribute> of the containing assembly is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> property.</span></span>  
  
<a name="type_equiv"></a>   
### <a name="marking-com-types-for-type-equivalence"></a><span data-ttu-id="5cda8-122">COM türleri tür denkliği için işaretleme</span><span class="sxs-lookup"><span data-stu-id="5cda8-122">Marking COM Types for Type Equivalence</span></span>  
 <span data-ttu-id="5cda8-123">Bir tür için iki yolla tür denkliği uygun olarak işaretleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5cda8-123">You can mark a type as eligible for type equivalence in two ways:</span></span>  
  
-   <span data-ttu-id="5cda8-124">Uygulama <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> öznitelik türü.</span><span class="sxs-lookup"><span data-stu-id="5cda8-124">Apply the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute to the type.</span></span>  
  
-   <span data-ttu-id="5cda8-125">Türünün bir COM alma türü olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5cda8-125">Make the type a COM import type.</span></span> <span data-ttu-id="5cda8-126">Bu arabirim COM alma türü ise <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cda8-126">An interface is a COM import type if it has the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute.</span></span> <span data-ttu-id="5cda8-127">İçinde tanımlanmış derleme bir arabirim, yapısı, numaralandırma veya temsilci COM alma türü ise <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cda8-127">An interface, structure, enumeration, or delegate is a COM import type if the assembly in which it is defined has the <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cda8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cda8-128">See Also</span></span>  
 <xref:System.Type.IsEquivalentTo%2A>  
 [<span data-ttu-id="5cda8-129">Yönetilen kodda COM türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="5cda8-129">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="5cda8-130">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="5cda8-130">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
