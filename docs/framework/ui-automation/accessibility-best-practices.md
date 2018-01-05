---
title: "En İyi Erişilebilirlik Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 83b4c2ae04ab6be1f1a1327649bbf679a24580ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-best-practices"></a>En İyi Erişilebilirlik Uygulamaları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Aşağıdaki uygulama denetimlerinde en iyi uygulamalar veya uygulamaları kullanan kişiler için kendi erişilebilirlik geliştirmek [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] aygıtlar. Bu en iyi uygulamaları çoğunu iyi üzerinde odaklanmak [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] tasarım. En iyi her uygulama için uygulama bilgileri içerir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimleri ve uygulamaları. Çoğu durumda, bu en iyi uygulamaları karşılamak için çalışma zaten bulunduğundan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim içerir sağlanarak tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri etiketli, özellik değerlerini sunulur ve uygun olayları ortaya çıkar. Standart [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetimleri, çoğu bu iş zaten aracılığıyla yapılır <xref:System.Windows.Automation.Peers.AutomationPeer>. Özel denetimler programlı erişim doğru bir şekilde uygulandığından emin olmak için ek iş gerektirir.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Tüm kullanıcı Arabirimi öğeleri ve metin programlı erişimi etkinleştir  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]öğeleri programlı erişim etkinleştirmeniz gerekir. Varsa [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir standarttır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetlemek, programlı erişim denetimine dahil için destek. Denetim bir özel denetim – ise bir ortak denetimi veya denetim – sonra sınıflandırma bir denetiminden sınıflandırma bir denetim denetlemelisiniz <xref:System.Windows.Automation.Peers.AutomationPeer> değiştirilmesi gerekebilir alanlar için uygulama.  
  
 En iyi yöntemi sağlar [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] tanımlamak ve ürününüzün öğelerini işlemek için Satıcılar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Kullanıcı Arabirimi nesneleri, çerçeve ve sayfa adları, başlıkları ve açıklamaları yerleştirin  
 Yardımcı teknolojiler, özellikle ekran okuyucular başlığı çerçeve, nesne veya sayfa gezinti düzenindeki konumunu anlamak için kullanın. Bu nedenle, başlık çok açıklayıcı olmalıdır. Örneğin, bir Web sayfası başlığı, "Microsoft Web sayfası" kullanıcı derine bazı belirli alanına gezinen varsa gereksizdir. Açıklayıcı bir başlık görme ve ekran okuyucular bağımlı kullanıcılar için önemlidir. Benzer şekilde, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimleri <xref:System.Windows.Automation.AutomationProperties.NameProperty> ve <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> için önemli olan [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] aygıtlar.  
  
 En iyi yöntemi sağlar [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]tanımlamak ve yönetmek için s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] örnek denetimleri ve uygulamaları.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Programsal olayları tüm UI etkinlikleri tarafından tetiklenen emin olun  
 En iyi yöntemi sağlar [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]değişiklikleri dinlemek için s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve kullanıcıyı bu değişiklikler hakkında bilgilendirir.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Kullanıcı ayarları  
 Bu bölümdeki en iyi uygulama denetimleri veya uygulamalar kullanıcı ayarlarını geçersiz kılmaz olduğunu sağlar.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Tüm Sistem genelindeki ayarları dikkate alır ve erişilebilirlik işlevleriyle engel olmaz  
 Kullanıcılar, bazı sistem genelinde bayrakları ayarlamak için Denetim Masası'nı kullanabilirsiniz; diğer bayraklar program aracılığıyla ayarlanabilir. Bu ayarları denetimleri veya uygulamalar tarafından değiştirilmemelidir. Ayrıca, uygulamaları kendi ana bilgisayar işletim sisteminin erişilebilirlik ayarlarını desteklemesi gerekir.  
  
 Bu en iyi yöntem aşağıdaki kullanıcıların Erişilebilirlik ayarlarını ve bu ayarları uygulamalar tarafından değiştirilmeyecek biliyorsanız olanak tanır.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Görsel kullanıcı Arabirimi tasarımı  
 Bu bölümdeki en iyi yöntemler denetimleri ve uygulamaları renk ve görüntüleri verimli kullanmak ve tarafından kullanılması için emin olun [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Renkleri Sabit Kodlamayın  
 Renk görme olan, görme engelli ya da bir siyah beyaz ekran kullanıyorsanız kişiler sabit kodlanmış renklerle uygulamaları kullanmanız mümkün olmayabilir.  
  
 Bu en iyi yöntem aşağıdaki renk birleşimleri tek tek ihtiyaçlarına göre ayarlamak kullanıcıların sağlar.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Destek yüksek karşıtlık ve tüm sistem görüntü öznitelikleri  
 Uygulamaları kesintiye veya kullanıcı tarafından seçilen, sistem genelinde karşıtlık ayarlarını rengi seçimleri veya diğer sistem genelinde görüntü ayarlarını ve öznitelikleri devre dışı bırakmak gerekir. Bunlar devre dışı veya uygulamalar tarafından göz ardı şekilde Sistem genelindeki ayarları bir kullanıcı tarafından benimsenen uygulamaları erişilebilirliğini geliştirin. Renk uygun karşıtlık sağlamak için bunların doğru ön plan üzerinde arka plan birlikte kullanılmalıdır. İlişkisiz renkleri değil mixed olmalıdır ve renkleri ters.  
  
 Çok sayıda kullanıcı siyah bir arka plan üzerinde beyaz metin gibi belirli yüksek karşıtlıklı birleşimleri gerektirir. Bu ters, beyaz bir arka plan üzerinde siyah metin olarak çizim ön taşma için arka plan neden olur ve okuma için bazı kullanıcılar zorlaştırabilir.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Tüm olun UI herhangi DPI ayarı tarafından doğru şekilde ölçekler  
 Emin tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tarafından doğru bir şekilde ölçeklendirebilirsiniz [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ayarı. Ayrıca, emin [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri uygun ekranında 1024 x 768 120 ile [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Gezinme  
 Bu bölümdeki en iyi yöntemler denetimleri ve uygulamaları için Gezinti giderilmiş emin olun.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Tüm kullanıcı Arabirimi öğeleri için klavye arabirimi  
 Sekme durakları, özellikle dikkatle planlanmış zaman vermek kullanıcılar gitmek için bir başka yolu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamaları aşağıdaki klavye arabirimleri sağlamanız gerekir:  
  
-   Kullanıcı, düğmeleri, bağlantılar veya liste kutuları gibi etkileşim kurabildikleri tüm denetimler için sekme durdurur  
  
-   mantıksal sekme sırası  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Klavye odağı Göster  
 Kullanıcılar kendi tuş vuruşları etkisini tahmin böylece hangi nesne klavye odağı olan bilmeniz gerekir. Klavye odağı vurgulamak için renkleri, yazı tipleri ve dikdörtgenler veya büyütme gibi grafik kullanın. Klavye odağı kullanımı vurgulamak için birim, aralık veya ton kalite değiştirin.  
  
 Karışıklığı önlemek için uygulamaların tüm visual odak göstergelerini Gizle ve etkin olmayan windows (veya bölmeleri) bulunan seçimleri dim gerekir.  
  
 Uygulamaları klavye odağını ile aşağıdakileri yapmanız gerekir:  
  
-   bir öğe klavye odağı her zaman gerekir  
  
-   klavye odağı görünür ve belirgin olması gerekir  
  
-   seçimleri ve/veya odaklanmış öğelerini görsel olarak vurgulanmış olması gerekir  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Gezinti standartları ve güçlü Gezinti düzenleri desteği  
 Klavye gezinti farklı yönlerini gitmek kullanıcılar için farklı yollar sağlamak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamaları aşağıdaki klavye arabirimleri sağlamanız gerekir:  
  
-   kısayol tuşları ve tüm komutlar, menüler ve denetimler için altı çizili erişim tuşları  
  
-   önemli bağlantılar için klavye kısayolları  
  
-   tüm menü öğelerini erişim tuşu sahip; Hızlandırıcı tuşları tüm düğmeleri vardır, tüm komutları bir kısayol tuşu sahip.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Fare izin vermeyin konumu müdahale klavye gezinme  
 Fare konumu ile klavye gezinti engellemez. İçin fare ise nedenini bildirmeden bir yerde konumlandırılır ve kullanıcı klavye ile fare değil olacağını kullanıcı tarafından başlatılan sürece gezinme.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Çokdoruklu arabirimi  
 Bu bölümdeki en iyi yöntemler sağlamak, uygulamanın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alternatifleri için görsel öğeleri içerir.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Metin olmayan öğeler için kullanıcı tarafından seçilebilen eşdeğerleri sağlayın  
 Her metin dışı öğesi için metin, dökümleri ya da alternatif metin, resim yazıları veya görsel geribildirim gibi ses açıklamaları için bir kullanıcı tarafından seçilebilen eşdeğer sağlayın.  
  
 Olmayan metin öğelerini kapsayan çok çeşitli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler de dahil olmak üzere: görüntüleri, resim haritası bölgeler, animasyonları, uygulamalarını, çerçeve, komut dosyaları, grafik düğmeleri, ses, tek başına ses dosyaları ve video. Görsel bilgileri, konuşma veya kullanıcı erişimi için içeriği olduğunu anlamak için ihtiyaç duyduğu genel ses bilgilerini içerdiğinde olmayan metin öğelerini önemli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Renk kullanır ancak renk alternatifleri de sağlar  
 Geliştirmek, vurgulamak veya başka yollarla gösterilen bilgileri yinelemek için renk kullanır, ancak yalnızca renk kullanarak bilgi iletişim kurmazlar. Renk görme veya tek renkli ekrana sahip kullanıcıları renk alternatifleri gerekir.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>CİHAZDAN bağımsız aramaları standart giriş API'lerini kullanma  
 CİHAZDAN bağımsız çağrıları sağlarken özelliği eşitlik, klavye ve fare olun [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] ile ilgili bilgiler gerekli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.Peers>  
 [Tema ve UI Otomasyon desteği örnek ile NumericUpDown özel denetimi](http://msdn.microsoft.com/en-us/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Klavye kullanıcı arabirimi tasarım yönergeleri](http://msdn2.microsoft.com/library/ms971323.aspx)
