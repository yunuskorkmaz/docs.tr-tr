---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496510"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>EnableViewStateMac 'i artık false olarak ayarlayaamayacak

#### <a name="details"></a>Ayrıntılar

ASP.NET artık geliştiricilerin veya belirlemesine izin vermez <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> . Görünüm durumu iletisi kimlik doğrulama kodu (MAC) artık katıştırılmış görünüm durumundaki tüm istekler için zorlanır. Yalnızca EnableViewStateMac özelliğini açıkça ayarlamış olan uygulamalar <code>false</code> etkilenir.

#### <a name="suggestion"></a>Öneri

EnableViewStateMac 'in doğru olması gerekir ve sonuçta elde edilen MAC hatalarının çözümlenmesi gerekir ( [Bu](https://support.microsoft.com/kb/2915218)kılavuzda açıklandığı gıbı, Mac hatalarına neden olan Özellikler ' e bağlı olarak birden çok çözüm içeren).

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
