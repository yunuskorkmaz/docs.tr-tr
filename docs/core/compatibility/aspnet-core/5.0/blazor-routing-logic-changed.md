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
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Blazor: Blazor uygulamalarında yol önceliği mantığı değişti

Blazor yönlendirme uygulamasındaki bir hata, yolların önceliğin nasıl belirlendiğine göre etkilendi. Bu hata, Blazor uygulamanızda isteğe bağlı parametrelerle tüm yolları veya yolları etkiler.

## <a name="version-introduced"></a>Sunulan sürüm

5.0.1

## <a name="old-behavior"></a>Eski davranış

Hatalı davranışla, daha düşük önceliğe sahip yollar, daha yüksek önceliğe sahip yollar üzerinden değerlendirilir ve eşleştirilir. Örneğin, yol daha `{*slug}` önce eşleştirilir `/customer/{id}` .

## <a name="new-behavior"></a>Yeni davranış

Geçerli davranış ASP.NET Core uygulamalarda tanımlanan yönlendirme davranışıyla daha yakından eşleşir. Framework, ilk olarak her bir segmentin yol önceliğini belirler. Yolun uzunluğu, yalnızca kesme özellikleri için ikinci bir ölçüt olarak kullanılır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Özgün davranış uygulamadaki bir hata olarak kabul edilir. Hedef olarak, Blazor Apps 'teki yönlendirme sistemi, ASP.NET Core geri kalanında yönlendirme sistemiyle aynı şekilde davranmalıdır.

## <a name="recommended-action"></a>Önerilen eylem

Önceki Blazor sürümlerinden 5. x sürümüne yükseltiyorsanız, `PreferExactMatches` bileşendeki özniteliğini kullanın `Router` . Bu öznitelik doğru davranışı kabul etmek için kullanılabilir. Örnek:

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

`PreferExactMatches`Olarak ayarlandığında `true` , rota eşleştirme joker karakterlerle tam eşleşmeler tercih eder.

## <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
