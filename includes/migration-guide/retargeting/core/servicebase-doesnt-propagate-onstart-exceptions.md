---
ms.openlocfilehash: 1148d040aa3b292d5c37eb50224413b6ddd202e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759538"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase OnStart özel durumları yayar değil

|   |   |
|---|---|
|Ayrıntılar|Hizmet başlangıç sırasında oluşturulan özel durumlar .NET Framework 4.7 ve önceki sürümlerle çağırana yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>.NET Framework 4.7.1'i hedefleyen uygulamalar ile başlayarak, çalışma zamanı özel durumları yayar <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> hizmetler başlatılamaz.|
|Öneri|Bir özel durum ise hizmet Başlat, o özel durumu yayılır. Bu, burada başlatmak için hizmetler başarısız durumda tanılanmasına yardımcı olmak. <br/>Bu davranış, istenmeyen ise, dışında aşağıdakileri ekleyerek seçebilirsiniz &lt;AppContextSwitchOverrides&gt; öğesine &lt;çalışma zamanı&gt; , uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Uygulamanızı 4.7.1 daha önceki bir sürümü hedefliyorsa, ancak bu davranışı olmasını istediğiniz aşağıdakileri ekleyin &lt;AppContextSwitchOverrides&gt; öğesine &lt;çalışma zamanı&gt; uygulamanızın bir bölümünü yapılandırma dosyası:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|
