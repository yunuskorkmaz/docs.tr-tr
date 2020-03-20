---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859134"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>İş akışı denetimleri MD5'ten SHA1'e değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile hata ayıklamayı desteklemek için, İş Akışı çalışma zamanı karma algoritması kullanarak bir iş akışı örneği için bir denetim çalışması oluşturur. .NET Framework 4.6.2 ve önceki sürümlerinde, iş akışı denetimi karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullanmıştır. .NET Framework 4.7 ile başlayarak algoritma SHA1'dir. Kodunuz bu denetimleri kalıcı olarak verdiyse, bunlar uyumsuz olacaktır.|
|Öneri|Kodunuz bir checksum hatası nedeniyle iş akışı örneklerini yükleyemiyorsa Switch.System.Activities.UseMD5ForWFDebugger'ı <code>AppContext</code> &quot;&quot; doğru ayarlamayı deneyin. Kod olarak:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Veya yapılandırmada:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
