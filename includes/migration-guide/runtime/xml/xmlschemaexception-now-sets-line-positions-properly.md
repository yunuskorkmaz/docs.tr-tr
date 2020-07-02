---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620724"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
