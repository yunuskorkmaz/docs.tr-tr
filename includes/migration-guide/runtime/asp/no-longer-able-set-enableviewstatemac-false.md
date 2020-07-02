---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620543"
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
