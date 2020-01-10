---
title: UI Otomasyon TextPattern Öğesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 22966c8ed80be99497e7d05b56455c3057fdd81a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741423"
---
# <a name="ui-automation-textpattern-overview"></a>UI Otomasyon TextPattern Öğesine Genel Bakış

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu genel bakışta, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından desteklenen platformlarda metin denetimlerinin biçim ve stil öznitelikleri dahil olmak üzere metin içeriğini göstermek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nasıl kullanılacağı açıklanmaktadır. Bu denetimler, Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> ile bunlarla sınırlı değildir.

Bir denetimin metinsel içeriğini göstermek, metin kapsayıcısının içeriğini bir metin akışı olarak temsil eden <xref:System.Windows.Automation.TextPattern> denetim deseninin kullanımı aracılığıyla gerçekleştirilir. <xref:System.Windows.Automation.TextPattern>, biçim ve stil özniteliklerini göstermek için <xref:System.Windows.Automation.Text.TextPatternRange> sınıfının desteğini gerektirir. <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ve <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktaları koleksiyonuyla bir metin kapsayıcısında bitişik veya birden çok, ayrık metin yayılmalarını temsil eden <xref:System.Windows.Automation.TextPattern> destekler. <xref:System.Windows.Automation.Text.TextPatternRange> seçim, karşılaştırma, alma ve çapraz geçiş gibi işlevleri destekler.

> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> sınıfları metin eklemek veya değiştirmek için bir yol sağlamaz. Ancak, denetime bağlı olarak, bu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> veya doğrudan klavye girişi aracılığıyla gerçekleştirilebilir. Örnek için [TextModel metin ekleme örneğine](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) bakın.

Bu genel bakışta açıklanan işlevselliğe yardımcı teknoloji satıcıları ve bunların son kullanıcıları için çok önemlidir. Yardımcı teknolojiler, Kullanıcı için tüm metin biçimlendirme bilgilerini toplamak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kullanabilir ve <xref:System.Windows.Automation.Text.TextUnit> (karakter, sözcük, çizgi veya paragraf) ile programlı gezinme ve metin seçimi sağlayabilir.

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>UI Otomasyonu TextModel ve metin Hizmetleri çerçevesi karşılaştırması

Metin Hizmetleri çerçevesi (TSF), masaüstünde ve uygulamalar içinde doğal dil Hizmetleri ve gelişmiş metin girişi sağlayan basit ve ölçeklenebilir bir sistem çerçevesidir. Uygulamanın metin mağazalarını kullanıma sunmasına yönelik arabirimlerin sağlanması ek olarak, bu metin deposunun meta verilerini de destekler.

Ancak TS<xref:System.Windows.Automation.TextPattern> f, bir salt okuma çözümüdür (yukarıda belirtilen sınırlı geçici çözümle birlikte), ekran okuyucular ve Braille cihazları için bir metin deposuna iyileştirilmiş erişim sağlamak amacıyla,

Kısa bir süre içinde, bir metin deposuna salt okuma erişimi gerektiren erişilebilir teknolojiler <xref:System.Windows.Automation.TextPattern>kullanabilir, ancak bağlama duyarlı giriş için TSF 'nin daha karmaşık işlevselliğine ihtiyaç duyar.

<a name="Control_Types"></a>

## <a name="control-types"></a>Denetim türleri

### <a name="text"></a>Metin

Metin denetimi, ekranda metin parçasını temsil eden temel öğedir.

Tek başına metin denetimi, form üzerinde etiket veya statik metin olarak kullanılabilir. Metin denetimleri, bir <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> veya <xref:System.Windows.Automation.ControlType.DataItem>yapısı içinde de bulunabilir.

> [!NOTE]
> Metin denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümünde görünmeyebilir (bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md)). Bunun nedeni, metin denetimlerinin genellikle başka bir denetimin Name özelliği aracılığıyla görüntülenmalardır. Örneğin, bir düzenleme denetimini etiketlemek için kullanılan metin, düzenleme denetiminin Name özelliği aracılığıyla sunulur. Düzenleme denetimi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümünde olduğundan, metin öğesinin kendisi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının bu görünümünde olması gerekmez. İçerik görünümünde görüntülenen tek metin, gereksiz bilgiler olmayan metindir. Bu, tüm yardımcı teknolojilerin, kullanıcıların ihtiyaç duyduğu bilgi parçalarını hızla filtrelemesine olanak sağlar.

### <a name="edit"></a>Düzenle

Denetimleri Düzenle, bir kullanıcının tek satırlık bir metin görüntülemesini ve düzenlemenizi sağlar.

> [!NOTE]
> Tek satırlık metin belirli düzen senaryolarında kaydırılabilir.

### <a name="document"></a>Belge

