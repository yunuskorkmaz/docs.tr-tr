---
title: 'Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586423"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="0c77a-102">Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="0c77a-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="0c77a-103"><xref:System.TimeZoneInfo> SAX iki özellik <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>, önceden tanımlanmış saat dilimi nesneleri, kod erişim verin.</span><span class="sxs-lookup"><span data-stu-id="0c77a-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="0c77a-104">Bu konu nasıl erişileceğini açıklar <xref:System.TimeZoneInfo> bu özellik tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="0c77a-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="0c77a-105">Eşgüdümlü Evrensel Saat (UTC) Timezoneınfo nesnesinin erişmek için</span><span class="sxs-lookup"><span data-stu-id="0c77a-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="0c77a-106">Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel Saat erişmeye özelliği.</span><span class="sxs-lookup"><span data-stu-id="0c77a-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="0c77a-107">Atama yerine <xref:System.TimeZoneInfo> nesnesi bir nesne değişkenine özelliği tarafından döndürülen Eşgüdümlü Evrensel Saat üzerinden erişmeye devam <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0c77a-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="0c77a-108">Yerel saat dilimi erişmek için</span><span class="sxs-lookup"><span data-stu-id="0c77a-108">To access the local time zone</span></span>

1. <span data-ttu-id="0c77a-109">Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel sistem saat dilimi erişmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="0c77a-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="0c77a-110">Atama yerine <xref:System.TimeZoneInfo> nesnesi bir nesne değişkenine özelliği tarafından döndürülen yerel saat dilimi üzerinden erişmeye devam <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0c77a-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="0c77a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c77a-111">Example</span></span>

<span data-ttu-id="0c77a-112">Aşağıdaki kod <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ABD ve Kanada Doğu Standart saat diliminden dönüştürün gibi saat dilimi adını konsolda görüntülemek için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0c77a-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="0c77a-113">Her zaman yerel saat dilimi üzerinden erişmelidir <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel saat atamak yerine özellik bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0c77a-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="0c77a-114">Benzer şekilde, her zaman Eşgüdümlü Evrensel Saat üzerinden erişmelidir <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC atamak yerine özellik bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0c77a-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="0c77a-115">Bu engeller <xref:System.TimeZoneInfo> gelen bir çağrı tarafından geçersiz nesne değişkeni <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c77a-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="0c77a-116">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="0c77a-116">Compiling the code</span></span>

<span data-ttu-id="0c77a-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0c77a-117">This example requires:</span></span>

* <span data-ttu-id="0c77a-118">Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="0c77a-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c77a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c77a-119">See also</span></span>

- [<span data-ttu-id="0c77a-120">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="0c77a-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="0c77a-121">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="0c77a-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="0c77a-122">Nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c77a-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
