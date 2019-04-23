---
title: System.String Yöntemleri
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 3a7b45f27441d889524f5055eb5c6a3b06937bd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160504"
---
# <a name="systemstring-methods"></a><span data-ttu-id="b96de-102">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b96de-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b96de-103">şunları desteklemez <xref:System.String> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b96de-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="b96de-104">System.String yöntemleri genel desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b96de-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="b96de-105">Desteklenmeyen <xref:System.String> genel yöntemler:</span><span class="sxs-lookup"><span data-stu-id="b96de-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="b96de-106">Kültüre duyarlı aşırı yüklemeler (ele yöntemleri bir `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="b96de-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="b96de-107">Alabilir veya üretmek yöntemleri bir `char` dizi.</span><span class="sxs-lookup"><span data-stu-id="b96de-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="b96de-108">Desteklenmeyen System.String statik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b96de-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="b96de-109">Desteklenmeyen System.String statik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b96de-109">Unsupported System.String Static Methods</span></span>|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="b96de-110">Desteklenmeyen System.String statik olmayan metotlar</span><span class="sxs-lookup"><span data-stu-id="b96de-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="b96de-111">Desteklenmeyen System.String statik olmayan metotlar</span><span class="sxs-lookup"><span data-stu-id="b96de-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="b96de-112">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="b96de-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="b96de-113">Sorgular, sunucu üzerinde etkin olabilir ve bu nedenle varsayılan olarak kültüre duyarlı ve büyük küçük harf duyarsız karşılaştırmalarını sağlar, SQL Server harmanlamaları için hesap kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b96de-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="b96de-114">Bu davranış, varsayılan, .NET Framework'ün büyük/küçük harfe semantiği farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b96de-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="b96de-115">Zaman `LastIndexOf` döndürür ya da dize 0 `NULL` veya bulunan konumu 0'dır.</span><span class="sxs-lookup"><span data-stu-id="b96de-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="b96de-116">Beklenmeyen sonuçlar birleştirme ya da sabit uzunluklu dizeler üzerinde başka işlemler döndürülmesi (`CHAR`, `NCHAR`), bu tür, veritabanında uygulanan doldurma otomatik olarak sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="b96de-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="b96de-117">Çünkü birçok yöntem gibi `Replace`, `ToLower`, `ToUpper`ve geçerli çeviri için sahip karakter dizin oluşturucu `TEXT` veya `NTEXT` sütunları ve XML `SqlExceptions` normalde çevrilmiş ortaya.</span><span class="sxs-lookup"><span data-stu-id="b96de-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="b96de-118">Bu davranışı Bu türleri için kabul edilebilir olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b96de-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="b96de-119">Ancak, tüm dize işlemleri için ortak dil çalışma zamanı (CLR) semantiği eşleşmelidir `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, ve `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="b96de-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96de-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b96de-120">See also</span></span>

- [<span data-ttu-id="b96de-121">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b96de-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
