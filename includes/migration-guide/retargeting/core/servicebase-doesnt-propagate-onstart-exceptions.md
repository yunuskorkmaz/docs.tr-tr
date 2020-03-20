---
ms.openlocfilehash: 1148d040aa3b292d5c37eb50224413b6ddd202e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859007"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase OnStart özel durumlarını yaymaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ve önceki sürümlerde, hizmet başlatmada atılan özel <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>durumlar.<br/>.NET Framework 4.7.1'i hedefleyen uygulamalardan başlayarak, çalışma zamanı <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> başlatılamayan hizmetler için özel durumları yayır.|
|Öneri|Hizmet başlangıcında, bir özel durum varsa, bu özel durum yayılır. Bu, hizmetlerin başlatılamadığı durumları tanılamaya yardımcı olur. <br/>Bu davranış istenmeyen ise, uygulama yapılandırma &lt;dosyanızın&gt; &lt;çalışma süresi&gt; bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyerek bu davranışı devre dışı bırakmak olabilir:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Uygulamanız 4.7.1'den daha önceki bir sürümü hedefliyorsa ancak &lt;bu davranışı&gt; istiyorsanız, &lt;uygulama&gt; yapılandırma dosyanızın çalışma zamanı bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyin:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|
