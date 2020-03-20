---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887847"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>ASP.NET.NET Çerçevesi 4.7.1'de Erişilebilirlik İyileştirmeleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayan ASP.NET, ASP.NET müşterileri daha iyi desteklemek için ASP.NET Web Controls'ün Visual Studio'daki erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirdi.  Bunlar aşağıdaki değişiklikleri içerir:<ul><li>Ayrıntılar Görünümü sihirbazındaki Alan Ekle iletişim kutusu veya ListView sihirbazının Yapılandırılmış ListView iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik desenleri uygulamak için değişiklikler.</li><li>Veri Çağrı Alanı Alanları Düzenleyicisi gibi Yüksek Karşıtlık modunda ekranı geliştirmek için değişiklikler.</li><li>DataPager denetiminin Çağrı Cihazı Alanları Sihirbazı Sihirbazı sihirbazı, ObjectContext'ı Yapılandırışla iletişim kutusu veya Yapılandır Veri Kaynağı sihirbazının Yapılandır Veri Selction iletişim kutusu gibi denetimler için klavye gezintisi deneyimlerini geliştirmek için yapılan değişiklikler.</li></ul>|
|Öneri|**Bu değişiklikleri nasıl tercih edin veya çıkar**<br>Visual Studio Tasarımcısı'nın bu değişikliklerden yararlanabilmesi için .NET Framework 4.7.1 veya sonraki yerlerde çalışması gerekir. Web uygulaması aşağıdaki şekillerden herhangi biri bu değişikliklerden yararlanabilir:<ul><li>Varsayılan olarak aşağıdaki AppContext Switch ile yeni erişilebilirlik özelliklerini destekleyen Visual Studio 2017 15.3 veya sonraki öğeleri yükleyin.</li><li>Devenv.exe.config dosyasındaki <code>Switch.UseLegacyAccessibilityFeatures</code> <code>&lt;runtime&gt;</code> bölüme AppContext anahtarını ekleyerek ve aşağıdaki örnekte görüldüğü gibi <code>false</code>, eski erişilebilirlik davranışlarını devre dışı bırakmak.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1 veya daha sonrasını hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını <code>true</code>açıkça ayarlayarak eski erişilebilirlik özelliklerinin kullanımını seçebilir.|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
