---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620634"
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
