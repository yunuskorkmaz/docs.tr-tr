---
title: SYSLIB0005 uyarısı
description: Derleme zamanı uyarı SYSLIB0005 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9ed36d247d31bcebc499bd7ed3945490d9d901f9
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256380"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="1f502-103">SYSLIB0005: genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1f502-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="1f502-104">.NET Core ve .NET 5 ve sonraki sürümleri, .NET Framework mevcut olan genel derleme önbelleği (GAC) kavramını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1f502-104">.NET Core and .NET 5 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="1f502-105">Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="1f502-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="1f502-106">Bu API 'Lerin kullanılması, `SYSLIB0005` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f502-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="1f502-107">Aşağıdaki GAC ile ilgili API 'Ler artık kullanılmıyor olarak işaretlendi:</span><span class="sxs-lookup"><span data-stu-id="1f502-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="1f502-108">Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 + ' de döndürdüğünden, çalışma zamanı davranışı hakkında belirleyici hale getirmek için API 'yi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f502-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="1f502-109">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="1f502-109">Workarounds</span></span>

<span data-ttu-id="1f502-110">Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1f502-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="1f502-111">"GAC 'de olmayan bir derleme"-Flow "( <xref:System.Reflection.Assembly.GlobalAssemblyCache> GAC 'de olmayan bir derleme") arasında seçim yapmak için değeri kullanırsanız, akışın bir .NET 5 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="1f502-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="1f502-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f502-112">See also</span></span>

- [<span data-ttu-id="1f502-113">Genel derleme önbelleği</span><span class="sxs-lookup"><span data-stu-id="1f502-113">Global assembly cache</span></span>](../../../framework/app-domains/gac.md)
