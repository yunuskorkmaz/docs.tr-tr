---
title: ".NET Framework türleri dizeleri dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="3ea2c-102">.NET Framework türleri dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3ea2c-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="3ea2c-103">.NET Framework türü bir dizeye dönüştürmek istediğiniz kullanırsanız **ToString** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="3ea2c-104">**ToString** yöntemi geçirilen tür bir dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="3ea2c-105">Aşağıdaki tabloda XML Şeması (XSD) belirtimleri eşleyen biçiminde bir dize döndürecek .NET Framework türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="3ea2c-106">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="3ea2c-106">.NET Framework type</span></span>|<span data-ttu-id="3ea2c-107">Döndürülen dize türü</span><span class="sxs-lookup"><span data-stu-id="3ea2c-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="3ea2c-108">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3ea2c-108">Boolean</span></span>|<span data-ttu-id="3ea2c-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="3ea2c-109">"true", "false"</span></span>|  
|<span data-ttu-id="3ea2c-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3ea2c-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="3ea2c-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="3ea2c-111">"INF"</span></span>|  
|<span data-ttu-id="3ea2c-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3ea2c-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="3ea2c-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3ea2c-113">"-INF"</span></span>|  
|<span data-ttu-id="3ea2c-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3ea2c-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="3ea2c-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="3ea2c-115">"INF"</span></span>|  
|<span data-ttu-id="3ea2c-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3ea2c-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="3ea2c-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3ea2c-117">"-INF"</span></span>|  
|<span data-ttu-id="3ea2c-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="3ea2c-118">DateTime</span></span>|<span data-ttu-id="3ea2c-119">Biçimidir yyyy-aa-ddTHH:mm:sszzzzzz ve onun alt kümeleri.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="3ea2c-120">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3ea2c-120">Timespan</span></span>|<span data-ttu-id="3ea2c-121">Biçimidir PnYnMnTnHnMnS, örneğin, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10hours süresi 30 dakika ve 20 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea2c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ea2c-122">See Also</span></span>  
 [<span data-ttu-id="3ea2c-123">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3ea2c-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="3ea2c-124">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3ea2c-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
