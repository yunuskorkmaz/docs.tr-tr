---
ms.openlocfilehash: c4b293cf7db3762831be7f3a7a355748ff5758c5
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859007"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase OnStart özel durumları yayar değil

|   |   |
|---|---|
|Ayrıntılar|Hizmet başlangıç sırasında oluşturulan özel durumlar .NET Framework 4.7 ve önceki sürümlerle çağırana yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>.NET Framework 4.7.1'i hedefleyen uygulamalar ile başlayarak, çalışma zamanı özel durumları yayar <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> hizmetler başlatılamaz.|
|Öneri|Bir özel durum ise hizmet Başlat, o özel durumu yayılır. Bu, burada başlatmak için hizmetler başarısız durumda tanılanmasına yardımcı olmak. <br/>Bu davranış, istenmeyen ise, dışında aşağıdakileri ekleyerek seçebilirsiniz &lt;AppContextSwitchOverrides&gt; öğesine &lt;çalışma zamanı&gt; , uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Uygulamanızı 4.7.1 daha önceki bir sürümü hedefliyorsa, ancak bu davranışı olmasını istediğiniz aşağıdakileri ekleyin &lt;AppContextSwitchOverrides&gt; öğesine &lt;çalışma zamanı&gt; uygulamanızın bir bölümünü yapılandırma dosyası:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7.1|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

