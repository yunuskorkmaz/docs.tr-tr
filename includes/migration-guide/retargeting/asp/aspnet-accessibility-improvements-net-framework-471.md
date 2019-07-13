---
ms.openlocfilehash: 100b34941b045619c7424921f9315e679f173a60
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858984"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 ASP.NET erişilebilirlik geliştirmeleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, ASP.NET, ASP.NET Web denetimleri ile daha iyi destek ASP.NET müşterileri için erişilebilirlik teknolojisinin Visual Studio'da nasıl geliştirdi.  Bunlar aşağıdaki değişiklikleri içerir:<ul><li>Denetimleri içinde eksik kullanıcı Arabirimi erişilebilirliği desenleri uygulamak için değişiklikler, alan Ekle iletişim kutusunun Ayrıntılar görünümü sihirbazında veya ListView Sihirbazı ListView yapılandırma iletişim gibi.</li><li>Yüksek karşıtlık modunda, çağrı cihazı veri alanları Düzenleyicisi gibi görünen geliştirmek üzere değiştirir.</li><li>Klavye ile gezintiyi iyileştirmeye yönelik değişiklikler deneyimleri alanları iletişim çağrı alanları düzenleme Sihirbazı'nın DataPager denetimi, ObjectContext Yapılandır iletişim kutusu veya veri kaynağı Yapılandırma Sihirbazı'nın veri Selction Yapılandır iletişim kutusunda gibi denetimler için.</li></ul>|
|Öneri|<strong>İçine veya dışına bu değişiklikleri nasıl</strong>sırada bu değişiklikleri yararlanmak Visual Studio tasarımcısı için .NET Framework 4.7.1 çalıştırmanız gerekir veya üzeri. Web uygulaması bu değişiklikler aşağıdaki yollardan birini yararlanabilir:<ul><li>Visual Studio 2017 15.3 yükleyebilir veya daha sonra varsayılan olarak aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özelliklerini destekler.</li><li>Eski erişilebilirlik davranışları dışında ekleyerek iyileştirilmiş <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext anahtara <code>&lt;runtime&gt;</code> bölümü devenv.exe.config dosyasında ve bu ayarın <code>false</code>aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1'i hedefleyen uygulamalar veya üzeri ve eski korumak istiyorsanız erişilebilirlik davranışı kabul etme eski erişilebilirlik özelliklerinin kullanımı için açıkça ayarlayarak bu AppContext anahtar <code>true</code>.|
|`Scope`|Küçük|
|Version|4.7.1|
|Type|Yeniden Hedefleme|

