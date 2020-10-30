---
title: 'Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 598cd631fab1ddc115bc6153580351b1dc14d5bf
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063891"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="b920e-102">Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="b920e-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="b920e-103"><xref:System.TimeZoneInfo>Sınıfı, <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> kodunuzun önceden tanımlanmış saat dilimi nesnelerine erişmesini sağlayan iki özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b920e-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="b920e-104">Bu konu, bu <xref:System.TimeZoneInfo> Özellikler tarafından döndürülen nesnelere nasıl erişebileceğinizi anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b920e-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="b920e-105">Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="b920e-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="b920e-106">`static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel saate erişmek için (Visual Basic) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b920e-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="b920e-107"><xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b920e-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="b920e-108">Yerel saat dilimine erişmek için</span><span class="sxs-lookup"><span data-stu-id="b920e-108">To access the local time zone</span></span>

1. <span data-ttu-id="b920e-109">`static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Yerel sistem saat dilimine erişmek için (Visual Basic) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b920e-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="b920e-110"><xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla yerel saat dilimine erişmeye devam edin <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b920e-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="b920e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b920e-111">Example</span></span>

<span data-ttu-id="b920e-112">Aşağıdaki kod, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliklerini ABD ve Kanada Doğu Standart saat diliminden bir kez dönüştürmek için ve saat dilimi adını konsola göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b920e-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="b920e-113">Yerel Saat dilimini <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> bir nesne değişkenine atamak yerine, her zaman, özelliği aracılığıyla yerel saat dilimine erişmeniz gerekir <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="b920e-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b920e-114">Benzer şekilde, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC bölgesini bir nesne değişkenine atamak yerine, Eşgüdümlü Evrensel saate her zaman özelliği aracılığıyla erişmeniz gerekir <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="b920e-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b920e-115">Bu, <xref:System.TimeZoneInfo> nesne değişkeninin metoda yapılan bir çağrı tarafından geçersiz kılınmasını önler <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b920e-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b920e-116">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="b920e-116">Compiling the code</span></span>

<span data-ttu-id="b920e-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b920e-117">This example requires:</span></span>

- <span data-ttu-id="b920e-118">Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="b920e-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b920e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b920e-119">See also</span></span>

- [<span data-ttu-id="b920e-120">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="b920e-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="b920e-121">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="b920e-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="b920e-122">Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b920e-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
