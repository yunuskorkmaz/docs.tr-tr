---
title: SYSLIB0005 uyarısı
description: Derleme zamanı uyarı SYSLIB0005 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8a9893d81c781335014c8b970c460b5a4241ed18
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333346"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="ea071-103">SYSLIB0005: genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ea071-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="ea071-104">.NET Core ve .NET 5,0 ve sonraki sürümleri, .NET Framework bulunan genel derleme önbelleği (GAC) kavramını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ea071-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="ea071-105">Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ea071-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="ea071-106">Bu API 'Lerin kullanılması, `SYSLIB0005` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea071-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="ea071-107">Aşağıdaki GAC ile ilgili API 'Ler artık kullanılmıyor olarak işaretlendi:</span><span class="sxs-lookup"><span data-stu-id="ea071-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="ea071-108">Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 + ' de döndürdüğünden, çalışma zamanı davranışı hakkında belirleyici hale getirmek için API 'yi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea071-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workaround"></a><span data-ttu-id="ea071-109">Geçici çözüm</span><span class="sxs-lookup"><span data-stu-id="ea071-109">Workaround</span></span>

<span data-ttu-id="ea071-110">Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ea071-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="ea071-111">"GAC 'de olmayan bir derleme"-Flow "( <xref:System.Reflection.Assembly.GlobalAssemblyCache> GAC 'de olmayan bir derleme") arasında seçim yapmak için değeri kullanırsanız, akışın bir .NET 5 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="ea071-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea071-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea071-112">See also</span></span>

- [<span data-ttu-id="ea071-113">Genel derleme önbelleği</span><span class="sxs-lookup"><span data-stu-id="ea071-113">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
