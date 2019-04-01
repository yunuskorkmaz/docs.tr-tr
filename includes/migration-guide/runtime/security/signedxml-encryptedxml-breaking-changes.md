---
ms.openlocfilehash: 2c54912e5c29b2ed8f4c8163550050e12e367263
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760691"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml ve EncryptedXml bozucu değişiklikler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, güvenlik giderir <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> farklı çalışma zamanı davranışları neden olabilir. Örneğin,<ul><li>Bir belgede aynı sahip birden çok öğe varsa <code>id</code> özniteliğini ve bir imza hedeflediği bu öğelerden birini imza kökü olarak belge artık geçersiz kabul edilir.</li><li>Kurallı olmayan XPath dönüştürme algoritmaları başvurular belgeleri artık geçersiz olarak kabul edilir.</li><li>Kurallı olmayan XSLT dönüşümü algoritmaları başvurular belgeleri artık dikkat edilmelidir geçersiz.</li><li>Dış kaynak ayrılmış imzaları program yapmayı kullanımı yapmanız mümkün olacaktır.</li></ul>|
|Öneri|Geliştiriciler, kullanımını gözden geçirmek isteyebileceğiniz <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, yanı sıra türetilmiş türler <xref:System.Security.Cryptography.Xml.Transform> bu yana belge alıcı işlem sırasında mümkün olmayabilir.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|

