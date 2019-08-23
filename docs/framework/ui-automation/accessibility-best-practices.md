---
title: En İyi Erişilebilirlik Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: f4096d6441c64499dae8003a63100b59037897ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932772"
---
# <a name="accessibility-best-practices"></a>En İyi Erişilebilirlik Uygulamaları
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Aşağıdaki en iyi yöntemleri denetimlerde veya uygulamalarda uygulamak, yardımcı teknoloji cihazlarını kullanan kişiler için erişilebilirliğini geliştirir. Bu en iyi uygulamaların birçoğu iyi [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] tasarıma odaklanmaktadır. En iyi yöntemler, denetimler veya uygulamalar [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] için uygulama bilgilerini içerir. Çoğu durumda, bu en iyi uygulamaları karşılamak için çalışma zaten [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimlere eklenmiştir.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim, tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin etiketlenmesini, özellik değerlerinin gösterilmesini ve uygun olayların ortaya çıkarılmasını sağlar. Standart [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimler için, bu çalışmanın çoğu aracılığıyla <xref:System.Windows.Automation.Peers.AutomationPeer>zaten yapılır. Özel denetimler, programlı erişimin doğru bir şekilde uygulandığından emin olmak için ek çalışma gerektirir.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Tüm Kullanıcı Arabirimi öğelerine ve metnine programlı erişimi etkinleştir  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]öğeler programlı erişimi etkinleştirmelidir. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Standart[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bir denetim ise, programlı erişim desteği denetime dahil edilir. Denetim özel bir denetim ise (ortak bir denetimden veya denetimin alt sınıflandırıından oluşturulmuş bir denetimden) alt sınıflandırılacak bir denetim – daha sonra, <xref:System.Windows.Automation.Peers.AutomationPeer> değişiklik gerekebilecek alanlara yönelik uygulamayı denetlemeniz gerekir.  
  
 Bu en iyi yöntem, yardımcı teknoloji satıcılarının ürününüzün [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]öğelerini belirlemesine ve işlemesini sağlar.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Kullanıcı arabirimi nesnelerine, çerçevelerine ve sayfalarına ad, başlık ve açıklama yerleştirme  
 Yardımcı teknolojiler, özellikle ekran okuyucular, gezinti düzeninde çerçeve, nesne veya sayfanın konumunu anlamak için başlığı kullanır. Bu nedenle, başlık çok açıklayıcı olmalıdır. Örneğin, Kullanıcı belirli bir alana daha fazla gezindiyseniz, "Microsoft Web sayfası" Web sayfası başlığı kullanılamaz. Açıklayıcı bir başlık, görme engelli ve ekran okuyucularına bağlı olan kullanıcılar için önemlidir. Benzer şekilde, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Automation.AutomationProperties.NameProperty> denetimler için ve <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> yardımcı teknoloji cihazları için önemlidir.  
  
 Bu en iyi yöntem, yardımcı teknolojik, örnek denetimleri ve uygulamaları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] belirlemesine ve değiştirmesine olanak tanır.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Programlı olayların tüm Kullanıcı arabirimi etkinlikleri tarafından tetiklendiğinden emin olun  
 Bu en iyi yöntem, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yardımcı teknolojik içindeki değişiklikleri dinlemek ve kullanıcıya bu değişiklikleri bildirme olanağı sağlar.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Kullanıcı ayarları  
 Bu bölümdeki en iyi yöntem, denetimlerin veya uygulamaların kullanıcı ayarlarını geçersiz kılmamasını sağlar.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Tüm sistem genelinde ayarları dikkate alarak erişilebilirlik Işlevlerini engellemez  
 Kullanıcılar, sistem genelinde bazı bayraklar ayarlamak için Denetim Masası 'nı kullanabilir; diğer bayraklar programlı bir şekilde ayarlanabilir. Bu ayarlar, denetimler veya uygulamalar tarafından değiştirilmemelidir. Ayrıca, uygulamalar, ana bilgisayar işletim sisteminin erişilebilirlik ayarlarını desteklemelidir.  
  
 Bu en iyi yöntem, kullanıcıların erişilebilirlik ayarlarını ayarlamasına ve bu ayarların uygulamalar tarafından değiştirilmediğini bilmesini sağlar.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Görsel kullanıcı arabirimi tasarımı  
 Bu bölümdeki en iyi uygulamalar, denetimlerin veya uygulamaların renk ve görüntüleri etkin şekilde kullanmasını ve yardımcı teknolojiler tarafından kullanılmasını sağlar.  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Renkleri Sabit Kodlamayın  
 Renkli, görme zorluğu olan veya siyah beyaz bir ekran kullanan kişiler, sabit kodlanmış renklerle uygulamaları kullanmayabilir.  
  
 Bu en iyi yöntem, kullanıcıların renk birleşimlerini bireysel gereksinimlere göre ayarlamasına olanak tanır.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Yüksek Karşıtlık ve tüm sistem görüntüleme özniteliklerini destekler  
 Uygulamalar, Kullanıcı tarafından seçilen, sistem genelinde karşıtlık ayarlarını, renk seçimlerini veya sistem genelindeki diğer ekran ayarlarını ve özniteliklerini bozmamalıdır veya devre dışı bırakmamalıdır. Bir kullanıcı tarafından benimsenen sistem genelindeki ayarlar uygulamaların erişilebilirliğini geliştirir, bu nedenle uygulamalar tarafından devre dışı bırakılmamalıdır veya gözardı edilmelidir. Renk, doğru karşıtlığı sağlamak için doğru arka plan ön planda kullanılmalıdır. İlişkisiz renklerin karışık olmaması ve renklerin ters çevrilmemelidir.  
  
 Birçok kullanıcı, siyah bir arka planda beyaz metin gibi belirli yüksek karşıtlıklı birleşimler gerektirir. Bu ters çevrilme, beyaz bir arka planda siyah metin olarak çizilerek arka planda taşma ve bazı kullanıcılar için okuma zor hale gelmesine neden olabilir.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Tüm Kullanıcı arabiriminin tüm DPı ayarlarına göre doğru şekilde ölçeklendirdiğinden emin olun  
 Her bir nokta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] /inç (dpi) ayarı için tümünün doğru şekilde ölçeklendiğinden emin olun. Ayrıca, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin 1024 x 768 ekranına, inç başına 120 nokta (DPI) ile uygun olduğundan emin olun.  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Gezinti  
 Bu bölümdeki en iyi uygulamalar, gezintinin denetimler ve uygulamalar için sağlandığından emin olun.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Tüm Kullanıcı arabirimi öğeleri için klavye arabirimi sağla  
 Özellikle dikkatli bir şekilde planlandığınızda, kullanıcıların ' de gezinmek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]için başka bir yol vermesi için sekme duraklar.  
  
 Uygulamalar aşağıdaki klavye arabirimlerini sağlamalıdır:  
  
