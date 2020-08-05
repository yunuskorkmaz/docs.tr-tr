---
title: En İyi Erişilebilirlik Uygulamaları
description: .NET ' te erişilebilirlik en iyi uygulamaları hakkında bilgi edinin. Programlı erişimi, Kullanıcı ayarlarını, görsel kullanıcı arabirimi tasarımını, gezinmeyi ve çok kalıcı arabirimleri bulun.
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 2980881bbcd34ca82f6cca7723cf976e0890f463
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557092"
---
# <a name="accessibility-best-practices"></a>En iyi erişilebilirlik uygulamaları

> [!NOTE]
> Bu makale, ad alanında tanımlanan yönetilen UI Otomasyon sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . UI Otomasyonu hakkında en son bilgiler için bkz. [Windows AUTOMATION API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Aşağıdaki en iyi yöntemleri denetimlerde veya uygulamalarda uygulamak, yardımcı teknoloji cihazlarını kullanan kişiler için erişilebilirliğini geliştirir. Bu en iyi uygulamaların birçoğu iyi kullanıcı arabirimi (UI) tasarımına odaklanmaktadır. En iyi yöntemler Windows Presentation Foundation (WPF) denetimleri veya uygulamaları için uygulama bilgilerini içerir. Çoğu durumda, bu en iyi uygulamaları karşılayan iş WPF denetimlerine zaten dahil edilmiştir.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Programlı Erişim  
 Programlı erişim, tüm Kullanıcı arabirimi öğelerinin etiketlenmesini, özellik değerlerinin gösterilmesini ve uygun olayların ortaya çıkmasını sağlar. Standart WPF denetimlerinde, bu çalışmanın çoğu aracılığıyla zaten yapılır <xref:System.Windows.Automation.Peers.AutomationPeer> . Özel denetimler, programlı erişimin doğru bir şekilde uygulandığından emin olmak için ek çalışma gerektirir.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Tüm Kullanıcı Arabirimi öğelerine ve metnine programlı erişimi etkinleştir  
 Kullanıcı arabirimi (UI) öğeleri programlı erişimi etkinleştirmelidir. Kullanıcı arabirimi standart bir WPF denetimi ise, programlı erişim desteği denetime dahil edilir. Denetim özel bir denetim ise (ortak bir denetimden veya denetimin alt sınıflandırıından oluşturulmuş bir denetimden) alt sınıflandırılacak bir denetim – daha sonra, <xref:System.Windows.Automation.Peers.AutomationPeer> değişiklik gerekebilecek alanlara yönelik uygulamayı denetlemeniz gerekir.  
  
 Bu en iyi yöntem, yardımcı teknoloji satıcılarının, ürününüzün Kullanıcı arabirimindeki öğeleri belirlemesine ve işlemesini sağlar.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Kullanıcı arabirimi nesnelerine, çerçevelerine ve sayfalarına ad, başlık ve açıklama yerleştirme  
 Yardımcı teknolojiler, özellikle ekran okuyucular, gezinti düzeninde çerçeve, nesne veya sayfanın konumunu anlamak için başlığı kullanır. Bu nedenle, başlık açıklayıcı olmalıdır. Örneğin, Kullanıcı belirli bir alana daha fazla gezindiyseniz, "Microsoft Web sayfası" Web sayfası başlığı kullanılamaz. Açıklayıcı bir başlık, görme engelli ve ekran okuyucularına bağlı olan kullanıcılar için önemlidir. Benzer şekilde, WPF denetimleri için <xref:System.Windows.Automation.AutomationProperties.NameProperty> ve <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> yardımcı teknoloji cihazları için önemlidir.  
  
 Bu en iyi yöntem, yardımcı teknolojilerin, örnek denetimlerde ve uygulamalarda Kullanıcı arabirimini belirlemesine ve işlemesini sağlar.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Programlı olayların tüm Kullanıcı arabirimi etkinlikleri tarafından tetiklendiğinden emin olun  
 Bu en iyi yöntem, yardımcı teknolojilerin Kullanıcı ARABIRIMINDEKI değişiklikleri dinlemesi ve kullanıcıya bu değişiklikler hakkında bildirim almasına olanak tanır.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Kullanıcı Ayarları  
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
 Uygulamalar, Kullanıcı tarafından seçilen, sistem genelinde karşıtlık ayarlarını, renk seçimlerini veya sistem genelindeki diğer ekran ayarlarını ve özniteliklerini bozmamalıdır veya devre dışı bırakmamalıdır. Bir kullanıcı tarafından benimsenen sistem genelindeki ayarlar uygulamaların erişilebilirliğini geliştirir, bu nedenle uygulamalar tarafından devre dışı bırakılmamalıdır veya gözardı edilmelidir. Renk, doğru karşıtlığı sağlamak için doğru arka plan ön planda kullanılmalıdır. İlişkisiz renkleri karıştırmayın ve renkleri ters kullanmayın.  
  
 Birçok kullanıcı, siyah bir arka planda beyaz metin gibi belirli yüksek karşıtlıklı birleşimler gerektirir. Bu ters çevrilme, beyaz bir arka planda siyah metin olarak çizilerek arka planda taşma ve bazı kullanıcılar için okuma zor hale gelmesine neden olabilir.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Tüm Kullanıcı arabiriminin tüm DPı ayarlarına göre doğru şekilde ölçeklendirdiğinden emin olun  
 Tüm Kullanıcı arabiriminin nokta/inç (dpi) ayarıyla doğru şekilde ölçeklendirebilmesini sağlayın. Ayrıca, Kullanıcı arabirimi öğelerinin 1024 x 768 ekranına, inç başına 120 nokta (DPI) ile uygun olduğundan emin olun.  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Gezinti  
 Bu bölümdeki en iyi uygulamalar, gezintinin denetimler ve uygulamalar için sağlandığından emin olun.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Tüm Kullanıcı arabirimi öğeleri için klavye arabirimi sağla  
 Özellikle dikkatli olarak planlandığınızda, kullanıcıların kullanıcı arabiriminde gezinmek için başka bir yol vermesi için sekme duraklar.  
  
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
 Klavye gezinmesinin farklı yönleri, kullanıcıların kullanıcı arabiriminde gezinmesine yönelik farklı yollar sağlar.  
  
 Uygulamalar aşağıdaki klavye arabirimlerini sağlamalıdır:  
  
- Tüm komutlar, menüler ve denetimler için kısayol tuşları ve altı çizili erişim tuşları  
  
- önemli bağlantılara klavye kısayolları  
  
- tüm menü öğelerinin bir erişim anahtarı vardır; tüm düğmelerin kısayol tuşları vardır, tüm komutlarda kısayol tuşu vardır.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Klavye gezintisi ile fare konumunun kesintiye uğramasını Izin vermeyin  
 Fare konumu klavye gezintisini engellemez. Örneğin, fare bir yere konumlandırılmışsa ve Kullanıcı klavyeyle geziniyorsa Kullanıcı tarafından başlatılmadığı takdirde fare tıklaması gerçekleşmemelidir.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Multimodal arabirimi  
 Bu bölümdeki en iyi uygulamalar, uygulama kullanıcı arabiriminin görsel öğeler için alternatifler içerdiğinden emin olun.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Metin olmayan öğeler için Kullanıcı tarafından seçilebilir eşdeğerleri sağlama  
 Metin olmayan her öğe için, metin, döküm veya görsel geri bildirim gibi metin, döküm veya ses açıklamaları için Kullanıcı tarafından seçilebilir bir eşdeğer belirtin.  
  
 Metin olmayan öğeler; görüntüler, görüntü eşleme bölgeleri, animasyonlar, uygulamalar, çerçeveler, betikler, grafik düğmeleri, sesler, tek başına ses dosyaları ve video dahil olmak üzere çok çeşitli kullanıcı arabirimi öğelerini kapsar. Metin olmayan öğeler, kullanıcının kullanıcı ARABIRIMININ içeriğini anlamak için erişmesi gereken görsel bilgiler, konuşma veya genel ses bilgileri içerdiğinde önemlidir.  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Renk kullanın, ancak renk alternatifleri de sağlar  
 Diğer yollarla gösterilen bilgileri geliştirmek, vurgulamak veya yeniden yinelemek için renk kullanın, ancak yalnızca renk kullanarak bilgileri iletmeyin. Renkleri görme engelli veya tek renkli ekranı olan kullanıcıların renk alternatifleri olmalıdır.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Cihazdan bağımsız çağrılarla standart giriş API 'Lerini kullanma  
 Cihazdan bağımsız çağrılar klavye ve fare özelliği eşitliğini sağlar ve Kullanıcı arabirimi hakkında gerekli bilgileri içeren yardımcı teknolojiler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.Peers>
- [Tema ve UI Otomasyonu desteği örneği ile NumericUpDown özel denetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Klavye Kullanıcı arabirimi tasarımı için yönergeler](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
