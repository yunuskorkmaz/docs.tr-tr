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
manager: markl
ms.openlocfilehash: e8358a4a4e0b4933670a2f01dfdf4dd9a7aa43cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409886"
---
# <a name="ui-automation-textpattern-overview"></a>UI Otomasyon TextPattern Öğesine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin denetimlerin biçimi ve stil öznitelikleri de dahil olmak üzere metin içeriği kullanıma sunmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-desteklenen platformlar. Bu denetimler içerir, ancak Microsoft .NET Framework sınırlı değildir <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> yanı sıra bunların [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] eşdeğerleri.  
  
 Denetim metin içeriğini gösterme kullanılarak gerçekleştirilir <xref:System.Windows.Automation.TextPattern> metin kapsayıcı olarak bir metin akış içeriğini temsil eden denetim düzeni. Buna karşılık, <xref:System.Windows.Automation.TextPattern> desteği gerektiren <xref:System.Windows.Automation.Text.TextPatternRange> biçimi ve stil öznitelikleri kullanıma sunmak için sınıf. <xref:System.Windows.Automation.Text.TextPatternRange> destekleyen <xref:System.Windows.Automation.TextPattern> bitişik temsil eden tarafından veya birden çok, metin yayılma koleksiyonuyla metin kapsayıcısında ayrık <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ve <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktaları. <xref:System.Windows.Automation.Text.TextPatternRange> Seçimi, karşılaştırma, alma ve çapraz geçişi gibi işlevselliği destekler.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> Sınıfları eklemek veya metin değiştirmek için bir yol sağlamaz. Ancak, denetimin bağlı olarak bu tarafından gerçekleştirilmesi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> veya doğrudan klavye girdisi aracılığıyla. Bkz: [TextPattern Ekle metin örnek](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16) bir örnek.  
  
 Bu genel bakışta açıklanan işlevselliği yardımcı teknoloji satıcılar ve kendi son kullanıcıları için önemlidir. Yardımcı teknolojiler kullanabileceğiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tam metin biçimlendirme kullanıcı için bilgileri toplamak ve programlama gezinme ve seçim tarafından metnin sağlamak için <xref:System.Windows.Automation.Text.TextUnit> (karakter, word, satır veya paragraf).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>UI Otomasyon TextPattern vs. Metin hizmetleri altyapısı  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] doğal dil hizmet ve Gelişmiş metin Masaüstü ve uygulama içinden girişi sağlayan bir basit ve ölçeklenebilir sistem çerçevedir. Metin depolarındaki kullanıma sunmak üzere uygulamalar için arabirim sağlayan ek olarak ayrıca meta veriler için bu metni deposu destekler.  
  
 Ancak, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] ise bağlam algılayan senaryolarına giriş eklemesine gereken uygulamalar için tasarlanmış <xref:System.Windows.Automation.TextPattern> olduğu bir salt okunur çözümüyle (yukarıda belirtilen sınırlı geçici çözüm) amacı bir metin deposu için en iyi duruma getirilmiş erişim sağlamak ekran okuyucuların ve Braille aygıtlar.  
  
 Kısacası, bir metin deposu salt okunur erişim gerektiren erişilebilir teknolojileri kullanabilirsiniz <xref:System.Windows.Automation.TextPattern>, ancak daha karmaşık işlevselliğini gerekir [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] bağlamı algılayan girişi için.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Denetim türleri  
  
