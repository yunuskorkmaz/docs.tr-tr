---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620616"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Farklı 4,5 SQL neslini daha basit 4,0 SQL oluşturmaya geri dönmek için kabul etme kesmesi

#### <a name="details"></a>Ayrıntılar

JOIN deyimleri üreten ve önce OrderBy kullanılmadan sınırlayan bir işleme çağrı içeren sorgular artık daha basit bir SQL üretin. .NET Framework 4,5 ' e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık bir SQL üretti.

#### <a name="suggestion"></a>Öneri

Bu özellik varsayılan olarak devre dışıdır. Entity Framework, performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|
