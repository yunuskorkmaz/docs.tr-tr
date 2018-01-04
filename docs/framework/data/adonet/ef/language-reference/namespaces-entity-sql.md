---
title: "Ad alanları (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f97b28bce20fa71f82942fa5f123d7c2ac6616a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="6fd64-102">Ad alanları (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="6fd64-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6fd64-103">Tür adları, varlık kümeleri, İşlevler vb. gibi genel tanımlayıcıları için ad çakışmalarını önlemek için ad alanları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="6fd64-103"> introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="6fd64-104">Ad alanı desteği [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ad alanı desteği benzer [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6fd64-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6fd64-105">iki tür yan tümcesi sağlar: tam ad alanları (burada daha kısa bir diğer ad sağlanır ad alanı için) ve nitelenmemiş ad alanları, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="6fd64-105"> provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="6fd64-106">Ad çözümleme kuralları</span><span class="sxs-lookup"><span data-stu-id="6fd64-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="6fd64-107">Bir tanımlayıcı yerel kapsamlarda çözümlenemiyorsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] genel kapsamlarda (ad) adı bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="6fd64-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6fd64-108">İlk tanımlayıcı (önek) eşleşmesi tam ad alanlarından birini ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="6fd64-108"> first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="6fd64-109">Bir eşleşme varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanı tanımlayıcıda kalan çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="6fd64-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="6fd64-110">Eşleşme bulunursa, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="6fd64-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="6fd64-111">Ardından, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (giriş bölümünde belirtilen) tüm nitelenmemiş ad tanımlayıcısı için arama dener.</span><span class="sxs-lookup"><span data-stu-id="6fd64-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="6fd64-112">Tanımlayıcı tam olarak bir ad alanında bulunabilir, bu konuma döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6fd64-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="6fd64-113">Birden fazla ad alanı bu tanımlayıcı için bir eşleşme varsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="6fd64-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="6fd64-114">Hiçbir ad alanı için tanımlayıcı, tanımlanabilir varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adını sonraki dışa doğru kapsam geçirir ( <xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesnesi) aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="6fd64-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="6fd64-115">.NET Framework arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="6fd64-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="6fd64-116">İçinde [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], kısmen nitelenmiş ad alanlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fd64-116">In the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6fd64-117">Bu izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="6fd64-117"> does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="6fd64-118">ADO.NET kullanımı</span><span class="sxs-lookup"><span data-stu-id="6fd64-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="6fd64-119">Sorguları ADO.NET ifade <xref:System.Data.Common.DbCommand> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6fd64-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="6fd64-120"><xref:System.Data.Common.DbCommand>nesneleri üzerinden oluşturulabilen <xref:System.Data.Common.DbConnection> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6fd64-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="6fd64-121">Ad alanları bir parçası olarak da belirtilebilir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6fd64-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="6fd64-122">Varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tanımlayıcısı çözümlenemiyor sorguyla kendisi, dış ad alanları (benzer kurallar göre) sıklığının.</span><span class="sxs-lookup"><span data-stu-id="6fd64-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd64-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fd64-123">See Also</span></span>  
 [<span data-ttu-id="6fd64-124">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6fd64-124">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="6fd64-125">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6fd64-125">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
