---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802660"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET WebForms CheckBox denetimi için Giriş Öznitelikleri nin ve LabelÖzlerin İşleışını düzeltme

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümleri <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> hedefleyen <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> ve webforms <xref:System.Web.UI.WebControls.CheckBox> denetimine programlı olarak eklenen uygulamalar için postback sonrası kaybolur. .NET Framework 4.8 veya sonraki sürümleri hedefleyen uygulamalar için, postback sonra korunur.|
|Öneri|Postback öznitelikleri geri için doğru davranış için, 4.8 veya daha yüksek ayarlayın. <code>targetFrameworkVersion</code> Örnek:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Daha düşük veya hiç ayarlayarak eski yanlış davranışı korur.|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
