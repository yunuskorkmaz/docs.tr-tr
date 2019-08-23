---
title: WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: e34b61e14db1e7839173658d71a70240d63c5f8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917575"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış

Ürününüzün kullanılabilirliğini yalnızca bir dille sınırlandırdığınızda, olası müşteri tabanınızı dünyanın 6.500.000.000 popülasyonızın bir bölümü ile sınırlandırdığınızda. Uygulamalarınızın küresel bir hedef kitleye ulaşmasını istiyorsanız, ürününüzün düşük maliyetli yerelleştirilmesi, daha fazla müşteriye ulaşmak için en iyi ve en ekonomik yolların biridir.

Bu genel bakışta ' de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Genelleştirme ve yerelleştirme tanıtılmıştır. Genelleştirme, birden çok konumda gerçekleştiren uygulamaların tasarımını ve geliştirilmesini geliştirmektedir. Örneğin, Genelleştirme farklı kültürler içindeki kullanıcılar için yerelleştirilmiş kullanıcı arabirimlerini ve bölgesel verileri destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]otomatik düzen, uydu derlemeleri ve yerelleştirilmiş öznitelikler ve açıklama ekleme dahil olmak üzere Genelleştirilmiş tasarım özellikleri sağlar.

Yerelleştirme, uygulama kaynaklarının, uygulamanın desteklediği belirli kültürler için yerelleştirilmiş sürümlere çevirmesidir. ' De [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yerelleştirmeniz durumunda, <xref:System.Windows.Markup.Localizer> ad alanındaki API 'leri kullanırsınız. Bu API 'Ler [LocBaml aracı örnek](https://go.microsoft.com/fwlink/?LinkID=160016) komut satırı aracını güçlendirin. LocBaml oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF 'de Genelleştirme ve yerelleştirme için en iyi uygulamalar

Bu bölümün sağladığı Kullanıcı arabirimi tasarımını ve Yerelleştirmede ilgili ipuçlarını izleyerek, yerleşik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak bulunan Genelleştirme ve yerelleştirme işlevlerinden en iyi şekilde birini yapabilirsiniz.

