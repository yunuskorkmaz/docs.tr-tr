---
title: 'Son değişiklik: örnek zaten varsa CreateCounterSetInstance InvalidOperationException oluşturur'
description: .NET 5 ' in, CounterSet. CreateCounterSetInstance, sayaç zaten varsa farklı bir özel durum oluşturan çekirdek .NET kitaplıklarında, .NET 5 ' i değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: bf59677a85538bc4992c589f8642ab4a0fce54ac
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257576"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="de5cc-103">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="de5cc-103">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="de5cc-104">.NET 5 ' den başlayarak, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> sayaç kümesi zaten varsa bir yerine bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de5cc-104">Starting in .NET 5, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

## <a name="change-description"></a><span data-ttu-id="de5cc-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="de5cc-105">Change description</span></span>

<span data-ttu-id="de5cc-106">.NET Framework ve .NET Core 1,0 ile 3,1 arasında, çağırarak sayaç kümesinin bir örneğini oluşturabilirsiniz <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="de5cc-106">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="de5cc-107">Ancak, sayaç kümesi zaten varsa, yöntem bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de5cc-107">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="de5cc-108">.NET 5 ve sonraki sürümlerinde, çağırdığınızda <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ve sayaç kümesi varsa, bir <xref:System.InvalidOperationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="de5cc-108">In .NET 5 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="de5cc-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="de5cc-109">Version introduced</span></span>

<span data-ttu-id="de5cc-110">5.0</span><span class="sxs-lookup"><span data-stu-id="de5cc-110">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="de5cc-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="de5cc-111">Recommended action</span></span>

<span data-ttu-id="de5cc-112"><xref:System.ArgumentException>Çağrılırken uygulamanızda özel durumları yakalarsanız <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> özel durumları da yakalamaya göz önünde bulundurun <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="de5cc-112">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="de5cc-113">Yakalama <xref:System.ArgumentException> özel durumları önerilmez.</span><span class="sxs-lookup"><span data-stu-id="de5cc-113">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="de5cc-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="de5cc-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
