---
title: UI Otomasyon TextPattern Öğesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: defabb90c8aed19fda663d9b360545fc399acaec
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040530"
---
# <a name="ui-automation-textpattern-overview"></a>UI Otomasyon TextPattern Öğesine Genel Bakış

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu genel bakışta, desteklenen platformlardaki metin [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]denetimlerinin biçim ve stil öznitelikleri de dahil olmak üzere metin içeriğini göstermek için nasıl kullanılacağı açıklanmaktadır. Bu denetimler, Microsoft .NET çerçevesini <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> bunların [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] eşdeğerleriyle sınırlı olmamak üzere, ancak bunlarla sınırlı değildir.

Bir denetimin metinsel içeriğini göstermek, metin kapsayıcısının içeriğini bir metin akışı olarak temsil <xref:System.Windows.Automation.TextPattern> eden denetim deseninin kullanımı aracılığıyla gerçekleştirilir. Sırasıyla, <xref:System.Windows.Automation.TextPattern> biçim ve stil özniteliklerini göstermek için <xref:System.Windows.Automation.Text.TextPatternRange> sınıfının desteğini gerektirir. <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ve uç<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> noktaları içeren bir metin kapsayıcısında bitişik veya birden çok, ayrık metin yayılımları temsil ederek destekler. <xref:System.Windows.Automation.Text.TextPatternRange>seçim, karşılaştırma, alma ve çapraz geçiş gibi işlevleri destekler.

> [!NOTE]
> Sınıflar <xref:System.Windows.Automation.TextPattern> , metin eklemek veya değiştirmek için bir yol sağlamaz. Ancak, denetime bağlı olarak, bu işlem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> veya doğrudan klavye girişi aracılığıyla gerçekleştirilebilir. Örnek için [TextModel metin ekleme örneğine](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) bakın.

Bu genel bakışta açıklanan işlevselliğe yardımcı teknoloji satıcıları ve bunların son kullanıcıları için çok önemlidir. Yardımcı teknolojiler, Kullanıcı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için tüm metin biçimlendirme bilgilerini toplamak ve <xref:System.Windows.Automation.Text.TextUnit> kısa bir şekilde (karakter, sözcük, çizgi veya paragraf) metin seçimi sağlamak için kullanabilir.

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>UI Otomasyonu TextModel vs. Metin Hizmetleri çerçevesi

[!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)], masaüstünde ve uygulamalar içinde doğal dil Hizmetleri ve gelişmiş metin girişi sağlayan basit ve ölçeklenebilir bir sistem çerçevesidir. Uygulamanın metin mağazalarını kullanıma sunmasına yönelik arabirimlerin sağlanması ek olarak, bu metin deposunun meta verilerini de destekler.

Ancak, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] <xref:System.Windows.Automation.TextPattern> bir salt okuma çözümüdür (yukarıda belirtilen sınırlı geçici çözümle birlikte) için bir metin deposuna iyileştirilmiş erişim sağlanması amaçlanan bir salt okunurdur. ekran okuyucular ve Braille cihazları.

Kısa bir süre içinde bir metin deposuna salt okuma erişimi gerektiren erişilebilir teknolojiler kullanabilir <xref:System.Windows.Automation.TextPattern>, ancak bağlama duyarlı giriş [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] için daha karmaşık işlevlere ihtiyaç duyar.

<a name="Control_Types"></a>

## <a name="control-types"></a>Denetim türleri

### <a name="text"></a>Metin

Metin denetimi, ekranda metin parçasını temsil eden temel öğedir.

Tek başına metin denetimi, form üzerinde etiket veya statik metin olarak kullanılabilir. Metin denetimleri <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> veya <xref:System.Windows.Automation.ControlType.DataItem>yapısına de dahil edilebilir.

