---
title: System.String Yöntemleri
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 44d32ed1000ca49d9fc29ffcde4506b44fc975b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155672"
---
# <a name="systemstring-methods"></a><span data-ttu-id="960c0-102">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="960c0-102">System.String Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="960c0-103">Aşağıdaki <xref:System.String> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="960c0-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="960c0-104">Genel olarak desteklenmeyen System. String yöntemleri</span><span class="sxs-lookup"><span data-stu-id="960c0-104">Unsupported System.String Methods in General</span></span>  

 <span data-ttu-id="960c0-105"><xref:System.String>Genel olarak desteklenmeyen Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="960c0-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="960c0-106">Kültüre duyarlı aşırı yüklemeler (bir alma yöntemi `CultureInfo`  /  `StringComparison`  /  `IFormatProvider` ).</span><span class="sxs-lookup"><span data-stu-id="960c0-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="960c0-107">Dizi alan veya üreten Yöntemler `char` .</span><span class="sxs-lookup"><span data-stu-id="960c0-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="960c0-108">Desteklenmeyen System. String statik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="960c0-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="960c0-109">Desteklenmeyen System. String statik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="960c0-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="960c0-110">Desteklenmeyen System. String statik olmayan Yöntemler</span><span class="sxs-lookup"><span data-stu-id="960c0-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="960c0-111">Desteklenmeyen System. String statik olmayan Yöntemler</span><span class="sxs-lookup"><span data-stu-id="960c0-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="960c0-112">.NET farklılıkları</span><span class="sxs-lookup"><span data-stu-id="960c0-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="960c0-113">Sorgular, sunucuda geçerli olabilecek SQL Server harmanlamaları yapmaz ve bu nedenle varsayılan olarak kültüre duyarlı, büyük/küçük harfe duyarsız karşılaştırmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="960c0-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="960c0-114">Bu davranış, .NET Framework varsayılan, büyük/küçük harfe duyarlı anlamlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="960c0-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="960c0-115">`LastIndexOf`0 döndürdüğünde, dize `NULL` ya da bulunan konum 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="960c0-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="960c0-116">`CHAR` `NCHAR` Bu türler otomatik olarak veritabanında doldurma işlemi yaptığından, birleştirme işleminden veya sabit uzunluklu dizelerde (,) başka işlemlerden beklenmedik sonuçlar döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="960c0-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="960c0-117">,, Ve gibi birçok yöntem `Replace` , `ToLower` `ToUpper` veya sütunları ve XML için geçerli bir çeviri olmadığından, `TEXT` `NTEXT` `SqlExceptions` normal şekilde çevrilmişse oluşur.</span><span class="sxs-lookup"><span data-stu-id="960c0-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="960c0-118">Bu davranış, bu türler için kabul edilebilir olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="960c0-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="960c0-119">Ancak, tüm dize işlemleri,,, ve için ortak dil çalışma zamanı (CLR) semantiğine uymalıdır `VARCHAR` `NVARCHAR` `VARCHAR(max)` `NVARCHAR(max)` .</span><span class="sxs-lookup"><span data-stu-id="960c0-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960c0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="960c0-120">See also</span></span>

- [<span data-ttu-id="960c0-121">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="960c0-121">Data Types and Functions</span></span>](data-types-and-functions.md)