### <a name="best-practices-for-wpf-ui-design"></a>WPF Kullanıcı arabirimi tasarımı için en iyi yöntemler

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Tabanlı[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bir tasarladığınızda, bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- Yazın; kodda oluşturmaktan[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaçının. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' Yi kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]oluşturduğunuzda [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , yerleşik yerelleştirme API 'leri aracılığıyla bunu kullanıma sunun.

- İçeriği düzenlemek için mutlak konumları ve sabit boyutları kullanmaktan kaçının; Bunun yerine, göreli veya otomatik boyutlandırma kullanın.

  - Kullanın <xref:System.Windows.Window.SizeToContent%2A> ve genişlikleri ve yükseklikleri olarak `Auto`ayarlayın.

  - Öğeleri düzenlemek için kullanmaktan kaçının. <xref:System.Windows.Controls.Canvas> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

  - Ve <xref:System.Windows.Controls.Grid> boyutunu paylaşma özelliğini kullanın.

- Yerelleştirilmiş metin genellikle daha fazla alan gerektirdiğinden kenar boşluklarında ek alan sağlayın. Fazladan boşluk, olası asılı karakterler için izin verir.

- Kırpması <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> önlemek <xref:System.Windows.Controls.TextBlock> için ' i etkinleştirin.

- `xml:lang` Özniteliğini ayarlayın. Bu öznitelik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu özelliğin değeri, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]çeşitli özelliklerin davranışını değiştirir. Örneğin, heceleme, yazım denetimi, sayı değiştirme, karmaşık betik şekillendirme ve yazı tipi geri dönüş davranışını değiştirir. [Xaml 'de XML: lang işlemeyi](../../xaml-services/xml-lang-handling-in-xaml.md)ayarlama hakkında daha fazla bilgi için bkz. [WPF için Genelleştirme](globalization-for-wpf.md) .

- Farklı diller için kullanılan yazı tiplerinin daha iyi denetimini elde etmek için özelleştirilmiş bir bileşik yazı tipi oluşturun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\Fonts dizininizde GlobalUserInterface. Composite yazı tipini kullanır.

- Sağdan sola biçimli bir biçimde metin sunan bir kültür içinde yerelleştirilebilecek Gezinti uygulamaları oluşturduğunuzda, sayfanın öğesinden <xref:System.Windows.FlowDirection> <xref:System.Windows.Navigation.NavigationWindow>devralmasını <xref:System.Windows.FlowDirection> sağlamak için her sayfanın açık olarak ayarlayın.

- Bir tarayıcı dışında barındırılan tek başına Gezinti uygulamaları oluşturduğunuzda, ilk uygulamanız <xref:System.Windows.Application.StartupUri%2A> için öğesini bir sayfa yerine bir <xref:System.Windows.Navigation.NavigationWindow> olarak ayarlayın (örneğin, `<Application StartupUri="NavigationWindow.xaml">`). Bu tasarım, <xref:System.Windows.FlowDirection> pencereyi ve gezinti çubuğunu değiştirmenize olanak sağlar. Daha fazla bilgi ve örnek için bkz. [Genelleştirme giriş sayfası örneği](https://go.microsoft.com/fwlink/?LinkID=159990).

### <a name="best-practices-for-wpf-localization"></a>WPF yerelleştirme için en iyi uygulamalar

Tabanlı uygulamaları yerelleştirediğinizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- Yerelleştiriciler için ek bağlam sağlamak üzere yerelleştirme açıklamalarını kullanın.

- Öğelerin özelliklerini seçmeli olarak atlama <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> yerine yerelleştirmeyi denetlemek için yerelleştirme özniteliklerini kullanın. Daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md) .

- İçindeki `msbuild -t:updateuid` özellikleri `-t:checkuid` <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> eklemek[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve denetlemek için ve kullanın. Geliştirme <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> ve yerelleştirme arasındaki değişiklikleri izlemek için özellikleri kullanın. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Özellikler yeni geliştirme değişikliklerini yerelleştirmenize yardımcı olur. ' A <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]el ile Özellikler eklerseniz, görev genellikle sıkıcı ve daha az doğru olur.

  - Yerelleştirmeye başladıktan sonra özellikleri <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> düzenlemeyin veya değiştirmeyin.

  - Yinelenen <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikler kullanmayın (Kopyala ve Yapıştır komutunu kullandığınızda bu ipucunu unutmayın).

  - Geri dönüş için uygun dili (örneğin, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`) belirtmek üzere AssemblyInfo. * içinde konumayarlayın.`UltimateResourceFallback`

    Proje dosyanızdaki `<UICulture>` etiketi atlayarak kaynak dilinizi ana derlemeye eklemeye karar verirseniz, `UltimateResourceFallback` konumu uydu yerine ana derleme olarak ayarlayın (örneğin, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).

## <a name="localize-a-wpf-application"></a>Bir WPF uygulamasını yerelleştirin

Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı yerelleştirmek istediğinizde, birkaç seçeneğiniz vardır. Örneğin, uygulamanızdaki yerelleştirilebilir kaynakları bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyaya bağlayabilir, yerelleştirilebilir metni resx tablolarında saklayabilir veya yerelleştirici kullanım [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyalarınıza sahip olabilirsiniz. Bu bölüm, çeşitli avantajlar sağlayan XAML 'in BAML formunu kullanan bir yerelleştirme iş akışını açıklar:

- Derlemeden sonra yerelleştirebilirsiniz.

- ' Nin yeni bir sürümünü kullanarak, oluşturduğunuz aynı zamanda yerelleştirebilmeniz için, XAML 'in BAML formunun daha eski bir sürümünden yerelleştirmeler içeren daha yeni bir sürüme güncelleştirebilirsiniz.

- XAML 'in BAML formu derlenmiş biçimde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olduğundan, derleme zamanında orijinal kaynak öğelerini ve semantiğini doğrulayabilirsiniz.

### <a name="localization-build-process"></a>Yerelleştirme derleme Işlemi

Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama geliştirirken, yerelleştirme için derleme işlemi aşağıdaki gibidir:

- Geliştirici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı oluşturur ve genelleştirir. Geliştirici, uygulamanın derlenmesi durumunda, dilden `<UICulture>en-US</UICulture>` bağımsız bir ana derlemenin oluşturulduğu proje dosyasında ayarlanır. Bu derleme, tüm yerelleştirilebilir kaynakları içeren bir uydu. resources. dll dosyasına sahiptir. İsteğe bağlı olarak, yerelleştirme API 'lerimiz ana derlemeden ayıklamayı destekledikleri için kaynak dilini ana derlemede tutabilirsiniz.

- Dosya, yapıya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlendiğinde xaml 'in BAML biçimine dönüştürülür. Bağımsız olarak nötr `MyDialog.exe` ve önemli (İngilizce) `MyDialog.resources.dll` dosyalar İngilizce konuşuyor müşterisi tarafından yayımlanır.

### <a name="localization-workflow"></a>Yerelleştirme Iş akışı

Yerelleştirilmemiş `MyDialog.resources.dll` dosya derlendikten sonra yerelleştirme işlemi başlar. Orijinalinizdeki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler ve özellikler, altındaki <xref:System.Windows.Markup.Localizer>API 'leri kullanarak XAML 'in BAML formundan anahtar-değer çiftlerine ayıklanır. Yerelleştiriciler, uygulamayı yerelleştirmek için anahtar-değer çiftlerini kullanır. Yerelleştirme tamamlandıktan sonra yeni değerlerden yeni bir. Resource. dll dosyası oluşturabilirsiniz.

Anahtar-değer çiftlerinin `x:Uid` anahtarları, başlangıçtaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]geliştirici tarafından verilen değerlerdir. Bu `x:Uid` değerler, API 'nin, yerelleştirme sırasında geliştirici ve yorumdur arasında gerçekleşen değişiklikleri izleyip birleştirmesini sağlar. Örneğin, geliştiriciler yerelleştirici yerelleştirmeye başladıktan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sonra değişiklik yaptığı takdirde, en az sayıda çeviri işinin kaybedilmesi için geliştirme değişikliğini zaten tamamlanmış yerelleştirme ile birleştirebilirsiniz.

Aşağıdaki grafik, XAML 'in BAML formunu temel alan tipik bir yerelleştirme iş akışını gösterir. Bu diyagramda geliştirici uygulamayı Ingilizce yazar. Geliştirici WPF uygulamasını oluşturur ve genelleştirir. Geliştirme `<UICulture>en-US</UICulture>` proje dosyasında, derleme için bir dilden bağımsız ana derleme, tüm yerelleştirilebilir kaynakları içeren bir uydu. resources. dll ile oluşturulur. Alternatif olarak, WPF yerelleştirme API 'Leri ana derlemeden ayıklamayı desteklediği için, biri ana derlemede kaynak dilini tutabilir. Oluşturma işleminden sonra XAML, BAML 'de derlenir. Bağımsız olarak nötr MyDialog. exe. resources. dll, Ingilizce konuşan müşterilere gönderilir.

![Yerelleştirme iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Yerelleştirilmiş olmayan iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>WPF yerelleştirme örnekleri

Bu bölüm, uygulamaları nasıl derleyip yerelleştirebileceğinizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] anlamanıza yardımcı olacak yerelleştirilmiş uygulamaların örneklerini içerir.

#### <a name="run-dialog-box-example"></a>Çalıştır Iletişim kutusu örneği

Aşağıdaki grafiklerde, **Çalıştır** iletişim kutusu örneğinin çıkışı gösterilmektedir.

**İngilizce:**

![Ingilizce Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Almanca:**

![Alman Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Genel çalıştırma Iletişim kutusu tasarlama**

Bu örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir Çalıştır iletişim kutusu oluşturur. Bu iletişim kutusu, [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Başlat menüsünden kullanılabilen **Çalıştır** iletişim kutusu ile eşdeğerdir.

Genel iletişim kutuları oluşturmak için bazı önemli noktalar şunlardır:

**Otomatik düzen**

*Window1. xaml içinde:*

`<Window SizeToContent="WidthAndHeight">`

Önceki pencere özelliği, pencereyi içeriğin boyutuna göre otomatik olarak yeniden boyutlandırır. Bu özellik, Windows 'un, yerelleştirme sonrasında boyut arttıkça artan içeriği almasını önler; Ayrıca içerik, yerelleştirme sonrasında boyutu azaldığında gereksiz alanı da kaldırır.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Yerelleştirme API 'lerinin doğru çalışması için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellikler gereklidir.

Geliştirme ve yerelleştirme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]arasındaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] değişiklikleri izlemek için yerelleştirme API 'leri tarafından kullanılır. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Özellikleri, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daha eski bir yerelleştirmesiyle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]uygulamasının daha yeni bir sürümünü birleştirmenizi sağlar. Komut kabuğu 'nda <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> çalıştırarak `msbuild -t:updateuid RunDialog.csproj` bir özellik eklersiniz. Bu, özelliklerin eklenmesi <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> için önerilen yöntemdir, çünkü bunları el ile eklemek genellikle zaman alabilir ve daha az doğru olur. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikleri çalışırken`msbuild -t:checkuid RunDialog.csproj`doğru şekilde ayarlandığını kontrol edebilirsiniz.

, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' <xref:System.Windows.Controls.Grid> De[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]otomatik düzenden yararlanmak için faydalı bir denetim olan denetim kullanılarak yapılandırılır. İletişim kutusunun üç satıra ve beş sütuna bölündüğüne unutmayın. Satır ve sütun tanımlarından biri sabit boyuta sahip değil; Bu nedenle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her hücrede konumlandırılmış öğeler, yerelleştirme sırasında boyut artışına ve düşüşe uyum sağlayabilir.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

**Open:** Label ve yerleştirildiği ilk iki sütun <xref:System.Windows.Controls.ComboBox> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplam genişliğin yüzde 10 ' unu kullanır.

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Örneğin, öğesinin <xref:System.Windows.Controls.Grid>paylaşılan boyutlandırma özelliğini kullandığını unutmayın. Son üç sütun, kendisini aynı <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>yerleştirerek bu özelliklerden yararlanır. Özelliğin adından beklendiğinden, bu sütunların aynı boyutta paylaşmasına izin verir. Yani "Gözatılacak..." "Durchsuchen..." daha uzun dizeye yerelleştirilir ve küçük bir "Tamam" düğmesine ve orantısız bir büyük "Durchsuchen..." olması yerine tüm düğmelerin genişliği artar. Bu.

**XML: lang**

`xml:lang="en-US"`

[Xaml 'de XML: lang işleme](../../xaml-services/xml-lang-handling-in-xaml.md) öğesinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]kök öğesine yerleştirilmiş olduğunu fark edin. Bu özellik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu değer, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli özellikler tarafından kullanılır ve yerelleştirme sırasında uygun şekilde değiştirilmelidir. Bu değer, heceleme ve yazım denetimi kelimeleri için kullanılacak dil sözlüğünü değiştirir. Ayrıca, basamakların görüntülenmesini ve yazı tipi geri dönüş sisteminin hangi yazı tipinin kullanılacağını nasıl seçeceğine de etkileri vardır. Son olarak, özellik sayıların görüntülenme şeklini etkiler ve karmaşık betiklerdeki metinlerin yazıldığı şekilde şekillendirilir. Varsayılan değer "en-US" dir.

**Uydu kaynak derlemesi oluşturma**

*. Csproj içinde:*

Dosyayı düzenleyin ve aşağıdaki etiketi koşulsuz `<PropertyGroup>`bir dosyaya ekleyin: `.csproj`

`<UICulture>en-US</UICulture>`

Bir `UICulture` değer eklenmesine dikkat edin. Bu, en-US gibi geçerli <xref:System.Globalization.CultureInfo> bir değere ayarlandığında, projenin oluşturulması içindeki tüm yerelleştirilebilir kaynaklarla bir uydu derlemesi oluşturacaktır.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

Tüm `RunIcon.JPG` kültürler için aynı görünmesi gerektiğinden, yerelleştirilmesi gerekmez. `Localizable`, uydu derlemesi `false` yerine dilden bağımsız ana derlemede kalacak şekilde olarak ayarlanır. Tüm noncompilable kaynaklarının `Localizable` varsayılan değeri olarak `true`ayarlanır.

**Çalıştır Iletişim kutusunu yerelleştirme**

**Parse**

Uygulamayı oluşturduktan sonra, yerelleştirmedeki ilk adım, yardımcı derlemeden yerelleştirilebilir kaynakların ayrıştırılmasından oluşur. Bu konunun amaçları doğrultusunda, [LocBaml araç örneğinde](https://go.microsoft.com/fwlink/?LinkID=160016)bulunan örnek LocBaml aracını kullanın. LocBaml 'in yalnızca yerelleştirme sürecinizi karşılayan bir yerelleştirme aracı oluşturmaya başlamanıza yardımcı olacak bir örnek araç olduğunu unutmayın. LocBaml kullanarak, ayrıştırmak için aşağıdakileri çalıştırın: **LocBaml/parse RunDialog. resources. dll/out:** bir "RunDialog. resources. dll. csv" dosyası oluşturmak için.

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

Almanya penceresinde, bu resources. dll ana derlemenin yanındaki bir de klasöre yerleştirilmişse, bu kaynak en-US klasörü yerine otomatik olarak yüklenir. Bunu test etmek için Windows 'un Almanca sürümüne sahip değilseniz, kültürü kullandığınız Windows kültürüne (örneğin, `en-US`) ayarlayın ve özgün kaynaklar dll 'sini değiştirin.

**Uydu kaynak yüklemesi**

|MyDialog. exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kod|Orijinal Ingilizce BAML|Yerelleştirilmiş BAML|
|Genel olarak nötr kaynaklar|Ingilizce 'deki diğer kaynaklar|Almanca 'ya yerelleştirilmiş diğer kaynaklar|

.NET Framework, uygulamayı `Thread.CurrentThread.CurrentUICulture`temel alarak hangi uydu kaynakları derlemesinin yükleneceğini otomatik olarak seçer. Bu, varsayılan olarak Windows işletim sisteminin kültürüne göre yapılır. Yani, Almanca Windows kullanıyorsanız, de-DE\MyDialog.resources.dll yüklenir, en-US\MyDialog.resources.dll yüklenir. Projenizin AssemblyInfo. * ' de NeutralResourcesLanguage belirterek uygulamanız için en son geri dönüş kaynağını ayarlayabilirsiniz. Örneğin şunu belirtirseniz:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

daha sonra, de-DE\MyDialog.resources.dll veya de\MyDialog.resources.dll her ikisi de kullanılamazsa, en-US\MyDialog.resources.dll Almanca Windows ile kullanılacaktır.

### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Suudi Arabistan giriş sayfası

Aşağıdaki grafiklerde Ingilizce ve Arapça bir giriş sayfası gösterilmektedir. Bu grafikleri üreten tüm örnek için bkz. [Genelleştirme giriş sayfası örneği](https://go.microsoft.com/fwlink/?LinkID=159990).

**İngilizce:**

![Ingilizce giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arapça:**

![Arapça giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Küresel Microsoft ana sayfası tasarlama

Microsoft Suudi Arabistan Web sitesinin bu şekilde sahte olması, RightToLeft dilleri için sunulan Genelleştirme özelliklerini gösterir. İbranice ve Arapça gibi dillerin sağdan sola okuma düzeni vardır. bu nedenle, Düzen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle İngilizce gibi soldan sağa dillerde olacak şekilde oldukça farklı bir şekilde düzenlenmelidir. Soldan sağa bir dilden sağdan sola bir dile veya tam tersi bir şekilde yerelleştirilmesi oldukça zor olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu tür yerelleştirmeleri çok daha kolay hale getirmek için tasarlanmıştır.

**FlowDirection**

*Giriş sayfası. xaml:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

<xref:System.Windows.FrameworkElement.FlowDirection%2A> Özelliği üzerinde<xref:System.Windows.Controls.Page>olduğuna dikkat edin. Bu özelliğin olarak <xref:System.Windows.FlowDirection.RightToLeft> değiştirilmesi <xref:System.Windows.Controls.Page> , ve alt <xref:System.Windows.FrameworkElement.FlowDirection%2A> öğelerinin, Arapça bir kullanıcı tarafından beklenecek şekilde, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğenin düzeninin sağdan sola dönüşecek şekilde değiştirilmesini sağlayacak şekilde değişecek. Herhangi bir öğe üzerinde açık <xref:System.Windows.FrameworkElement.FlowDirection%2A> bir şekilde belirterek devralma davranışını geçersiz kılabilir. Özelliği herhangi bir veya belge ile <xref:System.Windows.FrameworkElement> ilgili herhangi bir öğede kullanılabilir ve örtülü bir değeri <xref:System.Windows.FlowDirection.LeftToRight>vardır. <xref:System.Windows.FrameworkElement.FlowDirection%2A>

Kök <xref:System.Windows.FrameworkElement.FlowDirection%2A> değiştirildiğinde arka plan gradyanı fırçalarının doğru şekilde çevrildiğini de gözlemleyin:

**FlowDirection="LeftToRight"**

![Soldan sağa gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection="RightToLeft"**

![Sağdan sola gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Paneller ve denetimler için sabit boyutlar kullanmaktan kaçının**

Giriş sayfası. xaml ' ye göz atın, en üstte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel>yer alan sabit genişlik ve yüksekliğin yanı sıra, başka bir sabit boyut olmadığına dikkat edin. Kaynak metinden daha uzun olabilecek Yerelleştirilmiş metnin kırpılmasını önlemek için sabit boyutlar kullanmaktan kaçının. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Panolar ve denetimler, içerdikleri içeriğe göre otomatik olarak yeniden boyutlandırılır. Çoğu denetim Ayrıca daha fazla denetim için ayarlayabileceğiniz en düşük ve en büyük boyutlara sahiptir (örneğin, MinWidth = "20"). İle <xref:System.Windows.Controls.Grid>, '\*' kullanarak göreli genişlikleri ve yükseklikleri de ayarlayabilirsiniz (örneğin, `Width="0.25*"`) veya hücre boyutu paylaşım özelliğini kullanabilirsiniz.

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

Genellikle geliştirici veya yerelleştirme Yöneticisi, Yerelleştiricilerin okuyup değiştirebilecekleri denetimi gerektirir. Örneğin, yerelleştiriciye şirketinizin adını ya da yasal bir şekilde çevirmesini istemeyebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yerelleştirme aracınızın öğeleri kilitlemek, gizlemek veya sıralamak için kullanabileceği bir öğenin içeriğinin veya özelliğinin okunabilirliğini, modifilebilirliği ve kategorisini ayarlamanıza olanak tanıyan öznitelikler sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Localization.Attributes%2A>. Bu örneğin amaçları doğrultusunda, LocBaml aracı yalnızca bu özniteliklerin değerlerini çıktı olarak verir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin hepsi bu öznitelikler için varsayılan değerlere sahiptir, ancak bunları geçersiz kılabilirsiniz. Örneğin, aşağıdaki örnek için `TextBlock_1` varsayılan yerelleştirme özniteliklerini geçersiz kılar ve içeriği yerellerde okunabilir ancak değiştirilemeyen olarak ayarlar.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Okunabilirlik ve modifibeceri özniteliklerinin yanı sıra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerelleştiricilerin daha fazla bağlam sağlamak için kullanılabilen ortak kullanıcı arabirimi kategorilerinin (<xref:System.Windows.LocalizationCategory>) bir listesini sağlar. Platform denetimleri için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] varsayılan kategoriler de geçersiz kılınabilir: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Sağlayan varsayılan yerelleştirme öznitelikleri de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod aracılığıyla geçersiz kılınabilir, bu sayede özel denetimlerin doğru varsayılan değerlerini doğru şekilde ayarlayabilirsiniz. Örneğin:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayarlanan örnek başına öznitelikler, özel denetimlerde kodda ayarlanan değerlere göre önceliğe sahip olur. Öznitelikler ve açıklamalar hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).

**Yazı tipi geri dönüş ve bileşik yazı tipleri**

Verilen bir kod noktası aralığını desteklemeyen bir yazı tipi belirtirseniz, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otomatik olarak Windows\Fonts dizininizde bulunan genel kullanıcı arabirimi. compositefont kullanılarak bunu otomatik olarak geri yüklenir. Bileşik yazı tipleri tıpkı diğer yazı tiplerinde olduğu gibi çalışır ve bir öğe `FontFamily` (örneğin, `FontFamily="Global User Interface"`) ayarlanarak açıkça kullanılabilir. Kendi bileşik yazı tipi oluşturarak ve belirli kod noktası aralıkları ve dilleri için kullanılacak yazı tipini belirterek kendi yazı tipi geri dönüş tercihinizi belirtebilirsiniz.

Bileşik yazı tipleri hakkında daha fazla bilgi <xref:System.Windows.Media.FontFamily>için bkz.

**Microsoft giriş sayfasını yerelleştirme**

Bu uygulamayı yerelleştirmek için Run Iletişim kutusuyla aynı adımları izleyebilirsiniz. Arapça için yerelleştirilmiş. csv dosyası, [Genelleştirme giriş sayfası örneğinde](https://go.microsoft.com/fwlink/?LinkID=159990)sizin için kullanılabilir.
