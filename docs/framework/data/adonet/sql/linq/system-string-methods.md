---
title: System.String yöntemleri
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: a6a8ce897cc6ac15f3452d2ba98b1b12bee544c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360076"
---
# <a name="systemstring-methods"></a><span data-ttu-id="46f56-102">System.String yöntemleri</span><span class="sxs-lookup"><span data-stu-id="46f56-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="46f56-103"> Aşağıdaki desteklemiyor <xref:System.String> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="46f56-103"> does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="46f56-104">System.String yöntemleri genel desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="46f56-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="46f56-105">Desteklenmeyen <xref:System.String> genel yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="46f56-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="46f56-106">Kültüre duyarlı aşırı (ele yöntemleri bir `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="46f56-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="46f56-107">Alabilir veya üretmek yöntemleri bir `char` dizi.</span><span class="sxs-lookup"><span data-stu-id="46f56-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="46f56-108">Desteklenmeyen System.String statik yöntemler</span><span class="sxs-lookup"><span data-stu-id="46f56-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="46f56-109">Desteklenmeyen System.String statik yöntemler</span><span class="sxs-lookup"><span data-stu-id="46f56-109">Unsupported System.String Static Methods</span></span>|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="46f56-110">Desteklenmeyen System.String statik olmayan yöntemleri</span><span class="sxs-lookup"><span data-stu-id="46f56-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="46f56-111">Desteklenmeyen System.String statik olmayan yöntemleri</span><span class="sxs-lookup"><span data-stu-id="46f56-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="46f56-112">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="46f56-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="46f56-113">Sorguları sunucu üzerinde etkin olabilir ve bu nedenle varsayılan kültüre duyarlı, büyük küçük harf duyarsız karşılaştırma sağlar SQL Server harmanlamaları hesabı değil.</span><span class="sxs-lookup"><span data-stu-id="46f56-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="46f56-114">Bu davranış varsayılan olarak .NET Framework'ün büyük küçük harfe duyarlı semantiği farklıdır.</span><span class="sxs-lookup"><span data-stu-id="46f56-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="46f56-115">Zaman `LastIndexOf` döndürür 0, her iki dize `NULL` veya 0 bulunan konumdur.</span><span class="sxs-lookup"><span data-stu-id="46f56-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="46f56-116">Beklenmeyen sonuçlara neden olabilir döndürülen birleştirme veya sabit uzunluklu dizeler üzerinde başka işlemler (`CHAR`, `NCHAR`), bu türlerinin veritabanında uygulanan doldurma otomatik olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="46f56-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="46f56-117">İçin birçok yöntem gibi `Replace`, `ToLower`, `ToUpper`ve hiçbir geçerli çeviri sahip karakter dizin oluşturucu `TEXT` veya `NTEXT` sütunlar ve XML `SqlExceptions` normalde çevrilen ortaya.</span><span class="sxs-lookup"><span data-stu-id="46f56-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="46f56-118">Bu davranış bu türleri için kabul edilebilir olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="46f56-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="46f56-119">Ancak, tüm dize işlemleri için ortak dil çalışma zamanı (CLR) semantiği eşleşmelidir `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, ve `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="46f56-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f56-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46f56-120">See Also</span></span>  
 [<span data-ttu-id="46f56-121">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="46f56-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
