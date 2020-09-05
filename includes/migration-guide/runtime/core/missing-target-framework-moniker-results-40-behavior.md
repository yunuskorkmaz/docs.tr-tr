---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497241"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>4,0 davranışında hedef Framework bilinen ad sonuçları eksik

#### <a name="details"></a>Ayrıntılar

<xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Derleme düzeyinde uygulanmamış uygulamalar, .NET Framework 4,0 ' nin semantiği (olağandışı KS) kullanılarak otomatik olarak çalıştırılır. Yüksek kaliteli olduğundan emin olmak için tüm ikili dosyaların, <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> derlendikleri .NET Framework sürümünü belirten bir ile açıkça ilişkilendirilmesi önerilir. Bir proje dosyasında hedef çerçeve bilinen adının kullanılması, MSBuild 'in otomatik olarak uygulanmasına neden olacağını unutmayın <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

<xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Özniteliği doğrudan derlemeye ekleme yoluyla veya [Proje dosyasında ya da Visual Studio 'nun proje özellikleri GUI 'si aracılığıyla](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/)bir hedef çerçeve belirtilerek sağlanmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
