---
title: .NET Framework türlerini dizelere dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59e288a756a022763bae2235964a8b25a9d72bd1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46538196"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="8f4a2-102">.NET Framework türlerini dizelere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8f4a2-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="8f4a2-103">.NET Framework türü bir dizeye dönüştürmek istiyorsanız kullanmanız **ToString** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="8f4a2-104">**ToString** yöntemi geçirilen tür dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="8f4a2-105">Aşağıdaki tablo XML Şeması (XSD) belirtimlerine eşleyen biçiminde bir dize döndürecek .NET Framework türleri listeler.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="8f4a2-106">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="8f4a2-106">.NET Framework type</span></span>|<span data-ttu-id="8f4a2-107">Döndürülen dize türü</span><span class="sxs-lookup"><span data-stu-id="8f4a2-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="8f4a2-108">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8f4a2-108">Boolean</span></span>|<span data-ttu-id="8f4a2-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="8f4a2-109">"true", "false"</span></span>|  
|<span data-ttu-id="8f4a2-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="8f4a2-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="8f4a2-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="8f4a2-111">"INF"</span></span>|  
|<span data-ttu-id="8f4a2-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="8f4a2-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="8f4a2-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="8f4a2-113">"-INF"</span></span>|  
|<span data-ttu-id="8f4a2-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="8f4a2-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="8f4a2-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="8f4a2-115">"INF"</span></span>|  
|<span data-ttu-id="8f4a2-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="8f4a2-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="8f4a2-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="8f4a2-117">"-INF"</span></span>|  
|<span data-ttu-id="8f4a2-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f4a2-118">DateTime</span></span>|<span data-ttu-id="8f4a2-119">Biçimi yyyy-aa-ddTHH:mm:sszzzzzz ve onun alt kümeleri.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="8f4a2-120">Zaman aralığı</span><span class="sxs-lookup"><span data-stu-id="8f4a2-120">Timespan</span></span>|<span data-ttu-id="8f4a2-121">Biçimidir PnYnMnTnHnMnS, örneğin, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10hours süre olan 30 dakika ve 20 saniye.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f4a2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f4a2-122">See also</span></span>

- [<span data-ttu-id="8f4a2-123">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8f4a2-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
- [<span data-ttu-id="8f4a2-124">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8f4a2-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
