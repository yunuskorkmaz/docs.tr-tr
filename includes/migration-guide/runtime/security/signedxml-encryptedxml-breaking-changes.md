---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857472"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>İmzaXml ve ŞifreliXml Breaking Değişiklikler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'de, <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> Güvenlik <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> farklı çalışma zamanı davranışlarını düzeltir ve bu da farklı çalışma zamanı davranışlarına yol açar. Örneğin,<ul><li>Bir belgeaynı <code>id</code> öznitelik ve imza hedeflerinden biri imza kökü olarak birden çok öğe varsa, belge artık geçersiz olarak kabul edilecektir.</li><li>Başvurularda kanonik olmayan XPath dönüştürme algoritmaları kullanan belgeler artık geçersiz kabul edilir.</li><li>Başvurularda kanonik olmayan XSLT dönüştürme algoritmaları kullanan belgeler artık geçersiz kabul edilir.</li><li>Dış kaynak ayrılmış imzalardan yararlanan herhangi bir program bunu yapamaz.</li></ul>|
|Öneri|Geliştiriciler, belge alıcısının <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> bu <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>kullanımı ve , <xref:System.Security.Cryptography.Xml.Transform> yanı sıra türetilen türleri gözden geçirmek isteyebilir.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
