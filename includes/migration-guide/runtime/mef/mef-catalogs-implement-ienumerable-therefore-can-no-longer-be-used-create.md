---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497127"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF katalogları IEnumerable arabirimini uygular ve bu nedenle artık seri hale getirici oluşturmak için kullanılamaz

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak MEF katalogları IEnumerable 'ı uygular ve bu nedenle artık seri hale getirici (nesne) oluşturmak için kullanılamaz <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> . MEF kataloğu seri hale getirilmeye çalışıldığında bir özel durum oluşur.

#### <a name="suggestion"></a>Öneri

Bir serileştirici oluşturmak için artık MEF kullanılamıyor

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
