---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620694"
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
