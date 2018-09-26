---
title: En İyi Erişilebilirlik Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 60e95d79ae7cd43b79ec4fd79285bfea071f20f8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113140"
---
# <a name="accessibility-best-practices"></a>En İyi Erişilebilirlik Uygulamaları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Aşağıdaki uygulama denetimlerinde en iyi yöntemler veya uygulamalar kullanan kişiler için erişilebilirlik kendi artıracak [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] cihazlar. Bu en iyi uygulamaların çoğu üzerinde iyi odaklanmak [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] tasarım. Her en iyi uygulama bilgisi içeren [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimleri ve uygulamaları. Çoğu durumda, bu en iyi uygulamaları karşılayacak şekilde iş zaten dahildir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim gerektirir sağlanarak tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygun olayları oluştuğunda öğeleri kullananları ve özellik değerlerini sunulur. Standart [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimleri, bu çalışmanın çoğunu zaten aracılığıyla gerçekleştirilir <xref:System.Windows.Automation.Peers.AutomationPeer>. Özel denetimler programlı erişim doğru bir şekilde uygulandığından emin olmak için fazladan iş gerektirir.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Tüm kullanıcı Arabirimi öğeleri ve metin programlı erişimi etkinleştirme  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)] öğeleri programlı erişim izin vermesi gerekir. Varsa [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standardıdır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetlemek, programlı erişim denetimine dahil için destek. Denetim özel denetim – ise bir ortak denetimi veya denetim – sonra sınıflandırma bir denetim sınıflandırma bir denetim denetlemelidir <xref:System.Windows.Automation.Peers.AutomationPeer> uygulama değişikliği gerektirebilecek alanları için.  
  
 Bu en iyi yöntemin izlenmesi sağlayan [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] tanımlamak ve ürününüzün öğelerini yönetmek için Satıcılar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Kullanıcı Arabirimi nesneleri, çerçeveler ve sayfa adları, başlıkları ve açıklamaları yerleştirin  
 Yardımcı teknolojiler, özellikle de ekran okuyucular, çerçeve, nesne veya sayfa gezinti düzenindeki konumunu anlamak için başlık kullanın. Bu nedenle, başlık çok açıklayıcı olmalıdır. Örneğin, bir Web sayfası başlık, "Microsoft Web sayfası" kullanıcı derin belirli bazı alanına geldiyseniz kullanışsızdır. Açıklayıcı bir başlık, görme ve ekran okuyucu bağımlı olan kullanıcılar için önemlidir. Benzer şekilde, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimleri <xref:System.Windows.Automation.AutomationProperties.NameProperty> ve <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> için önemli olan [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] cihazlar.  
  
 Bu en iyi yöntemin izlenmesi sağlayan [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]tanımlamak ve yönetmek için s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] örnek denetimleri ve uygulamaları.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Tüm kullanıcı Arabirimi etkinlikleri tarafından tetiklenen programlı olayları emin olun.  
 Bu en iyi yöntemin izlenmesi sağlayan [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]değişiklikleri dinlemek için s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve bu değişiklikler hakkında kullanıcıyı bilgilendirir.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Kullanıcı ayarları  
 Bu bölümde en iyi uygulama, denetimleri ve uygulamaları kullanıcı ayarlarını geçersiz sağlar.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Tüm Sistem genelindeki ayarları dikkate alır ve erişilebilirlik işlevleriyle müdahale etmez  
 Kullanıcılar, bazı sistem genelinde bayrakları ayarlamak için Denetim Masası'nı kullanabilirsiniz; diğer bayraklar programlı olarak ayarlayabilirsiniz. Bu ayarlar, denetimleri veya uygulamalar tarafından değiştirilmemelidir. Ayrıca, uygulamaları, kendi ana bilgisayar işletim sisteminin erişilebilirlik ayarını desteklemesi gerekir.  
  
 Bu en iyi aşağıdaki kullanıcıların Erişilebilirlik ayarlar ve bu ayarları uygulama tarafından değiştirilmez biliyorsanız olanak tanır.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Görsel kullanıcı Arabirimi tasarımı  
 Bu bölümde en iyi denetimleri ve uygulamaları rengini ve görüntüleri etkili bir şekilde kullanmak ve tarafından kullanılmak üzere mümkün emin olun [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Renkleri Sabit Kodlamayın  
 Kişilerin renk körü olan, görme engelli veya siyah beyaz bir ekran kullanarak uygulamaları sabit kodlanmış renklerle kullanmanız mümkün olmayabilir.  
  
 Bu en iyi aşağıdaki renk birleşimleri gereksinimlerine göre ayarlamak kullanıcıların sağlar.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Yüksek Karşıtlık destek ve tüm sistem görüntü öznitelikleri  
 Uygulamaların kesintiye veya kullanıcı tarafından seçilen, sistem genelinde karşıtlık ayarlarını rengi seçimleri veya diğer sistem genelinde görüntü ayarlarını ve öznitelikleri devre dışı bırakmak gerekir. Böylece bunlar devre dışı veya uygulamalar tarafından göz ardı Sistem genelindeki ayarları bir kullanıcı tarafından benimsenen uygulamaları erişilebilirliğini artırın. Renk uygun karşıtlık sağlamak için bunların doğru ön plan üzerinde arka plan birlikte kullanılmalıdır. İlişkisiz bir renk değil mixed olmalıdır ve renkleri ters.  
  
 Yüksek Karşıtlık şahit, beyaz metinli siyah arka plan üzerinde gibi çok sayıda kullanıcı gerektirir. Bu çevrilen, siyah beyaz arka plan metin olarak çizim ön taşma arka plan neden olur ve okuma için bazı kullanıcılar zorlaştırabilir.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Tüm olun kullanıcı Arabirimi tarafından herhangi bir DPI ayarı doğru şekilde ölçeklendirir  
 Emin tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] göre doğru şekilde ölçeklendirebilirsiniz [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ayarı. Ayrıca, emin [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri sığacak 120 ile 1024 x 768 ekran [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Gezinti  
 Bu bölümde en iyi uygulamalar, denetimleri ve uygulamalar için Gezinti giderilmiş emin olun.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Tüm kullanıcı Arabirimi öğeleri için klavye arabirimi sağlayan  
 Sekme durakları özellikle dikkatle planlanmış, konusunda kullanıcıları gitmek için başka bir yolu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamalar, aşağıdaki klavye arabirimleri sağlamalıdır:  
  
-   Kullanıcının, düğmeler, bağlantılar ve liste kutuları gibi etkileşim tüm denetimler için sekmesinde durdurur  
  
-   mantıksal sekme sırası  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Klavye odağı Göster  
 Kullanıcıların kendi tuş vuruşları etkisini tahmin, böylece nesnenin klavye girintisine sahip bilmeniz gerekir. Klavye odağı vurgulamak için renkleri, yazı tipleri ve dikdörtgenler veya büyütme gibi grafik kullanın. Klavye odağı kullanımı vurgulamak için birim, aralık veya ton kalite değiştirin.  
  
 Karışıklığı önlemek için uygulamaları tüm görsel odak göstergeleri gizleyebilir ve etkin olmayan windows (veya bölmeleri) bulunan seçimleri dim.  
  
 Uygulamaları klavye odağı ile aşağıdakileri yapmalıdır:  
  
-   bir öğe klavye odağı her zaman olmalıdır  
  
-   klavye odağı görünür ve açık olmalıdır  
  
-   Seçim ve/veya odaklanmış öğelerin görsel olarak vurgulanmış olmalıdır  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Gezinti standartlar ve güçlü Gezinti düzenlerini desteği  
 Klavye ile gezinme farklı yönlerini gitmek kullanıcılar için farklı yollar sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamalar, aşağıdaki klavye arabirimleri sağlamalıdır:  
  
-   kısayol tuşları ve tüm komutlar, menüler ve denetimler için altı çizili erişim anahtarları  
  
-   önemli bağlantılar için klavye kısayolları  
  
-   tüm menü öğeleri, bir erişim anahtarı sahip; Tüm düğmeler Hızlandırıcı tuşları varsa, tüm komutları Hızlandırıcı tuşunu sahiptir.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Fare bulunmamasını konumu klavye gezintisi ile müdahale  
 Fare konumu, klavye gezintisi ile engellemez. İçin örnek fare ise, nedenini bildirmeden bir yerde konumlandırılır ve kullanıcı ile klavye, fare tıklatın değil olacağını kullanıcı tarafından başlatılan sürece yönlendirir.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Çokdoruklu arabirimi  
 Bu bölümde en iyi uygulama olun [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alternatifleri için görsel öğeler içerir.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Metin olmayan öğeler için kullanıcı tarafından seçilebilen eşdeğerleri sağlayın  
 Her metin olmayan öğe için metin, dökümleri ya da alternatif metin, resim yazıları veya görsel geri bildirim gibi ses açıklamaları için bir kullanıcı tarafından seçilebilen eşdeğerini sağlar.  
  
 Metin olmayan öğeler kapsayan çok çeşitli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri dahil olmak üzere: görüntüleri, resmi harita bölgelerini, animasyonları, uygulamaları, çerçeveleri, betikleri, grafik düğmeler, ses, tek başına ses dosyalarını ve video. Visual bilgileri, konuşma ve kullanıcı erişimi için içeriğini anlamak için gerektiğini genel ses bilgileri içerdiğinde metin olmayan öğeler önemli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Renk kullanır ancak rengi alternatifleri de sağlar  
 Geliştirmek, vurgulamak veya başka yollarla gösterilen bilgileri yinelemek için renk kullanın, ancak bu bilgileri yalnızca renk kullanarak iletişim kurmazlar. Renk körü veya tek renkli bir görüntüye sahip kullanıcılar, renk alternatifleri gerekir.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>CİHAZDAN bağımsız değişkenli çağrılar standart giriş API'leri kullanın  
 CİHAZDAN bağımsız çağrıları sağlarken klavye ve fare özellik eşitlik sağlamak [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] ile ilgili bilgiler gerekli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.Peers>  
 [NumericUpDown özel denetim teması ve UI Otomasyon desteği örneği](https://msdn.microsoft.com/library/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Klavye kullanıcı arabirimi tasarımı yönergeleri](http://msdn2.microsoft.com/library/ms971323.aspx)
