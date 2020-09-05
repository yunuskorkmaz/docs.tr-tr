---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496772"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm 'ın Checkforoverflowyetersizliği özelliği artık System. Drawing için doğru

#### <a name="details"></a>Ayrıntılar

System.Drawing.dll derlemesinin Checkforoverflowyetersizliği özelliği true olarak ayarlandı.

#### <a name="suggestion"></a>Öneri

Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir. Şimdi bir <xref:System.OverflowException?displayProperty=fullName> özel durum oluşturuldu.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
