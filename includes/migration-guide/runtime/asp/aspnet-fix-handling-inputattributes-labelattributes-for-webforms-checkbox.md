---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496605"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>WebForms onay kutusu denetimi için InputAttributes ve LabelAttributes 'ın ASP.NET düzeltmesini işleme

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümleri hedefleyen <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> Program aracılığıyla bir WebForms denetimine eklenen uygulamalar için <xref:System.Web.UI.WebControls.CheckBox> geri gönderme işleminden sonra kaybolacaktır. .NET Framework 4,8 veya sonraki sürümlerini hedefleyen uygulamalar için, geri gönderme sonrasında korunur.

#### <a name="suggestion"></a>Öneri

Geri göndermede özniteliklerin geri yüklenmesine yönelik doğru davranış için, öğesini <code>targetFrameworkVersion</code> 4,8 veya üzeri olarak ayarlayın. Örneğin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu ayarı daha düşük veya hiç değil, eski hatalı davranışı korur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Bilinmiyor|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
