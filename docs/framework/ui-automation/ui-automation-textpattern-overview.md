---
title: UI Otomasyon TextPattern Öğesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: ea03c037312ffdb66146dc0461e157c230aafcd2
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304056"
---
# <a name="ui-automation-textpattern-overview"></a>UI Otomasyon TextPattern Öğesine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin denetimlerini, biçimi ve stil öznitelikleri dahil olmak üzere, metinsel içeriği ortaya çıkarmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-desteklenen platformlar. Bu denetimler içerir, ancak Microsoft .NET Framework için sınırlı <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> yanı sıra bunların [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] eşdeğerleri.  
  
 Denetiminin metin içeriğini gösterme kullanımının gerçekleştirilir <xref:System.Windows.Automation.TextPattern> metin akışına olarak bir metin kapsayıcı içeriğini temsil eden denetim düzeni. Buna karşılık, <xref:System.Windows.Automation.TextPattern> desteğini gerektirir <xref:System.Windows.Automation.Text.TextPatternRange> biçimi ve stili özniteliklerini göstermek için sınıf. <xref:System.Windows.Automation.Text.TextPatternRange> destekleyen <xref:System.Windows.Automation.TextPattern> bitişik temsil eden tarafından veya birden çok metin yayılma koleksiyonuyla metin kapsayıcısında ayrık <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ve <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktaları. <xref:System.Windows.Automation.Text.TextPatternRange> Seçim, karşılaştırma, alma ve geçişi gibi işlevleri destekler.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> Sınıfları Ekle veya metin değiştirme olanağı sağlamaz. Ancak, denetimin bağlı olarak bu tarafından gerçekleştirilmesi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> veya doğrudan klavye girdisi aracılığıyla. Bkz: [textpattern öğesine Ekle metin örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) örneği.  
  
 Bu genel bakışta tanımlanan işlevselliği, yardımcı teknoloji satıcılar ve son kullanıcıları için önemlidir. Yardımcı teknolojiler kullanabileceğiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tam metin biçimlendirme için kullanıcı bilgilerini toplayın ve programlı gezinti ve metin seçimi <xref:System.Windows.Automation.Text.TextUnit> (karakter, sözcük, satır veya paragrafa).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>UI Otomasyon TextPattern vs. Metin hizmetleri altyapısı  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] doğal dil Hizmetleri ve Gelişmiş metin Masaüstü ve uygulamaları içinde girişi sağlayan bir basit ve ölçeklenebilir sistem çerçevedir. Uygulamaların metin depolarındaki kullanıma sunmak arabirimleri sağlamanın yanı sıra ayrıca meta veriler, metin depolama için destekler.  
  
 Ancak, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] ise bağlama duyarlı senaryolarına giriş eklemeye gerek duyan uygulamalar için tasarlanmıştır <xref:System.Windows.Automation.TextPattern> olduğu bir salt okunur çözümüyle (yukarıda belirtilen sınırlı geçici çözüm) amacı, bir metin depolama için iyileştirilmiş erişim sağlamak Ekran Okuyucu ve Braille cihazlar.  
  
 Kısacası, bir metin deposu salt okunur erişim gerektiren erişilebilir teknolojilerini kullanabilirsiniz <xref:System.Windows.Automation.TextPattern>, ancak daha karmaşık işlevselliğini artırır [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] bağlama duyarlı giriş.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Denetim türleri  
  
