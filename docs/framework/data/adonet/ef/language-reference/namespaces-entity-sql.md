---
title: Ad alanları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319555"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="5dedb-102">Ad alanları (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5dedb-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5dedb-103">, tür adları, varlık kümeleri, işlevler gibi genel tanımlayıcılara ad çakışmalarını önlemek için ad alanlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5dedb-103">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="5dedb-104">@No__t-0 ' daki ad alanı desteği, .NET Framework ad alanı desteğiyle benzerdir.</span><span class="sxs-lookup"><span data-stu-id="5dedb-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5dedb-105">, aşağıdaki örnekte gösterildiği gibi, USING yan tümcesinin iki biçimini sağlar: nitelenmiş ad alanları (ad alanı için daha kısa bir diğer ad) ve nitelenmemiş ad alanları.</span><span class="sxs-lookup"><span data-stu-id="5dedb-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="5dedb-106">Ad çözümleme kuralları</span><span class="sxs-lookup"><span data-stu-id="5dedb-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="5dedb-107">Bir tanımlayıcı yerel kapsamlardan çözülemezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Genel kapsamlar (ad alanları) içinde adı bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dedb-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5dedb-108">, önce nitelenmiş ad alanlarından biriyle tanımlayıcı (ön ek) ile eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dedb-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="5dedb-109">Bir eşleşme varsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanındaki tanımlayıcının geri kalanını çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dedb-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="5dedb-110">Eşleşme bulunmazsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5dedb-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="5dedb-111">Sonra, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcı için tüm nitelenmemiş ad alanlarını (giriş durumunda belirtilen) aramaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dedb-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="5dedb-112">Tanımlayıcı tam olarak bir ad alanında konumlandırılabilir ise, o konum döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5dedb-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="5dedb-113">Birden fazla ad alanının bu tanımlayıcı için bir eşleşmesi varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5dedb-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="5dedb-114">Tanımlayıcı için bir ad alanı tanımlanamıyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aşağıdaki örnekte gösterildiği gibi, adı bir sonraki dışarı kapsama geçirir (<xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesnesi):</span><span class="sxs-lookup"><span data-stu-id="5dedb-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="5dedb-115">.NET Framework farklılıklar</span><span class="sxs-lookup"><span data-stu-id="5dedb-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="5dedb-116">.NET Framework kısmen nitelenmiş ad alanlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5dedb-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5dedb-117">buna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5dedb-117">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="5dedb-118">ADO.NET kullanımı</span><span class="sxs-lookup"><span data-stu-id="5dedb-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="5dedb-119">Sorgular, ADO.NET <xref:System.Data.Common.DbCommand> nesneleri aracılığıyla ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="5dedb-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="5dedb-120"><xref:System.Data.Common.DbCommand> nesneleri <xref:System.Data.Common.DbConnection> nesneler üzerinde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5dedb-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="5dedb-121">Ad alanları <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesnelerinin bir parçası olarak da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="5dedb-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="5dedb-122">@No__t-0 sorgunun içindeki bir tanımlayıcıyı çözümleyemezse dış ad alanları araştırılır (benzer kurallara göre).</span><span class="sxs-lookup"><span data-stu-id="5dedb-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dedb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dedb-123">See also</span></span>

- [<span data-ttu-id="5dedb-124">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5dedb-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5dedb-125">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5dedb-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