Belge denetimleri, kullanıcının birden çok sayfadan metin almasına ve bilgi almasına izin verir.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>TextModel Istemci API 'Leri

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin modeli için giriş noktası.<br /><br /> Bu sınıf Ayrıca iki <xref:System.Windows.Automation.TextPattern> olay dinleyicilerini içerir <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> ve <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|<xref:System.Windows.Automation.TextPattern>destekleyen bir metin kapsayıcısı içindeki bir metin yayılımının temsili.<br /><br /> UI Otomasyonu istemcileri, <xref:System.Windows.Automation.Text.TextPatternRange>kullanılarak oluşturulan bir metin aralığının geçerli geçerliliği konusunda dikkatli olmalıdır. Metin denetimindeki özgün metnin tamamen yeni metinle değiştirildiği durumda, geçerli metin aralığı geçersiz hale gelir. Ancak, özgün metnin yalnızca bir kısmı değiştirilirse ve temel alınan metin denetimi, metin "Pointer" öğesini mutlak karakter konumlandırma yerine tutturucularla (veya uç noktalar) yönetse de metin aralığı yine de bazı vilebilirlik içerebilir.<br /><br /> İstemciler, üzerinde çalıştıkları metin içeriğine yapılan herhangi bir değişiklik bildirimi için <xref:System.Windows.Automation.TextPattern.TextChangedEvent> dinleyebilir.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Bir metin aralığının biçimlendirme özniteliklerini belirlemek için kullanılır.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>TextModel sağlayıcısı API 'Leri

