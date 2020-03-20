---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859240"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>WCF taşıma güvenliği CNG kullanılarak depolanan sertifikaları destekler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, WCF aktarım güvenliği Windows Şifreleme Kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler. Bu destek, en fazla 32 bit uzunluğunda bir üse sahip ortak anahtara sahip sertifikalarla sınırlıdır. Bir uygulama .NET Framework 4.6.2'yi hedefaldığında, bu özellik varsayılan olarak açıktır. .NET Framework'ün önceki sürümlerinde, CSG anahtar depolama sağlayıcısıyla X509 sertifikalarını kullanma girişimi bir özel durum oluşturur.|
|Öneri|.NET Framework 4.6.1 ve daha öncesini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalar, app.config veya web.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek CNG sertifikaları için destek sağlayabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Bu, aşağıdaki kodla programlı olarak da yapılabilir:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Bu değişiklik nedeniyle, cng sertifikası ile güvenli iletişim başlatma girişimine bağlı olan herhangi bir özel durum işleme kodunun artık yürütülmeyeceğini unutmayın.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
