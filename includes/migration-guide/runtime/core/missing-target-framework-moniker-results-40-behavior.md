---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620585"
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
