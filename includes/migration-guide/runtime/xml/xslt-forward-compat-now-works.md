---
ms.openlocfilehash: 8c8477ae3719cfcc2060459ba85bcc9e76f11c41
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497759"
---
### <a name="xslt-forward-compat-now-works"></a>XSLT ileriye dönük uyumluluk artık çalışmaktadır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4 ' te, XSLT 1,0 ileri uyumluluğu aşağıdaki sorunlara sahipti:<ul><li>Sürümü 2.0 değerine ayarlanmış bir stil sayfasının yüklenmesi başarısız oldu ve ayrıştırıcı tanınmayan bir XSLT 1.0 yapısıyla karşılaştı.</li><li><code>xsl:sort</code>Stil sayfası sürümü 1,1 olarak ayarlandıysa, yapı verileri sıralayamadı.</li></ul>.NET Framework 4,5 ' de, bu sorunlar düzeltildi ve XSLT 1,0 ileri uyumluluk modu düzgün şekilde çalışmaktadır.

#### <a name="suggestion"></a>Öneri

Çoğu uygulama etkilenmemelidir, ancak bazı durumlarda veriler farklı sıralanacaktır çünkü artık xsl: Sort kullanılır. <code>xsl:sort</code>1,1 Stil sayfalarında kullanılırsa, uygulamaların sıralanmamış veri sırasına bağlı olmadığını onaylayın. Uygulamalar 4,0 sıralama davranışını kullanıyorsa, <code>xsl:sort</code> stil sayfasından kaldırın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Xml.Xsl.XslCompiledTransform`

-->
