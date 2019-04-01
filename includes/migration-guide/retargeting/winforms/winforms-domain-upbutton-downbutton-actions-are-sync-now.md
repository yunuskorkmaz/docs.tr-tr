---
ms.openlocfilehash: 7344fddbc61d47d4ca735808f0b92f63e33e15a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760869"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm'ın etki alanı upbutton ve downbutton eylemleri eşitlenmiş durumda

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerinde <xref:System.Windows.Forms.DomainUpDown> denetimin <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> denetim metin mevcut olduğunda ve geliştirici kullanmak için gerekli eylemi görmezden <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> kullanmadan önce eylem denetimi <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylem. 4.7.2 hem .NET Framework ile başlayarak <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemleri Bu senaryoda, birbirinden bağımsız olarak çalışır ve eşitlenmiş olarak kalır.|
|Öneri|Sırayla bu değişiklikleri yararlanmak bir uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir veya üzeri. Uygulamaya bu değişiklikler aşağıdaki yollardan birini yararlanabilir:<ul><li>.NET Framework 4.7.2 hedefleyecek şekilde derlenmiştir. Bu, varsayılan olarak .NET Framework'ü 4.7.2 hedefleyen Windows Forms uygulamaları etkin ya da üzeri değişikliktir.</li><li>Eski davranışı aşağıdaki ekleyerek kaydırma dışında kabul eder [AppContext anahtar](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) için <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasını ve bu ayarın bölümünü <code>false</code>aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

