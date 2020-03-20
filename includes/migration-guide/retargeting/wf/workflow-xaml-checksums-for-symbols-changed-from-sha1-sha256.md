---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803505"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>SHA1'den SHA256'ya değiştirilen semboller için iş akışı XAML kontrolleri

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile hata ayıklamayı desteklemek için, İş Akışı çalışma zamanı karma algoritması kullanarak bir iş akışı XAML dosyası için bir denetim çalışması oluşturur. .NET Framework 4.6.2 ve önceki sürümlerinde, iş akışı denetimi karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullanmıştır. .NET Framework 4.7 ile başlayarak varsayılan algoritma SHA1 olarak değiştirildi. .NET Framework 4.8 ile başlayarak varsayılan algoritma SHA256 olarak değiştirildi.|
|Öneri|Kodunuz iş akışı örneklerini yükleyemiyorsa veya bir checksum hatası nedeniyle <code>AppContext</code> uygun &quot;sembolleri bulamıyorsa Switch.System.Activities.UseSHA1HashForDebuggerSymbols'ı&quot; doğru ayarlamayı deneyin. Kod olarak:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Veya yapılandırmada:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
