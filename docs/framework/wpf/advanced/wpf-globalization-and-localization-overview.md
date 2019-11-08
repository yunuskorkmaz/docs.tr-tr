---
title: WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: b8777e1402bef1708136a5f81a641beb8c761905
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740701"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış

Ürününüzün kullanılabilirliğini yalnızca bir dille sınırlandırdığınızda, olası müşteri tabanınızı dünyanın 6.500.000.000 popülasyonızın bir bölümü ile sınırlandırdığınızda. Uygulamalarınızın küresel bir hedef kitleye ulaşmasını istiyorsanız, ürününüzün düşük maliyetli yerelleştirilmesi, daha fazla müşteriye ulaşmak için en iyi ve en ekonomik yolların biridir.

Bu genel bakışta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Genelleştirme ve yerelleştirme tanıtılmıştır. Genelleştirme, birden çok konumda gerçekleştiren uygulamaların tasarımını ve geliştirilmesini geliştirmektedir. Örneğin, Genelleştirme farklı kültürler içindeki kullanıcılar için yerelleştirilmiş kullanıcı arabirimlerini ve bölgesel verileri destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], otomatik düzen, uydu derlemeleri ve yerelleştirilmiş öznitelikler ve açıklama ekleme dahil olmak üzere Genelleştirilmiş tasarım özellikleri sağlar.

Yerelleştirme, uygulama kaynaklarının, uygulamanın desteklediği belirli kültürler için yerelleştirilmiş sürümlere çevirmesidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' de yerelleştirmeniz durumunda, <xref:System.Windows.Markup.Localizer> ad alanındaki API 'Leri kullanırsınız. Bu API 'Ler [LocBaml aracı örnek](https://go.microsoft.com/fwlink/?LinkID=160016) komut satırı aracını güçlendirin. LocBaml oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF 'de Genelleştirme ve yerelleştirme için en iyi uygulamalar

Bu bölümün sağladığı Kullanıcı arabirimi tasarımını ve Yerelleştirmede ilgili ipuçlarını izleyerek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleşik olarak bulunan Genelleştirme ve yerelleştirme işlevlerinin çoğunu yapabilirsiniz.

