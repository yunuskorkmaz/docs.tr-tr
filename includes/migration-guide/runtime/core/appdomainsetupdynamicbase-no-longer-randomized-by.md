---
ms.openlocfilehash: 26c50ac8b0e570e31a38b1913f73acbe21fae08b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497032"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup. DynamicBase artık UseRandomizedStringHashAlgorithm tarafından rasgeleleştirilmedi

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' dan önce, değeri <xref:System.AppDomainSetup.DynamicBase> uygulama etki alanları arasında rastgele hale getirilir veya UseRandomizedStringHashAlgorithm, uygulamanın yapılandırma dosyasında etkinleştirildiyse, süreçler arasında rasgeledir. .NET Framework 4,6 ' den başlayarak, <xref:System.AppDomainSetup.DynamicBase> çalıştıran bir uygulamanın farklı örnekleri arasında ve farklı uygulama etki alanları arasında kararlı bir sonuç döndürür. Dinamik tabanlar farklı uygulamalar için hala farklılık gösterir; Bu değişiklik yalnızca aynı uygulamanın farklı örneklerinin rastgele adlandırma öğesini kaldırır.

#### <a name="suggestion"></a>Öneri

Etkinleştirmenin rastgele hale gelemeyeceğini unutmayın <code>UseRandomizedStringHashAlgorithm</code> <xref:System.AppDomainSetup.DynamicBase> . Rastgele bir taban gerekliyse, bu API 'nin yerine uygulamanızın kodunda oluşturulması gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.DynamicBase`

-->
