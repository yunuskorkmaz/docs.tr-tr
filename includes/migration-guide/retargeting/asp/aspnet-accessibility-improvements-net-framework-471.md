---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887847"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 'de erişilebilirlik Iyileştirmeleri ASP.NET

|   |   |
|---|---|
|Ayrıntılar|4\.7.1, ASP.NET .NET Framework ile başlayarak, ASP.NET müşterilerini daha iyi desteklemek için ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirmiştir.  Bunlar aşağıdaki değişiklikleri içerir:<ul><li>Ayrıntılar görünümü sihirbazındaki alan Ekle iletişim kutusu ya da ListView sihirbazının ListView yapılandırma iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.</li><li>Veri sayfalayıcı alanları Düzenleyicisi gibi Yüksek Karşıtlık modunda görüntüyü geliştirmek için değişiklikler.</li><li>DataPager denetiminin sayfalayıcı alanlarını düzenleme Sihirbazı 'ndaki alanlar iletişim kutusu gibi denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler veya veri kaynağını yapılandırma sihirbazının veri kaynağını Yapılandır</li></ul>|
|Öneri|**Bu değişiklikleri kabul etme veya devre dışı bırakma**<br>Visual Studio Tasarımcısı 'nın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya sonraki bir sürümde çalışmalıdır. Web uygulaması aşağıdaki yollarla bu değişikliklerden faydalanabilir:<ul><li>Varsayılan olarak aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özelliklerini destekleyen Visual Studio 2017 15,3 veya üstünü yükler.</li><li>Devenv. exe. config dosyasındaki <code>&lt;runtime&gt;</code> bölümüne <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext anahtarını ekleyerek ve aşağıdaki örnekte gösterildiği gibi, <code>false</code>olarak ayarlayarak eski erişilebilirlik davranışlarını geri çevirin.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını <code>true</code>olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir.|
|Kapsam|İkincil|
|Version|4.7.1|
|Tür|Yeniden Hedefleme|
