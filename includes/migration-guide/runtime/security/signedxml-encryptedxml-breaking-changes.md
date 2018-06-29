### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml ve EncryptedXml yeni değişiklikler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, güvenlik giderir <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> farklı çalışma zamanı davranışları sağlama. Örneğin,<ul><li>Bir belgede aynı birden çok öğe varsa <code>id</code> özniteliği ve imza hedeflediği bu öğelerden birine imza kök olarak belgeyi artık geçersiz olarak kabul edilir.</li><li>Kurallı olmayan XPath dönüştürme algoritmaları başvurularında kullanarak belgeleri artık geçersiz olarak kabul edilir.</li><li>Kurallı olmayan XSLT dönüşümü algoritmaları başvurularında kullanarak belgeleri şimdi dikkat edilmelidir geçersiz.</li><li>Bunu yapmak dış kaynak ayrılmış imzaları program yapmayı kullanımı yükleyemez.</li></ul>|
|Öneri|Geliştiriciler kullanımını gözden geçirmek isteyebilirsiniz <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, yanı sıra türleri türetilmiş <xref:System.Security.Cryptography.Xml.Transform> bu yana bir belge alıcı işlemek olmayabilir.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|