> [!NOTE]
> Metin denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümünde görünmeyebilir (bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md)). Bunun nedeni, metin denetimlerinin genellikle başka bir denetimin Name özelliği aracılığıyla görüntülenmalardır. Örneğin, bir düzenleme denetimini etiketlemek için kullanılan metin, düzenleme denetiminin Name özelliği aracılığıyla sunulur. Düzenleme denetimi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümünde olduğundan, metin öğesinin kendisi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç görünümünde olması gerekli değildir. İçerik görünümünde görüntülenen tek metin, gereksiz bilgiler olmayan metindir. Bu, tüm yardımcı teknolojilerin, kullanıcıların ihtiyaç duyduğu bilgi parçalarını hızla filtrelemesine olanak sağlar.

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
|`System.Windows.Automation.TextPattern Class`|[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Metin modeli için giriş noktası.<br /><br /> Bu sınıf Ayrıca iki <xref:System.Windows.Automation.TextPattern> olay <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> dinleyicilerini <xref:System.Windows.Automation.TextPattern.TextChangedEvent>içerir.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Tarafından desteklenen <xref:System.Windows.Automation.TextPattern>metin kapsayıcısı içindeki bir metin yayılımının temsili.<br /><br /> UI Otomasyonu istemcileri kullanılarak <xref:System.Windows.Automation.Text.TextPatternRange>oluşturulan bir metin aralığının geçerli geçerliliği konusunda dikkatli olmalıdır. Metin denetimindeki özgün metnin tamamen yeni metinle değiştirildiği durumda, geçerli metin aralığı geçersiz hale gelir. Ancak, özgün metnin yalnızca bir kısmı değiştirilirse ve temel alınan metin denetimi, metin "Pointer" öğesini mutlak karakter konumlandırma yerine tutturucularla (veya uç noktalar) yönetse de metin aralığı yine de bazı vilebilirlik içerebilir.<br /><br /> İstemciler, üzerinde çalıştıkları metinsel <xref:System.Windows.Automation.TextPattern.TextChangedEvent> içerikte yapılan herhangi bir değişiklik bildirimi için dinleme yapabilir.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Bir metin aralığının biçimlendirme özniteliklerini belirlemek için kullanılır.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>TextModel sağlayıcısı API 'Leri

Yerel olarak veya proxy 'ler aracılığıyla <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.Provider.ITextProvider> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , ve <xref:System.Windows.Automation.Provider.ITextRangeProvider> arabirimlerini uygulayarak destekleyen kullanıcı arabirimi öğeleri veya denetimleri, içerdikleri herhangi bir metin için ayrıntılı öznitelik bilgilerini ortaya çıkarabilme yeteneğine sahiptir güçlü gezinme özellikleri sağlamaya ek olarak.

Denetimin belirli öznitelikler için destek yoksa, sağlayıcınıntümmetinözniteliklerinidesteklemesigerekmez.<xref:System.Windows.Automation.TextPattern>

Denetim metin alanı içinde metin <xref:System.Windows.Automation.TextPattern.GetSelection%2A> seçimi <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> veya metin imlecinizin (veya sistem giriş işareti) yerleşimini destekliyorsa, sağlayıcıveişlevlerinidesteklemelidir.<xref:System.Windows.Automation.TextPattern> Denetim bu işlevselliği desteklemiyorsa, bu yöntemlerden birini desteklemesi gerekmez. Ancak denetim, <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> özelliği uygulayarak desteklediği metin seçiminin türünü kullanıma sunmalıdır.

Bir <xref:System.Windows.Automation.TextPattern> sağlayıcının, <xref:System.Windows.Automation.Text.TextUnit> her zaman sabitleri <xref:System.Windows.Automation.Text.TextUnit.Character> ve <xref:System.Windows.Automation.Text.TextUnit.Document> desteklenebilecek diğer <xref:System.Windows.Automation.Text.TextUnit> sabitleri desteklemesi gerekir.

> [!NOTE]
> Sağlayıcı, aşağıdaki <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit.Word> <xref:System.Windows.Automation.Text.TextUnit.Document> <xref:System.Windows.Automation.Text.TextUnit.Format> <xref:System.Windows.Automation.Text.TextUnit.Paragraph> <xref:System.Windows.Automation.Text.TextUnit.Page> <xref:System.Windows.Automation.Text.TextUnit.Character> sırayladesteklenen<xref:System.Windows.Automation.Text.TextUnit> bir sonraki en büyük ' ı erteleyerek belirli bir desteği atlayabilir:,,, ,,ve<xref:System.Windows.Automation.Text.TextUnit.Line> .

|||
|-|-|
|`ITextProvider Interface`|İstemci uygulamalarında destekleyen <xref:System.Windows.Automation.TextPattern> yöntemleri, özellikleri ve öznitelikleri gösterir (bkz <xref:System.Windows.Automation.Provider.ITextProvider>.).|
|`ITextRangeProvider Interface`|Metin sağlayıcısındaki metnin bir aralığını temsil eder (bkz <xref:System.Windows.Automation.Provider.ITextRangeProvider>.).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Metin sağlayıcıları için tanımlayıcı olarak kullanılan değerleri içerir (bkz <xref:System.Windows.Automation.TextPatternIdentifiers>.).|

<a name="Security"></a>

## <a name="security"></a>Güvenlik

Mimari güvenlik göz önünde bulundurularak tasarlanmıştır (bkz. [UI Otomasyonu güvenliğine genel bakış](ui-automation-security-overview.md)). [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ancak, bu genel bakışta açıklanan TextModel sınıfları bazı belirli güvenlik konuları gerektirir.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]metin sağlayıcıları salt okuma arabirimleri sağlar ve denetimdeki varolan metni değiştirme olanağı sağlamaz.

- UI Otomasyonu istemcileri yalnızca [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tam olarak "güvenilir" olmaları durumunda kullanılabilir. Bu, yalnızca bilinen ve güvenilen uygulamaların çalıştırılabileceği korumalı oturum açma masaüstü olabilir.

- UI Otomasyon sağlayıcılarının geliştiricileri, genel [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olarak genel ve diğer kod tarafından tam olarak erişilebilen, denetimleri içinde kullanıma sunmak için kullandıkları tüm bilgilerin farkında olmalıdır. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]herhangi bir UI Otomasyon istemcisinin güvenilirliğini belirleme çabası yoktur ve bu nedenle UI Otomasyon sağlayıcısı korunan içeriği veya gizli metin bilgilerini (parola alanları gibi) kullanıma sunmamalıdır.

- Güvenlik açısından [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] en önemli değişikliklerden birisi, en az ayrıcalıklı (veya sınırlı) Kullanıcı hesapları (LUA) ve Kullanıcı arabirimi ayrıcalık düzeyi yalıtımı (UIPI) gibi teknolojileri kapsayan "güvenli giriş" olarak adlandırılır.

  - UıPı, bir programın başka bir "ayrıcalıklı" programı denetlemesini ve/veya izlemesini engelliyorsa, kullanıcı girişine sızacak çapraz işlem penceresi ileti saldırılarını engeller.

  - LUA, Yöneticiler grubundaki kullanıcılar tarafından çalıştırılmakta olan uygulamaların ayrıcalıklarıyla sınırlar belirler. Uygulamaların yönetici ayrıcalıkları olması gerekmez, ancak bunun yerine gereken en az ayrıcalıklarla çalışır. Sonuç olarak, LUA senaryolarında uygulanan bazı kısıtlamalar olabilir. Çoğu bilinen dize kesilmesi (TextModel dizeleri dahil), burada, uygulamayı devre dışı bırakma noktasına bellek ayırmaya zorlanmaması için, yönetici düzeyindeki uygulamalardan alınan dizelerin boyutunu sınırlamak gerekli olabilir.

<a name="Performance"></a>

## <a name="performance"></a>Performans

TextModel çoğu işlevselliği için çapraz işlem çağrılarını kullandığından, içeriği işlerken performansı artırmak için bir önbelleğe alma mekanizması sağlamaz. Bu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya yöntemlerikullanılarakerişilebilen'dekidiğerdenetimdesenlerindenfarklıolur.<xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>

Performansı iyileştirmeye yönelik bir taktik, UI Otomasyonu istemcilerinin kullanarak <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>orta ölçekli metin bloklarını almayı denemelerini sağlar. Örneğin, GetText (1) çağrıları her karakter için çapraz işlem isabetlerine neden olur, ancak bir GetText (-1) çağrısı tek bir çapraz süreç isabetine neden olur, ancak metin sağlayıcısının boyutuna bağlı olarak yüksek gecikme süresine sahip olabilir.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>TextModel terminolojisi

**Özniteliğe**\
Bir metin aralığının biçimlendirme özelliği (örneğin, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> veya <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Aralık oluşturmayı kaldırma**\
Bozuk aralığı boş veya sıfır karakterli bir metin aralığıdır. TextModel denetim deseninin amaçları doğrultusunda, metin ekleme noktası (veya sistem giriş işareti), bir bozuk aralığı olarak kabul edilir. Metin seçilmezse, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> metin ekleme noktasında bir bozuk aralığı döndürür ve <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> başlangıç uç noktası olarak bir bozuk aralığı döndürür. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>ve <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> , metin sağlayıcısı verilen koşulla eşleşen herhangi bir metin aralığı bulamadığında, aralıkları deme aralığı döndürebilir. Bu bozuk aralığı, metin sağlayıcısı içinde başlangıç uç noktası olarak kullanılabilir. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>ve <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> bir boş başvuru (`Nothing` Microsoft Visual Basic .net 'te), bulunan bir Aralık ile karışıklık oluşmasını önlemek için

**Katıştırılmış nesne**\
[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Metin modelinde iki tür katıştırılmış nesne vardır. Köprüler veya tablolar gibi metin tabanlı içerik öğelerinden oluşur ve görüntüler ve düğmeler gibi öğeleri kontrol edin. Daha ayrıntılı bilgi için bkz. [UI Otomasyonu kullanarak katıştırılmış nesnelere erişme](access-embedded-objects-using-ui-automation.md).

**Bkz**\
Metin kapsayıcısı <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> içindeki <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bir metin aralığının mutlak veya noktası.

![TextPatternRangeEndpoints &#40;başlangıç ve bitiş&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints") Aşağıda, bir dizi başlangıç ve bitiş noktası gösterilmektedir.

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
