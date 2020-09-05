---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496937"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException artık satır konumlarını düzgün şekilde ayarlıyor

#### <a name="details"></a>Ayrıntılar

<xref:System.Xml.Linq.LoadOptions.SetLineInfo>Değer Load yöntemine geçirilirse ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri artık satır bilgilerini içerir.

#### <a name="suggestion"></a>Öneri

<xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> XML yükleme sırasında SetLineInfo kullanıldığında, ayarlanmayacak ve ayarlanmayacak olan özel durum işleme kodu güncellenmelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->