Yerel olarak veya [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy 'ler aracılığıyla <xref:System.Windows.Automation.Provider.ITextProvider> ve <xref:System.Windows.Automation.Provider.ITextRangeProvider> arabirimlerini uygulayarak <xref:System.Windows.Automation.TextPattern> destekleyen kullanıcı arabirimi öğeleri veya denetimleri, güçlü gezinme özellikleri sağlamaya ek olarak içerdikleri herhangi bir metin için ayrıntılı öznitelik bilgilerini ortaya çıkarabilme özelliğine sahiptir.

Denetim belirli öznitelikler için destek içermiyorsa, bir <xref:System.Windows.Automation.TextPattern> sağlayıcı tüm metin özniteliklerini desteklemek zorunda değildir.

Bir <xref:System.Windows.Automation.TextPattern> sağlayıcı metin seçimini veya metin imlecinin metin imleci (veya sistem giriş işaretini) yerleştirmeyi destekliyorsa, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> işlevlerini desteklemesi gerekir. Denetim bu işlevselliği desteklemiyorsa, bu yöntemlerden birini desteklemesi gerekmez. Ancak, denetim <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> özelliğini uygulayarak desteklediği metin seçiminin türünü kullanıma sunmalıdır.

<xref:System.Windows.Automation.TextPattern> sağlayıcısı her zaman <xref:System.Windows.Automation.Text.TextUnit> sabitlerini <xref:System.Windows.Automation.Text.TextUnit.Character> ve <xref:System.Windows.Automation.Text.TextUnit.Document> aynı zamanda desteklenebilecek <xref:System.Windows.Automation.Text.TextUnit> diğer tüm sabitleri desteklemelidir.

> [!NOTE]
> Sağlayıcı, aşağıdaki sırada desteklenen bir sonraki en büyük <xref:System.Windows.Automation.Text.TextUnit> erteleyerek belirli bir <xref:System.Windows.Automation.Text.TextUnit> desteğini atlayabilir: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>ve <xref:System.Windows.Automation.Text.TextUnit.Document>.

|||
|-|-|
|`ITextProvider Interface`|İstemci uygulamalarında <xref:System.Windows.Automation.TextPattern> destekleyen yöntemleri, özellikleri ve öznitelikleri gösterir (bkz. <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Metin sağlayıcısındaki metnin bir aralığını temsil eder (bkz. <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Metin sağlayıcıları için tanımlayıcı olarak kullanılan değerleri içerir (bkz. <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>

## <a name="security"></a>Güvenlik

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mimarisi güvenliği göz önünde bulundurularak tasarlanmıştır (bkz. [UI Otomasyonu güvenliğine genel bakış](ui-automation-security-overview.md)). Ancak, bu genel bakışta açıklanan TextModel sınıfları bazı belirli güvenlik konuları gerektirir.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin sağlayıcıları salt okuma arabirimleri sağlar ve denetimdeki varolan metni değiştirme olanağı sağlamaz.

- UI Otomasyonu istemcileri, yalnızca tam olarak "güvenilir" olmaları durumunda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanabilir. Bu, yalnızca bilinen ve güvenilen uygulamaların çalıştırılabileceği korumalı oturum açma masaüstü olabilir.

- UI Otomasyon sağlayıcılarının geliştiricileri, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla denetimlerinde açığa çıkarmak için kullandıkları tüm bilgilerin temelde genel ve diğer kod tarafından tam olarak erişebileceği farkında olmalıdır. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] herhangi bir UI Otomasyon istemcisinin güvenilirliğini belirleme çabası yoktur ve bu nedenle UI Otomasyon sağlayıcısı korunan içeriği veya gizli metin bilgilerini (parola alanları gibi) kullanıma sunmamalıdır.

- Windows Vista güvenliğine en önemli değişikliklerden birisi, en az ayrıcalıklı (veya sınırlı) Kullanıcı hesapları (LUA) ve kullanıcı ARABIRIMI ayrıcalık düzeyi yalıtımı (UıPı) gibi teknolojileri kapsayan "güvenli giriş" olarak adlandırılır.

  - UıPı, bir programın başka bir "ayrıcalıklı" programı denetlemesini ve/veya izlemesini engelliyorsa, kullanıcı girişine sızacak çapraz işlem penceresi ileti saldırılarını engeller.

  - LUA, Yöneticiler grubundaki kullanıcılar tarafından çalıştırılmakta olan uygulamaların ayrıcalıklarıyla sınırlar belirler. Uygulamaların yönetici ayrıcalıkları olması gerekmez, ancak bunun yerine gereken en az ayrıcalıklarla çalışır. Sonuç olarak, LUA senaryolarında uygulanan bazı kısıtlamalar olabilir. Çoğu bilinen dize kesilmesi (TextModel dizeleri dahil), burada, uygulamayı devre dışı bırakma noktasına bellek ayırmaya zorlanmaması için, yönetici düzeyindeki uygulamalardan alınan dizelerin boyutunu sınırlamak gerekli olabilir.

<a name="Performance"></a>

## <a name="performance"></a>Performans

TextModel çoğu işlevselliği için çapraz işlem çağrılarını kullandığından, içeriği işlerken performansı artırmak için bir önbelleğe alma mekanizması sağlamaz. Bu, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> yöntemleri kullanılarak erişilebilen [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] içindeki diğer denetim desenlerinden farklı olur.

Performansı iyileştirmeye yönelik bir taktik, UI Otomasyonu istemcilerinin <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>kullanarak orta ölçekli metin bloklarını almayı denemelerini sağlar. Örneğin, GetText (1) çağrıları her karakter için çapraz işlem isabetlerine neden olur, ancak bir GetText (-1) çağrısı tek bir çapraz süreç isabetine neden olur, ancak metin sağlayıcısının boyutuna bağlı olarak yüksek gecikme süresine sahip olabilir.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>TextModel terminolojisi

**Öznitelik**\
Bir metin aralığının biçimlendirme özelliği (örneğin, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> veya <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Aralık oluşturmayı kaldırma**\
Bozuk aralığı boş veya sıfır karakterli bir metin aralığıdır. TextModel denetim deseninin amaçları doğrultusunda, metin ekleme noktası (veya sistem giriş işareti), bir bozuk aralığı olarak kabul edilir. Hiçbir metin seçilmezse <xref:System.Windows.Automation.TextPattern.GetSelection%2A> metin ekleme noktasında bir bozuk aralığı döndürür ve <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> başlangıç uç noktası olarak bir bozuk aralığı döndürebilir. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ve <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A>, metin sağlayıcısı verilen koşulla eşleşen herhangi bir metin aralığı bulamıyorsa, aralıkları deme döndürebilir. Bu bozuk aralığı, metin sağlayıcısı içinde başlangıç uç noktası olarak kullanılabilir. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> ve <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> bir boş başvuru (Microsoft Visual Basic .NET 'te`Nothing`), bulunan bir Aralık ile karışıklık oluşmasını önlemek için de

**Katıştırılmış nesne**\
[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin modelinde iki tür katıştırılmış nesne vardır. Köprüler veya tablolar gibi metin tabanlı içerik öğelerinden oluşur ve görüntüler ve düğmeler gibi öğeleri kontrol edin. Daha ayrıntılı bilgi için bkz. [UI Otomasyonu kullanarak katıştırılmış nesnelere erişme](access-embedded-objects-using-ui-automation.md).

**Uç nokta**\
Metin kapsayıcısı içindeki bir metin aralığının mutlak <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> veya <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> noktası.

![TextPatternRangeEndpoints &#40;başlangıç ve bitiş&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")
Aşağıda, bir dizi başlangıç ve bitiş noktası gösterilmektedir.

**TextRange**\
Tüm ilişkili öznitelikleri ve işlevleri de içeren bir metin kapsayıcısında, başlangıç ve bitiş noktaları içeren bir metin yayılımının temsili.

<xref:System.Windows.Automation.Text.TextUnit>\
Bir metin aralığının mantıksal kesimlerinde gezinmek için kullanılan önceden tanımlanmış bir metin birimi (karakter, sözcük, çizgi veya paragraf).

## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](control-pattern-mapping-for-ui-automation-clients.md)
- [Metin Hizmetleri çerçevesi](/windows/desktop/api/_tsf/)
