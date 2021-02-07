---
description: 'Daha fazla bilgi edinin: nasıl yapılır: önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine erişim'
title: 'Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim'
ms.date: 04/10/2017
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
ms.openlocfilehash: 74e3ca601ac0b3a6a684569b0931f8566b5d5d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702762"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="fa59e-103">Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="fa59e-103">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="fa59e-104"><xref:System.TimeZoneInfo>Sınıfı, <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> kodunuzun önceden tanımlanmış saat dilimi nesnelerine erişmesini sağlayan iki özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa59e-104">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="fa59e-105">Bu konu, bu <xref:System.TimeZoneInfo> Özellikler tarafından döndürülen nesnelere nasıl erişebileceğinizi anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa59e-105">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="fa59e-106">Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="fa59e-106">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="fa59e-107">`static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel saate erişmek için (Visual Basic) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa59e-107">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="fa59e-108"><xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa59e-108">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="fa59e-109">Yerel saat dilimine erişmek için</span><span class="sxs-lookup"><span data-stu-id="fa59e-109">To access the local time zone</span></span>

1. <span data-ttu-id="fa59e-110">`static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Yerel sistem saat dilimine erişmek için (Visual Basic) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa59e-110">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="fa59e-111"><xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla yerel saat dilimine erişmeye devam edin <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa59e-111">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="fa59e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa59e-112">Example</span></span>

<span data-ttu-id="fa59e-113">Aşağıdaki kod, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliklerini ABD ve Kanada Doğu Standart saat diliminden bir kez dönüştürmek için ve saat dilimi adını konsola göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa59e-113">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="fa59e-114">Yerel Saat dilimini <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> bir nesne değişkenine atamak yerine, her zaman, özelliği aracılığıyla yerel saat dilimine erişmeniz gerekir <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="fa59e-114">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fa59e-115">Benzer şekilde, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC bölgesini bir nesne değişkenine atamak yerine, Eşgüdümlü Evrensel saate her zaman özelliği aracılığıyla erişmeniz gerekir <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="fa59e-115">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fa59e-116">Bu, <xref:System.TimeZoneInfo> nesne değişkeninin metoda yapılan bir çağrı tarafından geçersiz kılınmasını önler <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa59e-116">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fa59e-117">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="fa59e-117">Compiling the code</span></span>

<span data-ttu-id="fa59e-118">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fa59e-118">This example requires:</span></span>

- <span data-ttu-id="fa59e-119">Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="fa59e-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa59e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa59e-120">See also</span></span>

- [<span data-ttu-id="fa59e-121">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="fa59e-121">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="fa59e-122">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="fa59e-122">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="fa59e-123">Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa59e-123">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
