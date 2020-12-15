---
title: 'Son değişiklik: Blazor: Blazor uygulamalarında yönlendirme mantığındaki değişiklikler'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Blazor uygulamalarında yönlendirme mantığındaki değişiklikler"
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513525"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a><span data-ttu-id="fa47a-103">Blazor: Blazor uygulamalarında yol önceliği mantığı değişti</span><span class="sxs-lookup"><span data-stu-id="fa47a-103">Blazor: Route precedence logic changed in Blazor apps</span></span>

<span data-ttu-id="fa47a-104">Blazor yönlendirme uygulamasındaki bir hata, yolların önceliğin nasıl belirlendiğine göre etkilendi.</span><span class="sxs-lookup"><span data-stu-id="fa47a-104">A bug in the Blazor routing implementation affected how the precedence of routes was determined.</span></span> <span data-ttu-id="fa47a-105">Bu hata, Blazor uygulamanızda isteğe bağlı parametrelerle tüm yolları veya yolları etkiler.</span><span class="sxs-lookup"><span data-stu-id="fa47a-105">This bug affects catch-all routes or routes with optional parameters within your Blazor app.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fa47a-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fa47a-106">Version introduced</span></span>

<span data-ttu-id="fa47a-107">5.0.1</span><span class="sxs-lookup"><span data-stu-id="fa47a-107">5.0.1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="fa47a-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="fa47a-108">Old behavior</span></span>

<span data-ttu-id="fa47a-109">Hatalı davranışla, daha düşük önceliğe sahip yollar, daha yüksek önceliğe sahip yollar üzerinden değerlendirilir ve eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fa47a-109">With the erroneous behavior, routes with lower precedence are considered and matched over routes with higher precedence.</span></span> <span data-ttu-id="fa47a-110">Örneğin, yol daha `{*slug}` önce eşleştirilir `/customer/{id}` .</span><span class="sxs-lookup"><span data-stu-id="fa47a-110">For example, the `{*slug}` route is matched before `/customer/{id}`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="fa47a-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="fa47a-111">New behavior</span></span>

<span data-ttu-id="fa47a-112">Geçerli davranış ASP.NET Core uygulamalarda tanımlanan yönlendirme davranışıyla daha yakından eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fa47a-112">The current behavior more closely matches the routing behavior defined in ASP.NET Core apps.</span></span> <span data-ttu-id="fa47a-113">Framework, ilk olarak her bir segmentin yol önceliğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fa47a-113">The framework determines the route precedence for each segment first.</span></span> <span data-ttu-id="fa47a-114">Yolun uzunluğu, yalnızca kesme özellikleri için ikinci bir ölçüt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa47a-114">The route's length is used only as a second criteria to break ties.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fa47a-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="fa47a-115">Reason for change</span></span>

<span data-ttu-id="fa47a-116">Özgün davranış uygulamadaki bir hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fa47a-116">The original behavior is considered a bug in the implementation.</span></span> <span data-ttu-id="fa47a-117">Hedef olarak, Blazor Apps 'teki yönlendirme sistemi, ASP.NET Core geri kalanında yönlendirme sistemiyle aynı şekilde davranmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa47a-117">As a goal, the routing system in Blazor apps should behave the same way as the routing system in the rest of ASP.NET Core.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fa47a-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fa47a-118">Recommended action</span></span>

<span data-ttu-id="fa47a-119">Önceki Blazor sürümlerinden 5. x sürümüne yükseltiyorsanız, `PreferExactMatches` bileşendeki özniteliğini kullanın `Router` .</span><span class="sxs-lookup"><span data-stu-id="fa47a-119">If upgrading from previous versions of Blazor to 5.x, use the `PreferExactMatches` attribute on the `Router` component.</span></span> <span data-ttu-id="fa47a-120">Bu öznitelik doğru davranışı kabul etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa47a-120">This attribute can be used to opt into the correct behavior.</span></span> <span data-ttu-id="fa47a-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="fa47a-121">For example:</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

<span data-ttu-id="fa47a-122">`PreferExactMatches`Olarak ayarlandığında `true` , rota eşleştirme joker karakterlerle tam eşleşmeler tercih eder.</span><span class="sxs-lookup"><span data-stu-id="fa47a-122">When `PreferExactMatches` is set to `true`, route matching prefers exact matches over wildcards.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fa47a-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fa47a-123">Affected APIs</span></span>

<span data-ttu-id="fa47a-124">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fa47a-124">None</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