#### <a name="text"></a>Metin  
 Metin denetimini temsil eden bir ekrana metnin temel öğesidir.  
  
 Tek başına metin denetimi, bir etiket ya da bir form üzerinde statik metin olarak kullanılabilir. Metin denetimi de yer almalıdır yapısı içinde bir <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> veya <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Metin denetimi, içerik görünümünde görünmeyebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç (bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Metin denetimi genellikle başka bir denetimin Name özelliği görüntülenen olmasıdır. Örneğin, bir düzenleme denetimi etiketlemek için kullanılan metin düzenleme denetiminin Name özelliği kullanıma sunulur. Düzenleme denetimi içerik görünümünde olduğundan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı, bunu değil metin öğenin kendisinin bu görünümde olmasını gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç. İçerik görünümünde gösterilir yalnızca metin, yedekli bilgiler metindir. Bu, yalnızca kullanıcıları gereken bilgi parçalarını üzerinde hızlı bir şekilde filtrelemek herhangi bir yardımcı teknoloji sağlar.  
  
#### <a name="edit"></a>Düzenle  
 Denetimleri etkinleştirme görüntülemek ve tek satırlık metin düzenlemek için kullanıcıyı düzenleyin.  
  
> [!NOTE]
>  Tek satırlık metin düzeni belirli senaryolarda sarmalamanız.  
  
#### <a name="document"></a>Belge  
 Gidin ve birden çok metin sayfalarından bilgi edinme bir kullanıcı belge denetimleri sağlar.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern istemci API'SİNİN  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|Giriş noktası [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin modeli.<br /><br /> Bu sınıf ayrıca iki içeren <xref:System.Windows.Automation.TextPattern> olay dinleyicileri <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> ve <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|Destekleyen bir metin kapsayıcı içinde metin gösterimini <xref:System.Windows.Automation.TextPattern>.<br /><br /> UI Otomasyon istemcileri kullanılarak oluşturulan bir metin aralığı geçerli geçerliliğini hakkında dikkatli <xref:System.Windows.Automation.Text.TextPatternRange>. Orijinal metni metin denetiminde tamamen yeni metin tarafından değiştirilir, geçerli metin aralığı geçersiz hale gelir. Ancak, metin aralığı yine de bazı letim gereksinimlerinin yalnızca özgün metnin bir parçası olarak değiştirilir ve temel alınan metin denetimi, metin yönetme "işaretçi" bağlayıcılarını (veya uç noktaları) yerine mutlak karakter konumlandırma ile olabilir.<br /><br /> İstemciler dinlemek için bir <xref:System.Windows.Automation.TextPattern.TextChangedEvent> bunlar çalıştığınız metin içeriği için herhangi bir değişiklik bildirimi.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Bir metin aralığını biçimlendirme öznitelikleri tanımlamak için kullanılır.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern sağlayıcısı API  
 Kullanıcı Arabirimi öğeleri veya denetimleri destekleyen <xref:System.Windows.Automation.TextPattern> uygulayarak <xref:System.Windows.Automation.Provider.ITextProvider> ve <xref:System.Windows.Automation.Provider.ITextRangeProvider> , ya da yerel olarak arabirimleri aracılığıyla veya [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy'leri, içerdikleri içinde herhangi bir metin için ayrıntılı öznitelik bilgileri gösterme özellikli güçlü Gezinti özellikleri sağlayarak yanı sıra.  
  
 A <xref:System.Windows.Automation.TextPattern> denetim herhangi belirli öznitelikler için destek yoksa, tüm metin özniteliklerini desteklemek sağlayıcı yok.  
  
 A <xref:System.Windows.Automation.TextPattern> sağlayıcısı desteklemelidir <xref:System.Windows.Automation.TextPattern.GetSelection%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> denetim metin alanı içinde metin seçimi veya metin imleç (ya da sistem giriş işaretini) yerleşimini destekliyorsa çalışır. Denetim bu işlevleri desteklemiyorsa, bu yöntemlerden birini destekleyen gerekmez. Ancak denetim metin seçimi destekleyen uygulayarak türünü kullanıma sunması <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> özelliği.  
  
 A <xref:System.Windows.Automation.TextPattern> sağlayıcısı her zaman desteklemelidir <xref:System.Windows.Automation.Text.TextUnit> sabitleri <xref:System.Windows.Automation.Text.TextUnit.Character> ve <xref:System.Windows.Automation.Text.TextUnit.Document> yanı sıra diğer <xref:System.Windows.Automation.Text.TextUnit> sabitleri olduğu destekleme özelliğine sahiptir.  
  
> [!NOTE]
>  Sağlayıcı desteği için belirli bir atlayabilirsiniz <xref:System.Windows.Automation.Text.TextUnit> sonraki erteleniyor tarafından en büyük <xref:System.Windows.Automation.Text.TextUnit> şu sırayla desteklenen: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, ve <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Yöntemler, özellikler ve Destek öznitelikleri sunan <xref:System.Windows.Automation.TextPattern> istemci uygulamalarında (bkz <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Bir metin sağlayıcısı metinde temsil eder (bkz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Metin sağlayıcıları için tanımlayıcı olarak kullanılan değerleri içerir (bkz <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Mimarisi güvenlikten ödün tasarlanmıştır (bkz [UI Otomasyon güvenliğine genel bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). Ancak, bu genel bakışta açıklanan TextPattern sınıfları bazı belirli güvenlik konuları gerektirir.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin sağlayıcıları, salt okunur arabirimleri sağlayın ve var olan bir denetimdeki metin değiştirme olanağı sağlamaz.  
  
-   UI Otomasyon istemcileri yalnızca kullanma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tam olarak "güvenilen" olmaları durumunda. Buna örnek olarak, burada yalnızca bilinen ve güvenilen uygulamaları çalıştıracak şekilde korumalı oturum açma Masaüstü olacaktır.  
  
-   UI Otomasyonu sağlayıcıları geliştiriciler tüm bilgileri bunlar kendi denetimlerinde kullanıma sunmak seçtiğiniz kullanan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] temelde genel ve diğer kod tarafından tam olarak erişilebilir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] herhangi bir UI Otomasyon istemcisi ve bu nedenle UI Otomasyon sağlayıcısında güvenilirliğini korumalı içerik veya gizli metin bilgilerini (örneğin, parola alanları) kullanıma sunmamalıdır belirlemek için çaba göstermez.  
  
-   Güvenlik için en önemli değişikliklerden biri [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] problem için "Güvenli en az ayrıcalıklı (veya sınırlı) gibi teknolojileri kapsayan girişi" olarak adlandırılır (LUA) kullanıcı hesapları ve kullanıcı Arabirimi ayrıcalık düzeyi yalıtım (UIPI).  
  
    -   UIPI denetleme ve/veya daha fazla "ayrıcalıklı" program, başka bir izleme bir program kullanıcı girişi sızmasını çapraz işlem pencere ileti saldırılarını önleme engeller.  
  
    -   LUA Yöneticiler grubundaki kullanıcılar tarafından çalıştırılan uygulamaların ayrıcalıkları limitler koyar. Uygulamalar, yönetici ayrıcalıklarına sahip olması gerekmez, ancak yerine gerekli en düşük ayrıcalık ile çalışacak. Sonuç olarak, bazı kısıtlamalar LUA senaryolarda zorunlu olabilir. En önemlisi kesilmesi burada uygulama devre dışı bırakma noktasına bellek ayırmak için zorunlu olmayan şekilde yönetici düzeyinde uygulamalardan alınan dize boyutunu sınırlamak gerekebilir (dahil olmak üzere TextPattern dizeler), dize.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Performans  
 Çapraz işlem aramaları işlevselliğinin çoğunluğunun şirket textpattern öğesine bağımlı olduğundan, içeriği işlenirken performansını artırmak için bir önbelleğe alma mekanizması sağlamaz. Bu diğer denetim desenlerini aksine, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , erişilebilir kullanarak <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> yöntemleri.  
  
 Performansı artırmak için bir yöntem olan metin kullanarak, Orta boyutlu bloklarını almak UI Otomasyon istemcileri denemesi sağlayarak <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Örneğin, bir GetText(-1) çağrısı bir işlem içi isabet ödenmesini gerektirir, ancak metin sağlayıcısı boyutuna bağlı olarak yüksek gecikme olabilir ancak GetText(1) çağrıları her karakter için çapraz işlem isabet neden olur.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>TextPattern terminolojisi  
 **Öznitelik**  
 Bir metin aralığını biçimlendirme özelliği (örneğin, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> veya <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Bozabilirler aralığı**  
 Bozuk bir boş veya sıfır karakter metin aralığı aralıktır. TextPattern denetim düzeni amacı doğrultusunda, bozuk bir aralık metin ekleme noktasını (veya sistem giriş işareti) olarak kabul edilir. Hiçbir metin seçili değilse <xref:System.Windows.Automation.TextPattern.GetSelection%2A> metin ekleme noktasını bozuk bir aralığa döndürür ve <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> bozuk bir aralık, başlangıç uç noktası olarak döndürür. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ve <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> metin sağlayıcı belirtilen koşulu ile eşleşen hiçbir metin aralığı bulamadığında bozuk aralıkları döndürebilir. Bozuk bu aralık içinde metin sağlayıcısı başlayan bir uç nokta olarak kullanılabilir. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> null bir başvuru döndürür (`Nothing` Microsoft Visual Basic. NET'te) bozuk aralığı karşı bulunan bir aralıkla Karışıklığı önlemek için.  
  
 **Eklenen nesne**  
 Katıştırılmış nesneler iki tür vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin modeli. İçerik öğeleri Köprüler veya tablolar gibi metin tabanlı ve denetim öğeleri görüntüler ve düğmeler gibi oluşur. Daha ayrıntılı bilgi için bkz. [erişim katıştırılmış nesneleri kullanarak UI Otomasyonu](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Uç nokta**  
 Mutlak <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> veya <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> metin kapsayıcı içindeki bir metin aralığı noktasını.  
  
 ![TextPatternRangeEndpoints &#40;başlangıç ve bitiş&#41;. ](../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
Başlangıç ve bitiş noktaları kümesi gösterilmektedir.  
  
 **TextRange**  
 Başlangıç ve bitiş noktaları, ilişkili tüm öznitelikleri ve işlevleri dahil olmak üzere bir metin kapsayıcıdaki bir metin gösterimi.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Önceden tanımlanmış bir birim (karakter, sözcük, satır veya paragrafa) bir metin aralığını mantıksal parçalarını gezinmek için kullanılan metin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Metin hizmetleri altyapısı](/windows/desktop/api/_tsf/)