#### <a name="text"></a>Metin  
 Metin denetimini temsil eden bir ekran üzerindeki metnin temel öğedir.  
  
 Tek başına metin denetimi, bir etiket veya bir form üzerinde statik metin olarak kullanılabilir. Metin denetimleri de yer almalıdır yapısı içinde bir <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> veya <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Metin denetimleri içerik görünümünde değil görüntülenebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç (bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Metin denetimleri genellikle başka bir denetim adı özelliği üzerinden görüntülenen olmasıdır. Örneğin, bir düzenleme denetimi etiketlemek için kullanılan metin düzenleme denetimi Name özelliği sunulur. İçerik görünümünde düzenleme denetimi olduğundan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacında, bunu gerekli olmadığı metin öğesi kendisi bu görünümde olması için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. İçerik görünümünde görüntülenir yalnızca metin olarak yedekli bilgileri olmayan metindir. Bu, yalnızca, kullanıcılar gereken bilgi parçalarını üzerinde hızlı bir şekilde filtrelemek bir yardımcı teknoloji sağlar.  
  
#### <a name="edit"></a>Düzenle  
 Denetimleri etkinleştirme görüntülemek ve tek satırlık metin düzenlemek için kullanıcıyı düzenleyin.  
  
> [!NOTE]
>  Tek satırlık metin belirli düzeni senaryolarda sarmalamak.  
  
#### <a name="document"></a>Belge  
 Belge denetimler gidin ve birden çok metin sayfalarından bilgi edinme kullanıcı olanak sağlar.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern İstemcisi API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|Giriş noktası için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin modeli.<br /><br /> Bu sınıf ayrıca iki içerir <xref:System.Windows.Automation.TextPattern> olay dinleyicileri <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> ve <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|Destekleyen bir metin kapsayıcı içindeki metin gösterimini <xref:System.Windows.Automation.TextPattern>.<br /><br /> UI Otomasyon istemcileri kullanılarak oluşturulan bir metin aralığını geçerli geçerliliği hakkında dikkatli <xref:System.Windows.Automation.Text.TextPatternRange>. Metin denetimini özgün metinde tamamen yeni metin değiştirirse, geçerli metin aralığını geçersiz hale gelir. Bununla birlikte, metin aralığını hala bazı letim gereksinimlerinin yalnızca özgün metnin bir bölümünü değiştirilir ve alttaki metin denetimi, metin yönetme "işaretçi" bağlayıcılarını (veya uç noktaların) yerine mutlak karakter konumlandırma ile olabilir.<br /><br /> İstemciler dinlemek için bir <xref:System.Windows.Automation.TextPattern.TextChangedEvent> bunlar çalıştığınız metin içeriği için herhangi bir değişiklik bildirimi.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Bir metin aralığını biçimlendirme öznitelikleri tanımlamak için kullanılır.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern sağlayıcısı API'nin  
 Kullanıcı Arabirimi öğeleri veya denetimleri destekleyen <xref:System.Windows.Automation.TextPattern> uygulayarak <xref:System.Windows.Automation.Provider.ITextProvider> ve <xref:System.Windows.Automation.Provider.ITextRangeProvider> , ya da yerel olarak arabirimleri aracılığıyla veya [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy'leri içerdikleri içinde herhangi bir metin için ayrıntılı öznitelik bilgileri gösterme özellikli sağlam gezinme özelliklerinin sağlanması yanı sıra.  
  
 A <xref:System.Windows.Automation.TextPattern> denetimi herhangi belirli öznitelikler için destek eksikse tüm metin özniteliklerini desteklemek sağlayıcı yok.  
  
 A <xref:System.Windows.Automation.TextPattern> sağlayıcı desteklemelidir <xref:System.Windows.Automation.TextPattern.GetSelection%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> denetimi içinde metin alanı metin seçim ya da metin imlecin (veya sistem şapka) yerleşimini destekliyorsa çalışır. Denetim bu işlevselliği desteklemiyorsa, bu yöntemlerden birini destekleyen gerekmez. Ancak, Denetim desteklediği uygulayarak metin seçim türü kullanıma gerekir <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> özelliği.  
  
 A <xref:System.Windows.Automation.TextPattern> sağlayıcı her zaman desteklemelidir <xref:System.Windows.Automation.Text.TextUnit> sabitleri <xref:System.Windows.Automation.Text.TextUnit.Character> ve <xref:System.Windows.Automation.Text.TextUnit.Document> yanı sıra diğer <xref:System.Windows.Automation.Text.TextUnit> sabitleri olduğu destekleme kapasitesine sahip.  
  
> [!NOTE]
>  Sağlayıcı için belirli bir destek atlayabilirsiniz <xref:System.Windows.Automation.Text.TextUnit> sonraki ertelemeyi tarafından en büyük <xref:System.Windows.Automation.Text.TextUnit> aşağıdaki sırayla desteklenen: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, ve <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Yöntemler, özellikler ve Destek öznitelikleri gösterir <xref:System.Windows.Automation.TextPattern> istemci uygulamalarında (bkz: <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|SMS Sağlayıcısı'nda metin aralığını temsil eder (bkz: <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Metin sağlayıcıları için tanımlayıcı olarak kullanılan değerleri içerir (bkz: <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Mimarisi göz önünde bulundurularak ile tasarlanmıştır (bkz [UI Otomasyon güvenliğine genel bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). Ancak, bu genel bakış içinde açıklanan TextPattern sınıfları bazı belirli güvenlik konuları gerektirir.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin sağlayıcıları salt okunur arabirimleri sağlayın ve varolan metin denetiminde değiştirme yeteneği sağlamaz.  
  
-   UI Otomasyon istemcileri yalnızca kullanabilir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tam olarak "" güvenilirse. Bunun bir örneği burada yalnızca bilinen ve güvenilen uygulamaları çalıştırabilir korumalı oturum açma Masaüstü olacaktır.  
  
-   UI Otomasyon sağlayıcılar geliştiricileri tüm bilgileri kendi denetimlerinde kullanıma sunmak tercih ettikleri olduğunu kullanan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] temelde ortak ve başka bir kod tarafından tam olarak erişilebilir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UI Otomasyonu istemci ve bu nedenle UI Otomasyon Sağlayıcı'nın güvenilirliği korumalı içerik veya hassas metinsel bilgileri (örneğin, parola alanları) açığa çıkarmamalıdır belirlemek için hiçbir çaba yapar.  
  
-   Güvenlik için en önemli değişikliklerden biri [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] kapsamlı olarak "Güvenli en az ayrıcalıklı (veya sınırlı) gibi teknolojileri kapsar girişini" olarak adlandırılır kullanıcı hesapları (LUA) ve kullanıcı Arabirimi ayrıcalık düzeyi yalıtım (UIPI).  
  
    -   UIPI denetlenmesi ve/veya başka bir "ayrıcalıklı" daha fazla program izleme alanından bir program kullanıcı girişi aldatma çapraz işlem pencere ileti saldırılarını önleme engeller.  
  
    -   LUA Administrators grubundaki kullanıcılar tarafından çalıştırılan uygulamaların ayrıcalıkların sınırlar koyar. Uygulamaları mutlaka yönetici ayrıcalıklarına sahip olmaz ancak bunun yerine gerekli en düşük ayrıcalık ile çalışır. Sonuç olarak, bazı kısıtlamalar LUA senaryolarda zorunlu olabilir. Burada bu uygulamayı devre dışı bırakma noktasına bellek ayırmak için zorunlu olmayan için yönetici düzeyi uygulamalardan alınan dizeleri boyutunu sınırlamak gerekli olabilir kesilmesi (dahil olmak üzere TextPattern dizeleri), özellikle dize.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Performans  
 TextPattern çapraz işlem çağrıları işlevselliğini çoğu için kullandığından, içeriği işlerken performansını artırmak için önbelleğe alma mekanizması sağlamaz. Bu diğer denetim düzenleri benzemez [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , erişilebilir kullanarak <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> yöntemleri.  
  
 Performansı artırmak için bir yöntem olduğu UI Otomasyonu istemcileri çalışır metnini kullanarak, orta ölçekli bloklarını almak sağlayarak <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Örneğin, bir GetText(-1) çağrısı bir işlem içi isabet neden, ancak metin sağlayıcısı boyutuna bağlı olarak yüksek gecikme olabilir ancak GetText(1) çağrıları çapraz işlem isabet her karakter için uygulanabilir.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>TextPattern terminolojisi  
 **Özniteliği**  
 Bir metin aralığını biçimlendirme özelliğidir (örneğin, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> veya <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Bozuk aralığı**  
 Bozuk bir boş veya sıfır karakterlik metin aralığını aralıktır. TextPattern denetim düzeni amaçları doğrultusunda, metin ekleme noktasını (veya sistem şapka) bozuk bir aralık olarak kabul edilir. Metin seçtiyseniz <xref:System.Windows.Automation.TextPattern.GetSelection%2A> metin ekleme noktasını bozuk bir aralığa döndürür ve <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> bozuk bir aralık, başlangıç uç noktasında olarak döndürür. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ve <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> metin sağlayıcısı verilen koşulu sağlayan tüm metin aralıkları bulamadığında bozuk aralıkları döndürebilir. Bozuk bu aralık, başlangıç bir uç nokta metin sağlayıcısı içinde olarak kullanılabilir. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> null bir başvuru döndürür (`Nothing` Microsoft Visual Basic .NET içinde) bozuk bir aralık karşı bulunan aralığıyla Karışıklığı önlemek için.  
  
 **Katıştırılmış nesne**  
 Katıştırılmış nesneler iki tür vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin modeli. Metin tabanlı içerik öğeleri Köprüler veya tablolar gibi ve görüntüleri ve düğmeleri gibi denetim öğeleri oluşur. Daha ayrıntılı bilgi için bkz: [erişim katıştırılmış nesneler kullanarak UI Otomasyonu](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Uç nokta**  
 Mutlak <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> veya <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bir metin kapsayıcı içindeki bir metin aralığını noktası.  
  
 ![TextPatternRangeEndpoints &#40;başlangıç ve bitiş&#41;. ] (../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
Başlangıç ve bitiş noktalarını kümesi gösterilmektedir.  
  
 **TextRange**  
 Başlangıç ve bitiş noktaları, ilişkili tüm öznitelikleri ve işlevselliği de dahil olmak üzere bir metin kapsayıcıda metin gösterimi.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Bir metin aralığını mantıksal parçalarını gezinmek için kullanılan metin (karakter, word, satır veya paragraf), önceden tanımlanmış bir birimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Metin hizmetleri altyapısı](http://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
