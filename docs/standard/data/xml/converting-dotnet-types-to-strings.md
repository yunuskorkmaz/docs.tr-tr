---
description: 'Hakkında daha fazla bilgi edinin: .NET türlerini dizelere dönüştürme'
title: .NET türlerini dizelere dönüştürme
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 5a3e391eb0e6dc21ae800ede43247d24199efd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642532"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="3921f-103">.NET türlerini dizelere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="3921f-103">Convert .NET types to strings</span></span>

<span data-ttu-id="3921f-104">Bir .NET türünü dizeye dönüştürmek istiyorsanız, **ToString** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3921f-104">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="3921f-105">**ToString** yöntemi geçirilen türün dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3921f-105">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="3921f-106">Aşağıdaki tabloda, XML şeması (XSD) belirtimlerine eşlenen bir biçimde dize döndüren .NET türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3921f-106">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="3921f-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3921f-107">.NET type</span></span>|<span data-ttu-id="3921f-108">Döndürülen dize türü</span><span class="sxs-lookup"><span data-stu-id="3921f-108">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="3921f-109">Boole</span><span class="sxs-lookup"><span data-stu-id="3921f-109">Boolean</span></span>|<span data-ttu-id="3921f-110">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="3921f-110">"true", "false"</span></span>|  
|<span data-ttu-id="3921f-111">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3921f-111">Single.PositiveInfinity</span></span>|<span data-ttu-id="3921f-112">'SI</span><span class="sxs-lookup"><span data-stu-id="3921f-112">"INF"</span></span>|  
|<span data-ttu-id="3921f-113">Tek. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3921f-113">Single.NegativeInfinity</span></span>|<span data-ttu-id="3921f-114">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3921f-114">"-INF"</span></span>|  
|<span data-ttu-id="3921f-115">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3921f-115">Double.PositiveInfinity</span></span>|<span data-ttu-id="3921f-116">'SI</span><span class="sxs-lookup"><span data-stu-id="3921f-116">"INF"</span></span>|  
|<span data-ttu-id="3921f-117">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3921f-117">Double.NegativeInfinity</span></span>|<span data-ttu-id="3921f-118">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3921f-118">"-INF"</span></span>|  
|<span data-ttu-id="3921f-119">DateTime</span><span class="sxs-lookup"><span data-stu-id="3921f-119">DateTime</span></span>|<span data-ttu-id="3921f-120">Biçim yyyy-MM-ddTHH: mm: sszzzzzz ve alt kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="3921f-120">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="3921f-121">Timespan</span><span class="sxs-lookup"><span data-stu-id="3921f-121">Timespan</span></span>|<span data-ttu-id="3921f-122">Biçim Pnazmntnhnmns, örneğin `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye.</span><span class="sxs-lookup"><span data-stu-id="3921f-122">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3921f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3921f-123">See also</span></span>

- [<span data-ttu-id="3921f-124">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3921f-124">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="3921f-125">Dizeleri .NET veri türlerine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3921f-125">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