- düğme, bağlantılar veya liste kutuları gibi, kullanıcının etkileşime girebileceği tüm denetimler için sekme duraklar  
  
- mantıksal sekme sırası  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Klavye odağını göster  
 Kullanıcıların tuş vuruşlarının etkisini tahmin edebilmesi için hangi nesnenin klavye odağına sahip olduğunu bilmeleri gerekir. Klavye odağını vurgulamak için, renkler, yazı tipleri veya dikdörtgenler ya da büyütme gibi grafikleri kullanın. Klavye odağını sesli olarak vurgulamak için birim, Aralık veya ton kalitesini değiştirin.  
  
 Karışıklıkları önlemek için uygulamalar, etkin olmayan Windows (veya bölmeler) içindeki tüm görsel odak göstergelerini ve karartma seçimlerini gizlemelidir.  
  
 Uygulamalar klavye odağıyla aşağıdakileri yapması gerekir:  
  
- tek bir öğe, her zaman klavye odağına sahip olmalıdır  
  
- klavye odağı görünür ve belirgin olmalıdır  
  
- seçimlerin ve/veya odaklanmış öğelerin görsel olarak vurgulanmış olması gerekir  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Gezinti standartlarını ve güçlü gezinti düzenlerini destekleme  
 Klavye gezinmesinin farklı yönleri, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]kullanıcıların gezinmesinin farklı yollarını sağlar.  
  
 Uygulamalar aşağıdaki klavye arabirimlerini sağlamalıdır:  
  
- Tüm komutlar, menüler ve denetimler için kısayol tuşları ve altı çizili erişim tuşları  
  
- önemli bağlantılara klavye kısayolları  
  
- tüm menü öğelerinin bir erişim anahtarı vardır; tüm düğmelerin kısayol tuşları vardır, tüm komutlarda kısayol tuşu vardır.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Klavye gezintisi ile fare konumunun kesintiye uğramasını Izin vermeyin  
 Fare konumu klavye gezintisini engellemez. Örneğin, fare bir yerde konumlandırılmışsa ve Kullanıcı klavyeyle geziniyorsa Kullanıcı tarafından başlatılmadığı takdirde fare tıklaması gerçekleşmemelidir.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Multimodal arabirimi  
 Bu bölümdeki en iyi uygulamalar, uygulamanın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] görsel öğeler için alternatifler içerdiğinden emin olmanızı sağlamaktır.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Metin olmayan öğeler için Kullanıcı tarafından seçilebilir eşdeğerleri sağlama  
 Metin olmayan her öğe için, metin, döküm veya görsel geri bildirim gibi metin, döküm veya ses açıklamaları için Kullanıcı tarafından seçilebilir bir eşdeğer belirtin.  
  
 Metin olmayan öğeler; görüntüler, görüntü eşleme bölgeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , animasyonlar, uygulamalar, çerçeveler, betikler, grafik düğmeleri, sesler, tek başına ses dosyaları ve video dahil olmak üzere çok çeşitli öğeleri kapsar. Metin olmayan öğeler, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]kullanıcının içeriğini anlamak için erişmesi gereken görsel bilgiler, konuşma veya genel ses bilgileri içerdiğinde önemlidir.  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Renk kullanın, ancak renk alternatifleri de sağlar  
 Diğer yollarla gösterilen bilgileri geliştirmek, vurgulamak veya yeniden yinelemek için renk kullanın, ancak yalnızca renk kullanarak bilgileri iletmeyin. Renkleri görme engelli veya tek renkli ekranı olan kullanıcıların renk alternatifleri olmalıdır.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Cihazdan bağımsız çağrılarla standart giriş API 'Lerini kullanma  
 Cihazdan bağımsız çağrılar klavye ve fare özelliği eşitliğini [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.Peers>
- [Tema ve UI Otomasyonu desteği örneği ile NumericUpDown özel denetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Klavye Kullanıcı arabirimi tasarımı için yönergeler](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