### <a name="best-practices-for-wpf-ui-design"></a>WPF Kullanıcı arabirimi tasarımı için en iyi yöntemler

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tasarladığınızda, bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yazın; kodda [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturmaktan kaçının. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturduğunuzda, bunu yerleşik yerelleştirme API 'Leri aracılığıyla kullanıma sunun.

- İçeriği düzenlemek için mutlak konumları ve sabit boyutları kullanmaktan kaçının; Bunun yerine, göreli veya otomatik boyutlandırma kullanın.

  - <xref:System.Windows.Window.SizeToContent%2A> kullanın ve genişlikleri ve yükseklikleri `Auto`ayarlanmış halde tutun.

  - [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s 'yi düzenlemek için <xref:System.Windows.Controls.Canvas> kullanmaktan kaçının.

  - <xref:System.Windows.Controls.Grid> ve boyut paylaşma özelliğini kullanın.

- Yerelleştirilmiş metin genellikle daha fazla alan gerektirdiğinden kenar boşluklarında ek alan sağlayın. Fazladan boşluk, olası asılı karakterler için izin verir.

- Kırpılmasını önlemek için <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> etkinleştirin.

- `xml:lang` özniteliğini ayarlayın. Bu öznitelik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu özelliğin değeri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]içindeki çeşitli özelliklerin davranışını değiştirir. Örneğin, heceleme, yazım denetimi, sayı değiştirme, karmaşık betik şekillendirme ve yazı tipi geri dönüş davranışını değiştirir. [Xaml 'de XML: lang işlemeyi](../../xaml-services/xml-lang-handling-in-xaml.md)ayarlama hakkında daha fazla bilgi için bkz. [WPF için Genelleştirme](globalization-for-wpf.md) .

- Farklı diller için kullanılan yazı tiplerinin daha iyi denetimini elde etmek için özelleştirilmiş bir bileşik yazı tipi oluşturun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\Fonts dizininizde GlobalUserInterface. Composite yazı tipini kullanır.

- Sağdan sola biçimli bir biçimde metin sunan bir kültür içinde yerelleştirilebilecek Gezinti uygulamaları oluşturduğunuzda, sayfanın <xref:System.Windows.Navigation.NavigationWindow><xref:System.Windows.FlowDirection> devralmasını sağlamak için her sayfanın <xref:System.Windows.FlowDirection> açık olarak ayarlayın.

- Bir tarayıcı dışında barındırılan tek başına Gezinti uygulamaları oluşturduğunuzda, ilk uygulamanızın <xref:System.Windows.Application.StartupUri%2A>, bir sayfa yerine bir <xref:System.Windows.Navigation.NavigationWindow> ayarlayın (örneğin, `<Application StartupUri="NavigationWindow.xaml">`). Bu tasarım, pencerenin <xref:System.Windows.FlowDirection> ve gezinti çubuğunun değiştirilmesini sağlar. Daha fazla bilgi ve örnek için bkz. [Genelleştirme giriş sayfası örneği](https://go.microsoft.com/fwlink/?LinkID=159990).

### <a name="best-practices-for-wpf-localization"></a>WPF yerelleştirme için en iyi uygulamalar

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamaları yerelleştirediğinizde, bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- Yerelleştiriciler için ek bağlam sağlamak üzere yerelleştirme açıklamalarını kullanın.

- Öğeler üzerinde <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerini seçmeli olarak atlama yerine yerelleştirmeyi denetlemek için yerelleştirme özniteliklerini kullanın. Daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md) .

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri eklemek ve denetlemek için `msbuild -t:updateuid` ve `-t:checkuid` kullanın. Geliştirme ve yerelleştirme arasındaki değişiklikleri izlemek için <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerini kullanın. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikler yeni geliştirme değişikliklerini yerelleştirmenize yardımcı olur. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri el ile eklerseniz, görev genellikle sıkıcı ve daha az doğru olur.

  - Yerelleştirmeye başladıktan sonra <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerini düzenlemeyin veya değiştirmeyin.

  - Yinelenen <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri kullanmayın (Kopyala ve Yapıştır komutunu kullandığınızda bu ipucunu unutmayın).

  - Geri dönüş için uygun dili belirtmek üzere AssemblyInfo. * içindeki `UltimateResourceFallback` konumunu ayarlayın (örneğin, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).

    Proje dosyanızdaki `<UICulture>` etiketini atlayarak kaynak dilinizi ana derlemeye eklemeye karar verirseniz, `UltimateResourceFallback` konumunu uydu yerine ana derleme olarak ayarlayın (örneğin, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).

## <a name="localize-a-wpf-application"></a>Bir WPF uygulamasını yerelleştirin

Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını yerelleştirmek istediğinizde, birkaç seçeneğiniz vardır. Örneğin, uygulamanızdaki yerelleştirilebilir kaynakları bir XML dosyasına bağlayabilir, bu yerelleştirilebilir metni resx tablolarında saklayabilir veya yorumdur 'ın [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyalarını kullanabilirsiniz. Bu bölüm, çeşitli avantajlar sağlayan XAML 'in BAML formunu kullanan bir yerelleştirme iş akışını açıklar:

- Derlemeden sonra yerelleştirebilirsiniz.

- ' Nin yeni bir sürümünü kullanarak, oluşturduğunuz aynı zamanda yerelleştirebilmeniz için, XAML 'in BAML formunun daha eski bir sürümünden yerelleştirmeler içeren daha yeni bir sürüme güncelleştirebilirsiniz.

- XAML 'in BAML formu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]derlenmiş biçimi olduğundan, derleme zamanında orijinal kaynak öğelerini ve semantiğini doğrulayabilirsiniz.

### <a name="localization-build-process"></a>Yerelleştirme derleme Işlemi

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama geliştirdiğinizde, yerelleştirme için derleme işlemi aşağıdaki gibidir:

- Geliştirici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını oluşturur ve genelleştirir. Proje dosyasında, geliştirici `<UICulture>en-US</UICulture>`, uygulama derlendiğinde, dilden bağımsız bir ana derleme oluşturulur. Bu derleme, tüm yerelleştirilebilir kaynakları içeren bir uydu. resources. dll dosyasına sahiptir. İsteğe bağlı olarak, yerelleştirme API 'lerimiz ana derlemeden ayıklamayı destekledikleri için kaynak dilini ana derlemede tutabilirsiniz.

- Dosya, yapıya derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML 'in BAML biçimine dönüştürülür. Bağımsız olarak nötr `MyDialog.exe` ve bağımsız olarak bağımlı (Ingilizce) `MyDialog.resources.dll` dosyalar Ingilizce konuşuyor müşteri tarafından yayımlanır.

### <a name="localization-workflow"></a>Yerelleştirme Iş akışı

Yerelleştirilmemiş `MyDialog.resources.dll` dosyası derlendikten sonra yerelleştirme işlemi başlar. Özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri ve özellikleri, <xref:System.Windows.Markup.Localizer>altındaki API 'Leri kullanarak XAML 'in BAML formundan anahtar-değer çiftlerine ayıklanır. Yerelleştiriciler, uygulamayı yerelleştirmek için anahtar-değer çiftlerini kullanır. Yerelleştirme tamamlandıktan sonra yeni değerlerden yeni bir. Resource. dll dosyası oluşturabilirsiniz.

Anahtar-değer çiftlerinin anahtarları, özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]geliştirici tarafından verilen değerlerdir `x:Uid`. Bu `x:Uid` değerler, API 'nin, yerelleştirme sırasında geliştirici ve yorumdur arasında gerçekleşen değişiklikleri izleyip birleştirmesini sağlar. Örneğin, uygulama yerelleştirici yerelleştirmeye başladıktan sonra [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] değişirse, minimum çeviri işinin kaybedilmesi için, geliştirme değişikliğini zaten tamamlanmış yerelleştirme çalışmalarla birleştirebilirsiniz.

Aşağıdaki grafik, XAML 'in BAML formunu temel alan tipik bir yerelleştirme iş akışını gösterir. Bu diyagramda geliştirici uygulamayı Ingilizce yazar. Geliştirici WPF uygulamasını oluşturur ve genelleştirir. Proje dosyasında, geliştirici, derleme için `<UICulture>en-US</UICulture>` ayarlıyor ve tüm yerelleştirilebilir kaynakları içeren bir uydu. resources. dll ile bir dilden bağımsız ana derleme oluşturulur. Alternatif olarak, WPF yerelleştirme API 'Leri ana derlemeden ayıklamayı desteklediği için, biri ana derlemede kaynak dilini tutabilir. Oluşturma işleminden sonra XAML, BAML 'de derlenir. Bağımsız olarak nötr MyDialog. exe. resources. dll, Ingilizce konuşan müşterilere gönderilir.

![Yerelleştirme iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Yerelleştirilmiş olmayan iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>WPF yerelleştirme örnekleri

Bu bölüm, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarını nasıl derleyip yerelleştirebileceğinizi anlamanıza yardımcı olacak yerelleştirilmiş uygulamalar örneklerini içerir.

#### <a name="run-dialog-box-example"></a>Çalıştır Iletişim kutusu örneği

Aşağıdaki grafiklerde, **Çalıştır** iletişim kutusu örneğinin çıkışı gösterilmektedir.

**İngilizce:**

![Ingilizce Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Almanca:**

![Alman Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Genel çalıştırma Iletişim kutusu tasarlama**

Bu örnek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir **Çalıştır** iletişim kutusu oluşturur. Bu iletişim kutusu, Microsoft Windows Başlat menüsünden kullanılabilen **Çalıştır** iletişim kutusu ile eşdeğerdir.

Genel iletişim kutuları oluşturmak için bazı önemli noktalar şunlardır:

**Otomatik düzen**

*Window1. xaml içinde:*

`<Window SizeToContent="WidthAndHeight">`

Önceki pencere özelliği, pencereyi içeriğin boyutuna göre otomatik olarak yeniden boyutlandırır. Bu özellik, Windows 'un, yerelleştirme sonrasında boyut arttıkça artan içeriği almasını önler; Ayrıca içerik, yerelleştirme sonrasında boyutu azaldığında gereksiz alanı da kaldırır.

`<Grid x:Uid="Grid_1">`

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme API 'Lerinin düzgün çalışması için <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri gereklidir.

Bunlar, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]geliştirme ve yerelleştirme arasındaki değişiklikleri izlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme API 'Leri tarafından kullanılır. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikler, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]daha eski bir yerelleştirmeyle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daha yeni bir sürümünü birleştirmenizi sağlar. Bir komut kabuğunda `msbuild -t:updateuid RunDialog.csproj` çalıştırarak bir <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliği eklersiniz. Bu, <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri eklemenin önerilen yöntemidir çünkü bunları el ile eklemek genellikle zaman alabilir ve daha az doğru olur. `msbuild -t:checkuid RunDialog.csproj`çalıştırılarak <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerinin doğru şekilde ayarlandığını kontrol edebilirsiniz.

[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]otomatik düzenden faydalanmak için faydalı bir denetim olan <xref:System.Windows.Controls.Grid> denetimi kullanılarak yapılandırılır. İletişim kutusunun üç satıra ve beş sütuna bölündüğüne unutmayın. Satır ve sütun tanımlarından biri sabit boyuta sahip değil; Bu nedenle, her hücrede konumlandırılmış [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri, yerelleştirme sırasında boyut artışına ve düşüşe uyum sağlayabilir.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

**Open:** label ve <xref:System.Windows.Controls.ComboBox> yerleştirildiği ilk iki sütun, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplam genişliğinin yüzde 10 ' unu kullanır.

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Örneğin, <xref:System.Windows.Controls.Grid>paylaşılan boyutlandırma özelliğini kullandığını unutmayın. Son üç sütun, kendisini aynı <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>yerleştirerek bundan faydalanır. Özelliğin adından beklendiğinden, bu sütunların aynı boyutta paylaşmasına izin verir. Yani "Gözatılacak..." "Durchsuchen..." daha uzun dizeye yerelleştirilir ve küçük bir "Tamam" düğmesine ve orantısız bir büyük "Durchsuchen..." olması yerine tüm düğmelerin genişliği artar. Bu.

**XML: lang**

`xml:lang="en-US"`

[Xaml 'de XML: lang işleme](../../xaml-services/xml-lang-handling-in-xaml.md) [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]kök öğesine yerleştirilmiş olduğunu fark edin. Bu özellik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu değer, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli özellikler tarafından kullanılır ve yerelleştirme sırasında uygun şekilde değiştirilmelidir. Bu değer, heceleme ve yazım denetimi kelimeleri için kullanılacak dil sözlüğünü değiştirir. Ayrıca, basamakların görüntülenmesini ve yazı tipi geri dönüş sisteminin hangi yazı tipinin kullanılacağını nasıl seçeceğine de etkileri vardır. Son olarak, özellik sayıların görüntülenme şeklini etkiler ve karmaşık betiklerdeki metinlerin yazıldığı şekilde şekillendirilir. Varsayılan değer "en-US" dir.

**Uydu kaynak derlemesi oluşturma**

*. Csproj içinde:*

`.csproj` dosyasını düzenleyin ve aşağıdaki etiketi bir koşulsuz `<PropertyGroup>`ekleyin:

`<UICulture>en-US</UICulture>`

`UICulture` bir değer eklenmesine dikkat edin. Bu, en-US gibi geçerli bir <xref:System.Globalization.CultureInfo> değere ayarlandığında, projenin oluşturulması içindeki tüm yerelleştirilebilir kaynaklarla bir uydu derlemesi oluşturacaktır.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

Tüm kültürler için aynı görünmesi gerektiğinden `RunIcon.JPG` yerelleştirilmesi gerekmez. `Localizable`, uydu derlemesi yerine dilden bağımsız ana derlemede kalacak şekilde `false` olarak ayarlanır. Tüm noncompilable kaynaklarının varsayılan değeri `Localizable` `true`olarak ayarlanmıştır.

**Çalıştır Iletişim kutusunu yerelleştirme**

**Parse**

Uygulamayı oluşturduktan sonra, yerelleştirmedeki ilk adım, yardımcı derlemeden yerelleştirilebilir kaynakların ayrıştırılmasından oluşur. Bu konunun amaçları doğrultusunda, [LocBaml araç örneğinde](https://go.microsoft.com/fwlink/?LinkID=160016)bulunan örnek LocBaml aracını kullanın. LocBaml 'in yalnızca yerelleştirme sürecinizi karşılayan bir yerelleştirme aracı oluşturmaya başlamanıza yardımcı olacak bir örnek araç olduğunu unutmayın. LocBaml kullanarak, "RunDialog. resources. dll. CSV" dosyası oluşturmak için şunu çalıştırın: **LocBaml/parse RunDialog. resources. dll/out:** .

**Başlat**

Bu dosyayı düzenlemek için Unicode 'U destekleyen en sevdiğiniz CSV düzenleyicisini kullanın. Yerelleştirme kategorisi "none" olan tüm girişleri filtreleyin. Aşağıdaki girişleri görmeniz gerekir:

|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Düğme|Tamam|
|Button_2: System. Windows. Controls. Button. $Content|Düğme|İptal|
|Button_3: System. Windows. Controls. Button. $Content|Düğme|Gözatmaya...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Metin|Bir program, klasör, belge veya Internet kaynağı adı yazın ve Windows bunu sizin için açar.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Metin|Açın|
|Window_1: System. Windows. Window. title|Başlık|Çalıştır|

Uygulamayı Almanca olarak yerelleştirirken aşağıdaki Çeviriler gereklidir:

|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Düğme|Tamam|
|Button_2: System. Windows. Controls. Button. $Content|Düğme|Abbrechen|
|Button_3: System. Windows. Controls. Button. $Content|Düğme|Durchsuchen...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Metin|Geben, adam EMS, Ordyalar, Dokuments Oder einer ınternetresource a.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Metin|Öffnen:|
|Window_1: System. Windows. Window. title|Başlık|Çalıştır|

**Üretecek**

Yerelleştirmenin son adımı, yeni yerelleştirilmiş uydu derlemesini oluşturmayı içerir. Bu, aşağıdaki LocBaml komutuyla gerçekleştirilebilir:

**LocBaml. exe/Generate RunDialog. resources. dll/Trans: RunDialog. resources. dll. CSV/Out:. /Cul: de-DE**

Almanya penceresinde, bu resources. dll ana derlemenin yanındaki bir de klasöre yerleştirilmişse, bu kaynak en-US klasörü yerine otomatik olarak yüklenir. Bunu test etmek için Windows 'un Almanca sürümüne sahip değilseniz, kültürü kullandığınız Windows kültürü (örneğin, `en-US`) olarak ayarlayın ve özgün kaynaklar DLL 'sini değiştirin.

**Uydu kaynak yüklemesi**

|MyDialog. exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kod|Orijinal Ingilizce BAML|Yerelleştirilmiş BAML|
|Genel olarak nötr kaynaklar|Ingilizce 'deki diğer kaynaklar|Almanca 'ya yerelleştirilmiş diğer kaynaklar|

.NET Framework, uygulamanın `Thread.CurrentThread.CurrentUICulture`göre hangi uydu kaynakları derlemesinin yükleneceğini otomatik olarak seçer. Bu, varsayılan olarak Windows işletim sisteminin kültürüne göre yapılır. Yani, Almanca Windows kullanıyorsanız, de-DE\MyDialog.resources.dll yüklenir, en-US\MyDialog.resources.dll yüklenir. Projenizin AssemblyInfo. * ' de NeutralResourcesLanguage belirterek uygulamanız için en son geri dönüş kaynağını ayarlayabilirsiniz. Örneğin şunu belirtirseniz:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

daha sonra, de-DE\MyDialog.resources.dll veya de\MyDialog.resources.dll her ikisi de kullanılamazsa, en-US\MyDialog.resources.dll Almanca Windows ile kullanılacaktır.

### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Suudi Arabistan giriş sayfası

Aşağıdaki grafiklerde Ingilizce ve Arapça bir giriş sayfası gösterilmektedir. Bu grafikleri üreten tüm örnek için bkz. [Genelleştirme giriş sayfası örneği](https://go.microsoft.com/fwlink/?LinkID=159990).

**İngilizce:**

![Ingilizce giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arapça:**

![Arapça giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Küresel Microsoft ana sayfası tasarlama

Microsoft Suudi Arabistan Web sitesinin bu şekilde sahte olması, RightToLeft dilleri için sunulan Genelleştirme özelliklerini gösterir. Ibranice ve Arapça gibi dillerin sağdan sola okuma düzeni vardır. bu nedenle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzeninin, Ingilizce gibi soldan sağa dillerde olması çok farklı bir şekilde düzenlenmelidir. Soldan sağa bir dilden sağdan sola bir dile veya tam tersi bir şekilde yerelleştirilmesi oldukça zor olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu tür yerelleştirmeleri çok daha kolay hale getirmek için tasarlanmıştır.

**FlowDirection**

*Giriş sayfası. xaml:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

<xref:System.Windows.Controls.Page><xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğine dikkat edin. Bu özelliğin <xref:System.Windows.FlowDirection.RightToLeft> olarak değiştirilmesi, <xref:System.Windows.Controls.Page> ve alt öğelerinin <xref:System.Windows.FrameworkElement.FlowDirection%2A> bir Arapça Kullanıcı tarafından beklenecek şekilde, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzeninin sağdan sola olacak şekilde çevrilmesine izin verecek şekilde değişir. Herhangi bir öğe üzerinde açık bir <xref:System.Windows.FrameworkElement.FlowDirection%2A> belirterek devralma davranışını geçersiz kılabilir. <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği, herhangi bir <xref:System.Windows.FrameworkElement> veya belge ile ilgili herhangi bir öğede kullanılabilir ve örtük bir <xref:System.Windows.FlowDirection.LeftToRight>değeri vardır.

Kök <xref:System.Windows.FrameworkElement.FlowDirection%2A> değiştirildiğinde arka plan gradyan fırçaları doğru şekilde çevrildiğini de gözlemleyin:

**FlowDirection = "Solttoright"**

![Soldan sağa gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection = "RightToLeft"**

![Sağdan sola gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Paneller ve denetimler için sabit boyutlar kullanmaktan kaçının**

Giriş sayfası. xaml 'ye göz atın, en üstteki <xref:System.Windows.Controls.DockPanel>[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için belirtilen sabit genişlik ve yükseklikten, başka bir sabit boyut olmadığına dikkat edin. Kaynak metinden daha uzun olabilecek Yerelleştirilmiş metnin kırpılmasını önlemek için sabit boyutlar kullanmaktan kaçının. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölmeleri ve denetimleri, içerdikleri içeriğe göre otomatik olarak yeniden boyutlandırılır. Çoğu denetim Ayrıca daha fazla denetim için ayarlayabileceğiniz en düşük ve en büyük boyutlara sahiptir (örneğin, MinWidth = "20"). <xref:System.Windows.Controls.Grid>, '\*' kullanarak göreli genişlikleri ve yükseklikleri de ayarlayabilirsiniz (örneğin, `Width="0.25*"`) veya hücre boyutu paylaşımı özelliğini kullanabilirsiniz.

**Yerelleştirme açıklamaları**

İçeriğin belirsiz ve çevrilme zor olabileceği birçok durum vardır. Geliştirici veya tasarımcı, yerelleştirme açıklamaları aracılığıyla Yereller için ek bağlam ve açıklamalar sağlama olanağına sahiptir. Örneğin, yerelleştirme. aşağıdaki açıklamalar '&#124;' karakterinin kullanımını açıklığa kavuşturulur.

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Bu yorum TextBlock_1's içeriğiyle ilişkili olur ve LocBaml aracı söz konusu olduğunda (bkz. [bir uygulamayı yerelleştirin](how-to-localize-an-application.md)), output. csv dosyasındaki TextBlock_1 satırının 6. sütununda görülebilir:

|Kaynak anahtarı|Kategori|Ama|Düzenlenerek|Yorum|Değer|
|-|-|-|-|-|-|
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Metin|TRUE|TRUE|Bu karakter, dekoratif bir kural olarak kullanılır.|&#124;|

Açıklamalar, aşağıdaki sözdizimi kullanılarak herhangi bir öğenin içeriğine veya özelliğine yerleştirilebilir:

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Yerelleştirme öznitelikleri**

Genellikle geliştirici veya yerelleştirme Yöneticisi, Yerelleştiricilerin okuyup değiştirebilecekleri denetimi gerektirir. Örneğin, yerelleştiriciye şirketinizin adını ya da yasal bir şekilde çevirmesini istemeyebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yerelleştirme aracınızın öğeleri kilitlemek, gizlemek veya sıralamak için kullanabileceği bir öğenin içeriğinin veya özelliğinin okunabilirliğini, modifibilirliği ve kategorisini ayarlamanızı sağlayan öznitelikler sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Localization.Attributes%2A>. Bu örneğin amaçları doğrultusunda, LocBaml aracı yalnızca bu özniteliklerin değerlerini çıktı olarak verir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerinin hepsi bu öznitelikler için varsayılan değerlere sahiptir, ancak bunları geçersiz kılabilirsiniz. Örneğin, aşağıdaki örnek `TextBlock_1` için varsayılan yerelleştirme özniteliklerini geçersiz kılar ve içeriği yerellerde okunabilir ancak değiştirilemeyen olarak ayarlar.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Okunabilirlik ve modifiyeteneğinin özniteliklerine ek olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Yerelleştiricilerin daha fazla bağlam sağlamak için kullanılabilen ortak kullanıcı arabirimi kategorilerinin (<xref:System.Windows.LocalizationCategory>) bir listesini sağlar. Platform denetimleri için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan Kategoriler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de geçersiz kılınabilir:

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağladığı varsayılan yerelleştirme öznitelikleri, kod aracılığıyla da geçersiz kılınabilir, bu sayede özel denetimlerin doğru varsayılan değerlerini doğru şekilde ayarlayabilirsiniz. Örneğin:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayarlanan örnek başına öznitelikler, özel denetimlerde kodda ayarlanan değerlere göre önceliğe sahip olur. Öznitelikler ve açıklamalar hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).

**Yazı tipi geri dönüş ve bileşik yazı tipleri**

Verilen bir kod noktası aralığını desteklemeyen bir yazı tipi belirtirseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Windows\Fonts dizininizde bulunan genel kullanıcı arabirimi. compositefont kullanılarak otomatik olarak bir öğesine geri yüklenir. Bileşik yazı tipleri tıpkı diğer yazı tiplerinde olduğu gibi çalışır ve bir öğenin `FontFamily` (örneğin, `FontFamily="Global User Interface"`) ayarlanarak açıkça kullanılabilir. Kendi bileşik yazı tipi oluşturarak ve belirli kod noktası aralıkları ve dilleri için kullanılacak yazı tipini belirterek kendi yazı tipi geri dönüş tercihinizi belirtebilirsiniz.

Bileşik yazı tipleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.FontFamily>.

**Microsoft giriş sayfasını yerelleştirme**

Bu uygulamayı yerelleştirmek için Run Iletişim kutusuyla aynı adımları izleyebilirsiniz. Arapça için yerelleştirilmiş. csv dosyası, [Genelleştirme giriş sayfası örneğinde](https://go.microsoft.com/fwlink/?LinkID=159990)sizin için kullanılabilir.
