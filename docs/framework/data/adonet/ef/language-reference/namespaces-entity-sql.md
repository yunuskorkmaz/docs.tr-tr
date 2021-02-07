---
description: 'Hakkında daha fazla bilgi edinin: ad alanları (Entity SQL)'
title: Ad alanları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 70ef0021c3015fd661b42becb5371dcfd958f20f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696561"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="c4d69-103">Ad alanları (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c4d69-103">Namespaces (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c4d69-104">tür adları, varlık kümeleri, işlevler gibi genel Tanımlayıcılarla ilgili ad çakışmalarını önlemek için ad alanlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c4d69-104">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="c4d69-105">İçindeki ad alanı desteği [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .NET Framework ad alanı desteğine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c4d69-105">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c4d69-106">, aşağıdaki örnekte gösterildiği gibi, USING yan tümcesinin iki biçimini sağlar: nitelenmiş ad alanları (ad alanı için daha kısa bir diğer ad) ve nitelenmemiş ad alanları.</span><span class="sxs-lookup"><span data-stu-id="c4d69-106">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="c4d69-107">Ad çözümleme kuralları</span><span class="sxs-lookup"><span data-stu-id="c4d69-107">Name Resolution Rules</span></span>  

 <span data-ttu-id="c4d69-108">Bir tanımlayıcı yerel kapsamlardan çözülemezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adı Genel kapsamlar (ad alanları) içinde bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4d69-108">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c4d69-109">İlk olarak tanımlayıcı (önek) olarak nitelenmiş ad alanlarından birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="c4d69-109">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="c4d69-110">Bir eşleşme varsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanındaki tanımlayıcının geri kalanını çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4d69-110">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="c4d69-111">Eşleşme bulunmazsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c4d69-111">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="c4d69-112">Daha sonra [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcı için tüm nitelenmemiş ad alanlarını (giriş durumunda belirtilen) aramayı dener.</span><span class="sxs-lookup"><span data-stu-id="c4d69-112">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="c4d69-113">Tanımlayıcı tam olarak bir ad alanında konumlandırılabilir ise, o konum döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4d69-113">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="c4d69-114">Birden fazla ad alanının bu tanımlayıcı için bir eşleşmesi varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c4d69-114">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="c4d69-115">Tanımlayıcı için bir ad alanı tanımlanamıyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki örnekte gösterildiği gibi, adı bir sonraki dışarı kapsama ( <xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesne) geçirir:</span><span class="sxs-lookup"><span data-stu-id="c4d69-115">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="c4d69-116">.NET Framework farklılıklar</span><span class="sxs-lookup"><span data-stu-id="c4d69-116">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="c4d69-117">.NET Framework kısmen nitelenmiş ad alanlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4d69-117">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c4d69-118">Buna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c4d69-118">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="c4d69-119">ADO.NET kullanımı</span><span class="sxs-lookup"><span data-stu-id="c4d69-119">ADO.NET Usage</span></span>  

 <span data-ttu-id="c4d69-120">Sorgular ADO.NET nesneleri aracılığıyla ifade edilir <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="c4d69-120">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="c4d69-121"><xref:System.Data.Common.DbCommand> nesneler nesneler üzerinde oluşturulabilir <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="c4d69-121"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="c4d69-122">Ad alanları ve nesnelerinin bir parçası olarak da belirtilebilir <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="c4d69-122">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="c4d69-123">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Sorgunun içindeki bir tanımlayıcıyı çözümleyemezse dış ad alanları araştırılır (benzer kurallara göre).</span><span class="sxs-lookup"><span data-stu-id="c4d69-123">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d69-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d69-124">See also</span></span>

- [<span data-ttu-id="c4d69-125">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4d69-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c4d69-126">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4d69-126">Entity SQL Overview</span></span>](entity-sql-overview.md)
