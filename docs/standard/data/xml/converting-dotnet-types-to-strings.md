---
title: .NET türlerini dizelere dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687632"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="ee698-102">.NET türlerini dizelere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="ee698-102">Convert .NET types to strings</span></span>

<span data-ttu-id="ee698-103">Bir .NET türünü dizeye dönüştürmek istiyorsanız, **ToString** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee698-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="ee698-104">**ToString** yöntemi geçirilen türün dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee698-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="ee698-105">Aşağıdaki tabloda, XML şeması (XSD) belirtimlerine eşlenen bir biçimde dize döndüren .NET türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ee698-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="ee698-106">.NET türü</span><span class="sxs-lookup"><span data-stu-id="ee698-106">.NET type</span></span>|<span data-ttu-id="ee698-107">Döndürülen dize türü</span><span class="sxs-lookup"><span data-stu-id="ee698-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="ee698-108">Boole</span><span class="sxs-lookup"><span data-stu-id="ee698-108">Boolean</span></span>|<span data-ttu-id="ee698-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="ee698-109">"true", "false"</span></span>|  
|<span data-ttu-id="ee698-110">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="ee698-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="ee698-111">'SI</span><span class="sxs-lookup"><span data-stu-id="ee698-111">"INF"</span></span>|  
|<span data-ttu-id="ee698-112">Tek. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="ee698-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="ee698-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="ee698-113">"-INF"</span></span>|  
|<span data-ttu-id="ee698-114">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="ee698-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="ee698-115">'SI</span><span class="sxs-lookup"><span data-stu-id="ee698-115">"INF"</span></span>|  
|<span data-ttu-id="ee698-116">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="ee698-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="ee698-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="ee698-117">"-INF"</span></span>|  
|<span data-ttu-id="ee698-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="ee698-118">DateTime</span></span>|<span data-ttu-id="ee698-119">Biçim yyyy-MM-ddTHH: mm: sszzzzzz ve alt kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="ee698-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="ee698-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="ee698-120">Timespan</span></span>|<span data-ttu-id="ee698-121">Biçim Pnazmntnhnmns, örneğin `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye.</span><span class="sxs-lookup"><span data-stu-id="ee698-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee698-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee698-122">See also</span></span>

- [<span data-ttu-id="ee698-123">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ee698-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="ee698-124">Dizeleri .NET veri türlerine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ee698-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
