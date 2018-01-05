---
title: "Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="b1817-102">Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim</span><span class="sxs-lookup"><span data-stu-id="b1817-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="b1817-103"><xref:System.TimeZoneInfo> SAX iki özellik <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>, önceden tanımlanmış saat dilimi nesneleri için kod erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="b1817-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="b1817-104">Bu konuda ele alınmıştır nasıl erişileceği <xref:System.TimeZoneInfo> bu özellik tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="b1817-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="b1817-105">Eşgüdümlü Evrensel Saat (UTC) Timezoneınfo nesnesinin erişmek için</span><span class="sxs-lookup"><span data-stu-id="b1817-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="b1817-106">Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel Saat erişmeye özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1817-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="b1817-107">Atama yerine <xref:System.TimeZoneInfo> nesne bir nesne değişkeni için özellik tarafından döndürülen üzerinden Eşgüdümlü Evrensel Saat erişmeye devam <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1817-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="b1817-108">Yerel saat dilimini erişmek için</span><span class="sxs-lookup"><span data-stu-id="b1817-108">To access the local time zone</span></span>

1. <span data-ttu-id="b1817-109">Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel sistem saat dilimi erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="b1817-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="b1817-110">Atama yerine <xref:System.TimeZoneInfo> nesne bir nesne değişkeni için özellik tarafından döndürülen aracılığıyla yerel saat dilimi erişmeye devam <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1817-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="b1817-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1817-111">Example</span></span>

<span data-ttu-id="b1817-112">Aşağıdaki kod <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özellikleri ABD ve Kanada Doğu Standart Saati Bölgesi'nden bir saat dönüştürme gibi konsola saat dilimi adını görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="b1817-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="b1817-113">Yerel saat dilimi aracılığıyla her zaman erişim <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel saat atama yerine özelliği bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b1817-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b1817-114">Benzer şekilde, her zaman Eşgüdümlü Evrensel Saat üzerinden erişim <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC atama yerine özelliği bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b1817-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b1817-115">Bu engeller <xref:System.TimeZoneInfo> nesne değişkeni için bir çağrı tarafından geçersiz gelen <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1817-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b1817-116">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="b1817-116">Compiling the code</span></span>

<span data-ttu-id="b1817-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b1817-117">This example requires:</span></span>

* <span data-ttu-id="b1817-118">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="b1817-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="b1817-119">Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="b1817-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1817-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1817-120">See also</span></span>

<span data-ttu-id="b1817-121">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span><span class="sxs-lookup"><span data-stu-id="b1817-121">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span></span>
