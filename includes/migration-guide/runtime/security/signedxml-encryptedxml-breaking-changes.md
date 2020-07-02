---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621379"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml ve EncryptedXml kırılmaya yönelik değişiklikler

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ' de güvenlik düzeltmeleri <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> farklı çalışma zamanı davranışlarına yol açabilir. Örneğin,<ul><li>Bir belgede aynı özniteliğe sahip birden fazla öğe varsa <code>id</code> ve imza imza kökü olarak bu öğelerden birini hedefliyorsa, belge artık geçersiz olarak kabul edilir.</li><li>Başvurularda kurallı olmayan XPath dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</li><li>Başvurularda kurallı olmayan XSLT dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</li><li>Dış kaynak bağlantısı kesilen imzaları kullanan tüm programlar bunu yapamayacak.</li></ul>

#### <a name="suggestion"></a>Öneri

Geliştiriciler <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> , ve ' nin kullanımını ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> <xref:System.Security.Cryptography.Xml.Transform> belge alıcısından bu yana türetilmiş türleri işleyemeyebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
