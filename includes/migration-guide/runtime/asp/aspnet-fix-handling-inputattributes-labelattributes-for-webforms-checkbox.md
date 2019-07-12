---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802660"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>WebForms CheckBox denetimi InputAttributes LabelAttributes ve ASP.NET düzeltme işleme

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalar için <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> bir Webforms'tan program aracılığıyla eklenen <xref:System.Web.UI.WebControls.CheckBox> denetim geri gönderme sonra kaybolur. .NET Framework 4.8 veya sonraki sürümlerini hedefleyen uygulamalar için bunlar geri gönderme sonra korunur.|
|Öneri|Doğru davranışı geri gönderme özniteliklerinde geri yükleme ayarlayın <code>targetFrameworkVersion</code> 4.8 veya üzeri. Örneğin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Düşük veya olmayan hiç ayarı yanlış eski davranışı korur.|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

