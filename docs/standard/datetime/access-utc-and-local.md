---
title: 'Nasıl yapılır: önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine erişme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132601"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="a078f-102">Nasıl yapılır: önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine erişme</span><span class="sxs-lookup"><span data-stu-id="a078f-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="a078f-103"><xref:System.TimeZoneInfo> sınıfı, kodunuzun önceden tanımlanmış saat dilimi nesnelerine erişmesini sağlayan <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>iki özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a078f-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="a078f-104">Bu konu, bu özellikler tarafından döndürülen <xref:System.TimeZoneInfo> nesnelerine nasıl erişebileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a078f-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="a078f-105">Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="a078f-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="a078f-106">Eşgüdümlü Evrensel saate erişmek için `static` (Visual Basic`Shared`) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a078f-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="a078f-107">Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesnesini bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="a078f-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="a078f-108">Yerel saat dilimine erişmek için</span><span class="sxs-lookup"><span data-stu-id="a078f-108">To access the local time zone</span></span>

1. <span data-ttu-id="a078f-109">Yerel sistem saat dilimine erişmek için `static` (Visual Basic`Shared`) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a078f-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="a078f-110">Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesnesini bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yerel saat dilimine erişmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="a078f-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="a078f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a078f-111">Example</span></span>

<span data-ttu-id="a078f-112">Aşağıdaki kod, bir saati ABD ve Kanada Doğu Standart saat diliminden dönüştürmek için <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliklerini kullanır, Ayrıca saat dilimi adını konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a078f-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="a078f-113">Yerel Saat dilimini bir <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla her zaman yerel saat dilimine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a078f-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="a078f-114">Benzer şekilde, bir <xref:System.TimeZoneInfo> nesne değişkenine UTC bölgesi atamak yerine <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate her zaman erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a078f-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="a078f-115">Bu, <xref:System.TimeZoneInfo> nesne değişkeninin <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı tarafından geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a078f-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="a078f-116">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="a078f-116">Compiling the code</span></span>

<span data-ttu-id="a078f-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a078f-117">This example requires:</span></span>

- <span data-ttu-id="a078f-118"><xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="a078f-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="a078f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a078f-119">See also</span></span>

- [<span data-ttu-id="a078f-120">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="a078f-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="a078f-121">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="a078f-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="a078f-122">Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="a078f-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
