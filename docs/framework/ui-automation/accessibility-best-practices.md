---
title: En İyi Erişilebilirlik Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: c6f0f31260ffae43e59703ef53dd7ef30a73320b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180294"
---
# <a name="accessibility-best-practices"></a>En İyi Erişilebilirlik Uygulamaları
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Denetimlerde veya uygulamalarda aşağıdaki en iyi uygulamaların uygulanması, yardımcı teknoloji aygıtları kullanan kişiler için erişilebilirliklerini artırır. Bu en iyi uygulamaların çoğu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] iyi tasarım aodaklanz. Her en iyi uygulama, denetimler veya uygulamalar için [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulama bilgilerini içerir. Çoğu durumda, bu en iyi uygulamaları karşılamak için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] çalışma zaten denetimleri dahildir.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Programlı Erişim  
 Programlı erişim, tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin etiketlendiğini, özellik değerlerinin açığa alınmasını ve uygun olayların yükseltilmesini sağlar. Standart [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimler için, bu çalışmanın <xref:System.Windows.Automation.Peers.AutomationPeer>çoğu zaten . Özel denetimler, programatik erişimin doğru şekilde uygulandığından emin olmak için ek çalışma gerektirir.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Tüm Kullanıcı Ve Özel Eğitim Öğelerine ve Metne Programlı Erişimi Etkinleştirme  
 Kullanıcı arabirimi (UI) öğeleri programlı erişimi etkinleştirmelidir. Standart [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir denetim varsa, programlı erişim desteği denetime dahil edilir. Denetim özel bir denetimse – ortak bir denetimden veya Denetim'den alt sınıflanmış bir denetimden alt <xref:System.Windows.Automation.Peers.AutomationPeer> sınıflanmış bir denetim - o zaman değiştirilmesi gereken alanlar için uygulamayı denetlemeniz gerekir.  
  
 Bu en iyi uygulamayı takiben yardımcı teknoloji satıcılarının ürününüzün [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]elemanlarını tanımlamasına ve işlemesine olanak tanır.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Kullanıcı Sayısı Nesnelerine, Çerçevelere ve Sayfalara İsimler, Başlıklar ve Açıklamalar Yerleştirme  
 Yardımcı teknolojiler, özellikle ekran okuyucular, gezinti düzeninde çerçevenin, nesnenin veya sayfanın konumunu anlamak için başlığı kullanır. Bu nedenle, başlık çok açıklayıcı olmalıdır. Örneğin, kullanıcı belirli bir alanda derinden gezinmişse, "Microsoft Web Sayfası"nın bir Web sayfası başlığı işe yaramaz. Açıklayıcı bir başlık, görme engelliler ve ekran okuyuculara bağımlı olan kullanıcılar için çok önemlidir. Benzer şekilde, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimler için <xref:System.Windows.Automation.AutomationProperties.NameProperty> ve <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> yardımcı teknoloji aygıtları için önemlidir.  
  
 Bu en iyi uygulamanın ardından yardımcı teknolojilerin [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] örnek denetimleri ve uygulamalarında tanımlanmasına ve manipüle edilmesine olanak tanır.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Programlı Olayların Tüm UI Etkinlikleri Tarafından Tetiklendirilmesini Sağlayın  
 Bu en iyi uygulamayı takiben yardımcı teknolojiler, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yardımcı teknolojideki değişiklikleri dinlemelerine ve kullanıcıyı bu değişiklikler hakkında bilgilendirmelerine olanak tanır.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Kullanıcı Ayarları  
 Bu bölümdeki en iyi uygulama, denetimlerin veya uygulamaların kullanıcı ayarlarını geçersiz kılmamasını sağlar.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Tüm Sistem Genelindeki Ayarlara Saygı Gösterin ve Erişilebilirlik Fonksiyonlarına Müdahale Etmeyin  
 Kullanıcılar, sistem genelinde bazı bayraklar ayarlamak için Denetim Masası'nı kullanabilir; diğer bayraklar programlı olarak ayarlanabilir. Bu ayarlar denetimler veya uygulamalar tarafından değiştirilmemelidir. Ayrıca, uygulamalar ana bilgisayar işletim sisteminin erişilebilirlik ayarlarını desteklemelidir.  
  
 Bu en iyi uygulamadan sonra, kullanıcıların erişilebilirlik ayarlarını ayarlamasına ve bu ayarların uygulamalar tarafından değiştirilmeyeceğini bilmelerine olanak tanır.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Görsel UI Tasarım  
 Bu bölümdeki en iyi uygulamalar, denetimlerin veya uygulamaların renk ve görüntüleri etkin bir şekilde kullanmasını ve Yardımcı teknolojiler tarafından kullanılabilmesini sağlar.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Renkleri Sabit Kodlamayın  
 Renk körü olan, görme güçlüğü çeken veya siyah beyaz ekran kullanan kişiler, sabit kodlu renklere sahip uygulamaları kullanamayabilir.  
  
 Bu en iyi uygulamadan sonra, kullanıcıların bireysel ihtiyaçlara göre renk birleşimlerini ayarlamalarına olanak tanır.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Yüksek Karşıtlığı ve Tüm Sistem Görüntü Özelliklerini Destekle  
 Uygulamalar, kullanıcı tarafından seçilen, sistem genelindeki kontrast ayarlarını, renk seçimlerini veya sistem genelindeki diğer ekran ayarlarını ve özniteliklerini bozmamalı veya devre dışı etmememelidir. Kullanıcı tarafından benimsenen sistem genelindeki ayarlar uygulamaların erişilebilirliğini artırır, böylece uygulamalar tarafından devre dışı bırakılmamalı veya göz ardı edilmemelidir. Renk, doğru kontrast sağlamak için doğru ön plan-arka plan kombinasyonu kullanılmalıdır. İlişkisiz renkler karıştırılmamalı ve renkler ters çevrilmemelidir.  
  
 Birçok kullanıcı, siyah arka plandaki beyaz metin gibi belirli yüksek karşıtlıklı kombinasyonlar gerektirir. Beyaz arka plandaki siyah metin arka planın ön planda kanamasına neden olduğu ve bazı kullanıcılar için okumayı zorlaştırabileceği nden, bunları tersine çizmek.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Herhangi bir DPI Ayarına Göre Tüm UI'nin Doğru Ölçeklendirildirdiğinden emin olun  
 Tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] doğru inç başına herhangi bir nokta (dpi) ayarı tarafından ölçeklenebilir emin olun. Ayrıca, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemanların inç başına 120 nokta (dpi) ile 1024 x 768 ekrana sığdığından emin olun.  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Gezinti  
 Bu bölümdeki En İyi Uygulamalar, denetimler ve uygulamalar için gezintinin ele alınmasını sağlar.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Tüm UI Öğeleri için Klavye Arabirimi Sağlayın  
 Sekme durur, özellikle dikkatlice planlandığında, kullanıcılara gezinmek için başka bir yol [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]verin.  
  
 Uygulamalar aşağıdaki klavye arabirimlerini sağlamalıdır:  
  
- düğmeler, bağlantılar veya liste kutuları gibi kullanıcının etkileşimkurabileceği tüm denetimler için sekme durakları  
  
- mantıksal sekme sırası  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Klavye Odağı göster  
 Kullanıcıların tuş vuruşlarının etkisini öngörebilmeleri için klavye odağına sahip olan nesnenin olması gerekir. Klavye odağı vurgulamak için, dikdörtgenler veya büyütme gibi renkleri, yazı tiplerini veya grafikleri kullanın. Klavye odağının sesli olarak vurgulanması için ses düzeyini, perdeyi veya ton kalitesini değiştirin.  
  
 Karışıklığı önlemek için, uygulamalar etkin olmayan pencerelerde (veya bölmelerde) bulunan tüm görsel odak göstergelerini ve loş seçimleri gizlemelidir.  
  
 Uygulamalar klavye odaklama ile aşağıdakileri yapmalıdır:  
  
- bir öğe her zaman klavye odağı olmalıdır  
  
- klavye odağı görünür ve açık olmalıdır  
  
- seçimler ve/veya odaklanmış öğeler görsel olarak vurgulanmalıdır  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Destek Navigasyon Standartları ve Güçlü Navigasyon Şemaları  
 Klavye gezintisinin farklı yönleri, kullanıcıların [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamalar aşağıdaki klavye arabirimlerini sağlamalıdır:  
  
- tüm komutlar, menüler ve denetimler için kısayol tuşları ve altı çizili erişim tuşları  
  
- önemli bağlantılara klavye kısayolları  
  
- tüm menü öğelerinin bir erişim anahtarı vardır; tüm düğmelerde hızlandırıcı tuşları vardır, tüm komutların bir hızlandırıcı tuşu vardır.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Fare Konumunun Klavye Gezintisine Müdahale Etmesine İzin Vermeyin  
 Fare konumu klavye gezintisi ile müdahale etmemelidir. Örneğin, fare bir yere konumlandırılmışsa ve kullanıcı klavyede geziniyorsa, kullanıcı tarafından başlatılmadığı sürece fare tıklaması gerçekleşmemelidir.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Multimodal Arayüz  
 Bu bölümdeki En İyi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Uygulamalar, uygulamanın görsel öğeler için alternatifler içermesini sağlar.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Metin Olmayan Öğeler için Kullanıcı Tarafından Seçilebilir Eşdeğerler Sağlayın  
 Metin olmayan her öğe için, alt metin, altyazılar veya görsel geri bildirim gibi metin, transkript veya ses açıklamaları için kullanıcı tarafından seçilebilir bir eşdeğer sağlayın.  
  
 Metin dışı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler, resimler, görüntü haritası bölgeleri, animasyonlar, uygulamalar, kareler, komut dosyaları, grafik düğmeler, sesler, bağımsız ses dosyaları ve video gibi çok çeşitli öğeleri kapsar. Metin dışı öğeler, kullanıcının içeriğini anlamak için erişmesi gereken görsel bilgiler, konuşmalar veya genel [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ses bilgileri içerdiklerinde önemlidir.  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Renk Kullanın ama Aynı zamanda Renk Alternatifleri sağlayın  
 Başka yollarla gösterilen bilgileri geliştirmek, vurgulamak veya yinelemek için rengi kullanın, ancak renkleri tek başına kullanarak bilgileri iletmeyin. Renk körü veya tek renkli ekrana sahip kullanıcıların renk alternatiflerine ihtiyacı vardır.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Aygıt-Bağımsız Aramalarla Standart Giriş API'lerini Kullanma  
 Cihazdan bağımsız aramalar klavye ve fare özelliği eşitliğini sağlarken, yardımcı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]teknoloji hakkında gerekli bilgileri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.Peers>
- [Tema ve UI Otomasyon Destek Örneği ile SayısalUpDown Özel Kontrol](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Klavye Kullanıcı Arabirimi Tasarımı Kılavuzu](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
