---
title: .NET Framework Türlerini Dizelere Dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287824"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="cd320-102">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cd320-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="cd320-103">Bir .NET Framework türünü dizeye dönüştürmek istiyorsanız, **ToString** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd320-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="cd320-104">**ToString** yöntemi geçirilen türün dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd320-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="cd320-105">Aşağıdaki tabloda, XML şeması (XSD) belirtimlerine eşlenen bir biçimde dize döndüren .NET Framework türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd320-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="cd320-106">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="cd320-106">.NET Framework type</span></span>|<span data-ttu-id="cd320-107">Döndürülen dize türü</span><span class="sxs-lookup"><span data-stu-id="cd320-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="cd320-108">Boole</span><span class="sxs-lookup"><span data-stu-id="cd320-108">Boolean</span></span>|<span data-ttu-id="cd320-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="cd320-109">"true", "false"</span></span>|  
|<span data-ttu-id="cd320-110">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="cd320-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="cd320-111">'SI</span><span class="sxs-lookup"><span data-stu-id="cd320-111">"INF"</span></span>|  
|<span data-ttu-id="cd320-112">Tek. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="cd320-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="cd320-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="cd320-113">"-INF"</span></span>|  
|<span data-ttu-id="cd320-114">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="cd320-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="cd320-115">'SI</span><span class="sxs-lookup"><span data-stu-id="cd320-115">"INF"</span></span>|  
|<span data-ttu-id="cd320-116">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="cd320-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="cd320-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="cd320-117">"-INF"</span></span>|  
|<span data-ttu-id="cd320-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="cd320-118">DateTime</span></span>|<span data-ttu-id="cd320-119">Biçim yyyy-MM-ddTHH: mm: sszzzzzz ve alt kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="cd320-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="cd320-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="cd320-120">Timespan</span></span>|<span data-ttu-id="cd320-121">Biçim Pnazmntnhnmns, örneğin `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye.</span><span class="sxs-lookup"><span data-stu-id="cd320-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd320-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd320-122">See also</span></span>

- [<span data-ttu-id="cd320-123">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cd320-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="cd320-124">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cd320-124">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
