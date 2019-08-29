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
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106558"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="2b872-102">Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="2b872-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="2b872-103">Sınıfı, kodunuzun önceden tanımlanmış saat <xref:System.TimeZoneInfo.Utc%2A> dilimi <xref:System.TimeZoneInfo.Local%2A>nesnelerine erişmesini sağlayan iki özellik sağlar. <xref:System.TimeZoneInfo></span><span class="sxs-lookup"><span data-stu-id="2b872-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="2b872-104">Bu konu, <xref:System.TimeZoneInfo> bu özellikler tarafından döndürülen nesnelere nasıl erişebileceğinizi anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b872-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="2b872-105">Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="2b872-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="2b872-106">Eşgüdümlü Evrensel saate`Shared` erişmek için <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> (Visual Basic) özelliğini kullanın. `static`</span><span class="sxs-lookup"><span data-stu-id="2b872-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="2b872-107">Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesneyi bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="2b872-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="2b872-108">Yerel saat dilimine erişmek için</span><span class="sxs-lookup"><span data-stu-id="2b872-108">To access the local time zone</span></span>

1. <span data-ttu-id="2b872-109">Yerel sistem saat`Shared` dilimine erişmek için <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>(VisualBasic ) özelliğini kullanın. `static`</span><span class="sxs-lookup"><span data-stu-id="2b872-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="2b872-110">Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesneyi bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yerel saat dilimine erişmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="2b872-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="2b872-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b872-111">Example</span></span>

<span data-ttu-id="2b872-112">Aşağıdaki kod, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve özelliklerini ABD <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ve Kanada Doğu Standart saat diliminden bir kez dönüştürmek için ve saat dilimi adını konsola göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b872-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="2b872-113">Yerel Saat dilimini bir <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine, her zaman, özelliği aracılığıyla yerel saat dilimine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b872-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2b872-114">Benzer şekilde, UTC bölgesini bir <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine, Eşgüdümlü Evrensel saate her zaman özelliği aracılığıyla erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b872-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2b872-115">Bu, <xref:System.TimeZoneInfo> nesne değişkeninin <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda yapılan bir çağrı tarafından geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="2b872-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2b872-116">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="2b872-116">Compiling the code</span></span>

<span data-ttu-id="2b872-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2b872-117">This example requires:</span></span>

- <span data-ttu-id="2b872-118">Bu ad alanı, `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir). <xref:System></span><span class="sxs-lookup"><span data-stu-id="2b872-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b872-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b872-119">See also</span></span>

- [<span data-ttu-id="2b872-120">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="2b872-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="2b872-121">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="2b872-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="2b872-122">Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b872-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
