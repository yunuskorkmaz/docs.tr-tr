---
ms.openlocfilehash: f1a1eab471d46f018a8e0d0cf787d487cf67c11e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762664"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>İç içe geçmiş Toolstripmenuıtems söz konusu olduğunda, geçerli bir denetim ContextMenuStrip.SourceControl özelliği içerir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerde <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği yanlış menüden kullanıcı oturum açtığında null döndürür iç içe geçmiş <xref:System.Windows.Forms.ToolStripMenuItem> kontrol eder. .NET Framework'teki 4.7.2 ve daha sonra <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği her zaman gerçek kaynak denetimine ayarlayın.|
|Öneri|<strong>İçine veya dışına bu değişiklikleri nasıl</strong>sırada bu değişiklikleri yararlanmak bir uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir veya üzeri. Uygulamaya bu değişiklikler aşağıdaki yollardan birini yararlanabilir:<ul><li>Bu, .NET Framework 4.7.2 hedefler. Bu, varsayılan olarak .NET Framework'ü 4.7.2 hedefleyen Windows Forms uygulamaları etkin ya da üzeri değişikliktir.</li><li>.NET Framework 4.7.1 veya önceki bir sürümünü hedefleyen ve eski erişilebilirlik davranışları dışında aşağıdakileri ekleyerek bölgedeyse [AppContext anahtar](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) için <code>&lt;runtime&gt;</code> app.config dosyası ve içinayarlamabölümünü<code>false</code>aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7.2 hedefleyen uygulamalar veya sonraki bir sürümü ve eski korumak istediğiniz davranışı kabul etme eski tip bir kaynak denetim değerini kullanımını açıkça ayarlayarak bu AppContext anahtar <code>true</code>.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|
