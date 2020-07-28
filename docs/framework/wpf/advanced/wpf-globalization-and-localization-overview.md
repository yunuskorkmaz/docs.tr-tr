---
title: Genelleştirme ve yerelleştirme genel bakış
description: Otomatik düzen, uydu derlemeleri ve yerelleştirilmiş öznitelikler de dahil olmak üzere Windows Presentation Foundation için yerelleştirme ve Genelleştirme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 9a54ce2c265b989f99383ff9cdec961c80dd655c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168290"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış

Ürününüzün kullanılabilirliğini yalnızca bir dille sınırlandırdığınızda, olası müşteri tabanınızı dünyanın 7.500.000.000 popülasyonızın bir bölümü ile sınırlandırdığınızda. Uygulamalarınızın küresel bir hedef kitleye ulaşmasını istiyorsanız, ürününüzün düşük maliyetli yerelleştirilmesi, daha fazla müşteriye ulaşmak için en iyi ve en ekonomik yolların biridir.

Bu genel bakışta ' de Genelleştirme ve yerelleştirme tanıtılmıştır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Genelleştirme, birden çok konumda gerçekleştiren uygulamaların tasarımını ve geliştirilmesini geliştirmektedir. Örneğin, Genelleştirme farklı kültürler içindeki kullanıcılar için yerelleştirilmiş kullanıcı arabirimlerini ve bölgesel verileri destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]otomatik düzen, uydu derlemeleri ve yerelleştirilmiş öznitelikler ve açıklama ekleme dahil olmak üzere Genelleştirilmiş tasarım özellikleri sağlar.

Yerelleştirme, uygulama kaynaklarının, uygulamanın desteklediği belirli kültürler için yerelleştirilmiş sürümlere çevirmesidir. ' De yerelleştirmeniz durumunda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ad alanındaki API 'leri kullanırsınız <xref:System.Windows.Markup.Localizer> . Bu API 'Ler [LocBaml aracı örnek](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml) komut satırı aracını güçlendirin. LocBaml oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF 'de Genelleştirme ve yerelleştirme için en iyi uygulamalar

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Bu bölümün sağladığı Kullanıcı arabirimi tasarımını ve Yerelleştirmede ilgili ipuçlarını izleyerek, yerleşik olarak bulunan Genelleştirme ve yerelleştirme işlevlerinden en iyi şekilde birini yapabilirsiniz.

### <a name="best-practices-for-wpf-ui-design"></a>WPF Kullanıcı arabirimi tasarımı için en iyi yöntemler

Tabanlı bir tasarladığınızda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- Yazın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; kodda oluşturmaktan kaçının [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ' Yi kullanarak oluşturduğunuzda, yerleşik yerelleştirme API 'leri aracılığıyla bunu kullanıma sunun.

- İçeriği düzenlemek için mutlak konumları ve sabit boyutları kullanmaktan kaçının; Bunun yerine, göreli veya otomatik boyutlandırma kullanın.

  - Kullanın <xref:System.Windows.Window.SizeToContent%2A> ve genişlikleri ve yükseklikleri olarak ayarlayın `Auto` .

  - <xref:System.Windows.Controls.Canvas>Öğeleri düzenlemek için kullanmaktan kaçının [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

  - <xref:System.Windows.Controls.Grid>Ve boyutunu paylaşma özelliğini kullanın.

- Yerelleştirilmiş metin genellikle daha fazla alan gerektirdiğinden kenar boşluklarında ek alan sağlayın. Fazladan boşluk, olası asılı karakterler için izin verir.

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> <xref:System.Windows.Controls.TextBlock> Kırpması önlemek için ' i etkinleştirin.

- Özniteliğini ayarlayın `xml:lang` . Bu öznitelik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu özelliğin değeri, içindeki çeşitli özelliklerin davranışını değiştirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Örneğin, heceleme, yazım denetimi, sayı değiştirme, karmaşık betik şekillendirme ve yazı tipi geri dönüş davranışını değiştirir. [Xaml 'de XML: lang işlemeyi](../../../desktop-wpf/xaml-services/xml-language-handling.md)ayarlama hakkında daha fazla bilgi için bkz. [WPF için Genelleştirme](globalization-for-wpf.md) .

- Farklı diller için kullanılan yazı tiplerinin daha iyi denetimini elde etmek için özelleştirilmiş bir bileşik yazı tipi oluşturun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\Fonts dizininizde GlobalUserInterface. Composite yazı tipini kullanır.

- Sağdan sola biçimli bir biçimde metin sunan bir kültür içinde yerelleştirilebilecek Gezinti uygulamaları oluşturduğunuzda, <xref:System.Windows.FlowDirection> sayfanın öğesinden devralmasını sağlamak için her sayfanın açık olarak ayarlayın <xref:System.Windows.FlowDirection> <xref:System.Windows.Navigation.NavigationWindow> .

- Bir tarayıcı dışında barındırılan tek başına Gezinti uygulamaları oluşturduğunuzda, <xref:System.Windows.Application.StartupUri%2A> ilk uygulamanız için öğesini bir sayfa yerine bir olarak ayarlayın <xref:System.Windows.Navigation.NavigationWindow> (örneğin, `<Application StartupUri="NavigationWindow.xaml">` ). Bu tasarım, <xref:System.Windows.FlowDirection> pencereyi ve gezinti çubuğunu değiştirmenize olanak sağlar. Daha fazla bilgi ve örnek için bkz. [Genelleştirme giriş sayfası örneği](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

### <a name="best-practices-for-wpf-localization"></a>WPF yerelleştirme için en iyi uygulamalar

Tabanlı uygulamaları yerelleştirediğinizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , bu en iyi yöntemleri uygulamayı göz önünde bulundurun:

- Yerelleştiriciler için ek bağlam sağlamak üzere yerelleştirme açıklamalarını kullanın.

- Öğelerin özelliklerini seçmeli olarak atlama yerine yerelleştirmeyi denetlemek için yerelleştirme özniteliklerini kullanın <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> . Daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md) .

- `msbuild -t:updateuid` `-t:checkuid` İçindeki özellikleri eklemek ve denetlemek için ve kullanın <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Geliştirme ve yerelleştirme arasındaki değişiklikleri izlemek için özellikleri kullanın. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Özellikler yeni geliştirme değişikliklerini yerelleştirmenize yardımcı olur. ' A el ile <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikler eklerseniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , görev genellikle sıkıcı ve daha az doğru olur.

  - Yerelleştirmeye başladıktan sonra özellikleri düzenlemeyin veya değiştirmeyin <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> .

  - Yinelenen <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikler kullanmayın (Kopyala ve Yapıştır komutunu kullandığınızda bu ipucunu unutmayın).

  - `UltimateResourceFallback`AssemblyInfo içindeki konumu, \* geri dönüş için uygun dili belirtmek için ayarlayın (örneğin, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]` ).

    Proje dosyanızdaki etiketi atlayarak kaynak dilinizi ana derlemeye eklemeye karar verirseniz `<UICulture>` , `UltimateResourceFallback` konumu uydu yerine ana derleme olarak ayarlayın (örneğin, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]` ).

## <a name="localize-a-wpf-application"></a>Bir WPF uygulamasını yerelleştirin

Bir uygulamayı yerelleştirmek istediğinizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , birkaç seçeneğiniz vardır. Örneğin, uygulamanızdaki yerelleştirilebilir kaynakları bir XML dosyasına bağlayabilir, yerelleştirilebilir metni resx tablolarında saklayabilir veya yerelleştirici kullanım dosyalarınıza sahip olabilirsiniz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Bu bölüm, çeşitli avantajlar sağlayan XAML 'in BAML formunu kullanan bir yerelleştirme iş akışını açıklar:

- Derlemeden sonra yerelleştirebilirsiniz.

- ' Nin yeni bir sürümünü kullanarak, oluşturduğunuz aynı zamanda yerelleştirebilmeniz için, XAML 'in BAML formunun daha eski bir sürümünden yerelleştirmeler içeren daha yeni bir sürüme güncelleştirebilirsiniz.

- XAML 'in BAML formu derlenmiş biçimde olduğundan, derleme zamanında orijinal kaynak öğelerini ve semantiğini doğrulayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

### <a name="localization-build-process"></a>Yerelleştirme derleme Işlemi

Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama geliştirirken, yerelleştirme için derleme işlemi aşağıdaki gibidir:

- Geliştirici uygulamayı oluşturur ve genelleştirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Geliştirici, `<UICulture>en-US</UICulture>` uygulamanın derlenmesi durumunda, dilden bağımsız bir ana derlemenin oluşturulduğu proje dosyasında ayarlanır. Bu derleme, tüm yerelleştirilebilir kaynakları içeren bir uydu .resources.dll dosyasına sahiptir. İsteğe bağlı olarak, yerelleştirme API 'lerimiz ana derlemeden ayıklamayı destekledikleri için kaynak dilini ana derlemede tutabilirsiniz.

- Dosya, yapıya derlendiğinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] xaml 'ın BAML biçimine dönüştürülür. Bağımsız olarak nötr ve önemli `MyDialog.exe` (İngilizce) `MyDialog.resources.dll` dosyalar İngilizce konuşuyor müşterisi tarafından yayımlanır.

### <a name="localization-workflow"></a>Yerelleştirme Iş akışı

Yerelleştirilmemiş dosya derlendikten sonra yerelleştirme işlemi başlar `MyDialog.resources.dll` . [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Orijinalinizdeki öğeler ve özellikler, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] altındaki API 'LERI kullanarak XAML 'in BAML formundan anahtar-değer çiftlerine ayıklanır <xref:System.Windows.Markup.Localizer> . Yerelleştiriciler, uygulamayı yerelleştirmek için anahtar-değer çiftlerini kullanır. Yerelleştirme tamamlandıktan sonra yeni değerlerden yeni bir .resource.dll oluşturabilirsiniz.

Anahtar-değer çiftlerinin anahtarları, `x:Uid` başlangıçtaki geliştirici tarafından verilen değerlerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Bu `x:Uid` değerler, API 'nin, yerelleştirme sırasında geliştirici ve yorumdur arasında gerçekleşen değişiklikleri izleyip birleştirmesini sağlar. Örneğin, geliştiriciler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yerelleştirici yerelleştirmeye başladıktan sonra değişiklik yaptığı takdirde, en az sayıda çeviri işinin kaybedilmesi için geliştirme değişikliğini zaten tamamlanmış yerelleştirme ile birleştirebilirsiniz.

Aşağıdaki grafik, XAML 'in BAML formunu temel alan tipik bir yerelleştirme iş akışını gösterir. Bu diyagramda geliştirici uygulamayı Ingilizce yazar. Geliştirici WPF uygulamasını oluşturur ve genelleştirir. Geliştirme proje dosyasında, `<UICulture>en-US</UICulture>` derleme için bir dil nötr ana derleme, tüm yerelleştirilebilir kaynakları içeren bir uydu .resources.dll oluşturulur. Alternatif olarak, WPF yerelleştirme API 'Leri ana derlemeden ayıklamayı desteklediği için, biri ana derlemede kaynak dilini tutabilir. Oluşturma işleminden sonra XAML, BAML 'de derlenir. Bağımsız olarak nötr MyDialog.exe.resources.dll, Ingilizce konuşan müşterilere gönderilir.

![Yerelleştirme iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Yerelleştirilmiş olmayan iş akışını gösteren diyagram.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>WPF yerelleştirme örnekleri

Bu bölüm, uygulamaları nasıl derleyip yerelleştirebileceğinizi anlamanıza yardımcı olacak yerelleştirilmiş uygulamaların örneklerini içerir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

### <a name="run-dialog-box-example"></a>Çalıştır Iletişim kutusu örneği

Aşağıdaki grafiklerde, **Çalıştır** iletişim kutusu örneğinin çıkışı gösterilmektedir.

**İngilizce:**

![Ingilizce Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Almanca:**

![Alman Çalıştır iletişim kutusunu gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Genel çalıştırma Iletişim kutusu tasarlama**

Bu örnek, ve kullanarak bir **Çalıştır** iletişim kutusu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Bu iletişim kutusu, Microsoft Windows Başlat menüsünden kullanılabilen **Çalıştır** iletişim kutusu ile eşdeğerdir.

Genel iletişim kutuları oluşturmak için bazı önemli noktalar şunlardır:

**Otomatik düzen**

*Window1. xaml içinde:*

`<Window SizeToContent="WidthAndHeight">`

Önceki pencere özelliği, pencereyi içeriğin boyutuna göre otomatik olarak yeniden boyutlandırır. Bu özellik, Windows 'un, yerelleştirme sonrasında boyut arttıkça artan içeriği almasını önler; Ayrıca içerik, yerelleştirme sonrasında boyutu azaldığında gereksiz alanı da kaldırır.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yerelleştirme API 'lerinin doğru çalışması için özellikler gereklidir.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Geliştirme ve yerelleştirme arasındaki değişiklikleri izlemek için yerelleştirme API 'leri tarafından kullanılır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Özellikleri, daha eski bir yerelleştirmesiyle uygulamasının daha yeni bir sürümünü birleştirmenizi sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Komut kabuğu 'nda çalıştırarak bir özellik eklersiniz `msbuild -t:updateuid RunDialog.csproj` . Bu, özelliklerin eklenmesi için önerilen yöntemdir, <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> çünkü bunları el ile eklemek genellikle zaman alabilir ve daha az doğru olur. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Özellikleri çalışırken doğru şekilde ayarlandığını kontrol edebilirsiniz `msbuild -t:checkuid RunDialog.csproj` .

, ' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Grid> De otomatik düzenden yararlanmak için faydalı bir denetim olan denetim kullanılarak yapılandırılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . İletişim kutusunun üç satıra ve beş sütuna bölündüğüne unutmayın. Satır ve sütun tanımlarından biri sabit boyuta sahip değil; Bu nedenle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her hücrede konumlandırılmış öğeler, yerelleştirme sırasında boyut artışına ve düşüşe uyum sağlayabilir.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

**Open:** Label ve yerleştirildiği ilk iki sütun <xref:System.Windows.Controls.ComboBox> Toplam genişliğin yüzde 10 ' unu kullanır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Örneğin, öğesinin paylaşılan boyutlandırma özelliğini kullandığını unutmayın <xref:System.Windows.Controls.Grid> . Son üç sütun, kendisini aynı yerleştirerek bu özelliklerden yararlanır <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> . Özelliğin adından beklendiğinden, bu sütunların aynı boyutta paylaşmasına izin verir. Yani "Gözatılacak..." "Durchsuchen..." daha uzun dizeye yerelleştirilir ve küçük bir "Tamam" düğmesine ve orantısız bir büyük "Durchsuchen..." olması yerine tüm düğmelerin genişliği artar. Bu.

**XML: lang**

`xml:lang="en-US"`

[Xaml 'de XML: lang işleme](../../../desktop-wpf/xaml-services/xml-language-handling.md) öğesinin kök öğesine yerleştirilmiş olduğunu fark edin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bu özellik, belirli bir öğenin ve alt öğelerinin kültürünü açıklar. Bu değer, içindeki çeşitli özellikler tarafından kullanılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve yerelleştirme sırasında uygun şekilde değiştirilmelidir. Bu değer, heceleme ve yazım denetimi kelimeleri için kullanılacak dil sözlüğünü değiştirir. Ayrıca, basamakların görüntülenmesini ve yazı tipi geri dönüş sisteminin hangi yazı tipinin kullanılacağını nasıl seçeceğine de etkileri vardır. Son olarak, özellik sayıların görüntülenme şeklini etkiler ve karmaşık betiklerdeki metinlerin yazıldığı şekilde şekillendirilir. Varsayılan değer "en-US" dir.

**Uydu kaynak derlemesi oluşturma**

*. Csproj içinde:*

Dosyayı düzenleyin `.csproj` ve aşağıdaki etiketi koşulsuz bir dosyaya ekleyin `<PropertyGroup>` :

`<UICulture>en-US</UICulture>`

Bir değer eklenmesine dikkat edin `UICulture` . Bu, <xref:System.Globalization.CultureInfo> en-US gibi geçerli bir değere ayarlandığında, projenin oluşturulması içindeki tüm yerelleştirilebilir kaynaklarla bir uydu derlemesi oluşturacaktır.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

`RunIcon.JPG`Tüm kültürler için aynı görünmesi gerektiğinden, yerelleştirilmesi gerekmez. `Localizable`, `false` uydu derlemesi yerine dilden bağımsız ana derlemede kalacak şekilde olarak ayarlanır. Tüm noncompilable kaynaklarının varsayılan değeri `Localizable` olarak ayarlanır `true` .

**Çalıştır Iletişim kutusunu yerelleştirme**

**Parse**

Uygulamayı oluşturduktan sonra, yerelleştirmedeki ilk adım, yardımcı derlemeden yerelleştirilebilir kaynakların ayrıştırılmasından oluşur. Bu konunun amaçları doğrultusunda, [LocBaml araç örneğinde](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)bulunan örnek LocBaml aracını kullanın. LocBaml 'in yalnızca yerelleştirme sürecinizi karşılayan bir yerelleştirme aracı oluşturmaya başlamanıza yardımcı olacak bir örnek araç olduğunu unutmayın. LocBaml kullanarak, bir "RunDialog.resources.dll.CSV" dosyası oluşturmak için: **LocBaml/parse RunDialog.resources.dll/Out:** öğesini ayrıştırmak için aşağıdakileri çalıştırın.

**Başlat**

Bu dosyayı düzenlemek için Unicode 'U destekleyen en sevdiğiniz CSV düzenleyicisini kullanın. Yerelleştirme kategorisi "none" olan tüm girişleri filtreleyin. Aşağıdaki girişleri görmeniz gerekir:

|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Düğme|Tamam|
|Button_2: System. Windows. Controls. Button. $Content|Düğme|İptal|
|Button_3: System. Windows. Controls. Button. $Content|Düğme|Göz at...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Metin|Bir program, klasör, belge veya İnternet kaynağının adını girdiğinizde Windows tarafından açılır.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Metin|Aç:|
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

**Oluştur**

Yerelleştirmenin son adımı, yeni yerelleştirilmiş uydu derlemesini oluşturmayı içerir. Bu, aşağıdaki LocBaml komutuyla gerçekleştirilebilir:

**LocBaml.exe/Generate RunDialog.resources.dll/trans:RunDialog.resources.dll.CSV/Out:. /Cul: de-DE**

Almanya penceresinde, bu resources.dll ana derlemenin yanındaki bir de klasörüne yerleştirilirse, bu kaynak en-US klasörü yerine otomatik olarak yüklenir. Bunu test etmek için Windows 'un Almanca sürümüne sahip değilseniz, kültürü kullandığınız Windows kültürüne (örneğin, `en-US` ) ayarlayın ve özgün kaynaklar dll 'sini değiştirin.

**Uydu kaynak yüklemesi**

|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kod|Orijinal Ingilizce BAML|Yerelleştirilmiş BAML|
|Genel olarak nötr kaynaklar|Ingilizce 'deki diğer kaynaklar|Almanca 'ya yerelleştirilmiş diğer kaynaklar|

.NET otomatik olarak uygulamanın hangi uydu kaynakları derlemesinin yükleneceğini seçer <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> . Bu, varsayılan olarak Windows işletim sisteminin kültürüne göre yapılır. Almanca Windows kullanıyorsanız, *de-DE\MyDialog.resources.dll* dosyası yüklenir. Ingilizce Windows kullanıyorsanız, *en-US\MyDialog.resources.dll* dosyası yüklenir. `NeutralResourcesLanguage`Projenizin *AssemblyInfo* dosyasında özniteliğini belirterek uygulamanız için en son geri dönüş kaynağını ayarlayabilirsiniz. Örneğin, şunu belirtirseniz:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

*en-US\MyDialog.resources.dll* dosyası, aşağıdaki dosyaların hiçbiri kullanılabilir değilse Almanca Windows ile kullanılır: *de-DE\MyDialog.resources.dll* veya *de\MyDialog.resources.dll*.

### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Suudi Arabistan giriş sayfası

Aşağıdaki grafiklerde Ingilizce ve Arapça bir giriş sayfası gösterilmektedir. Bu grafikleri üreten tüm örnek için bkz. [Genelleştirme giriş sayfası örneği](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

**İngilizce:**

![Ingilizce giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arapça:**

![Arapça giriş sayfasını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Küresel Microsoft ana sayfası tasarlama

Microsoft Suudi Arabistan Web sitesinin bu şekilde sahte olması, RightToLeft dilleri için sunulan Genelleştirme özelliklerini gösterir. Ibranice ve Arapça gibi dillerin sağdan sola okuma düzeni vardır. bu nedenle, Düzen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle İngilizce gibi soldan sağa dillerde olacak şekilde oldukça farklı bir şekilde düzenlenmelidir. Soldan sağa bir dilden sağdan sola bir dile veya tam tersi bir şekilde yerelleştirilmesi oldukça zor olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu tür yerelleştirmeleri çok daha kolay hale getirmek için tasarlanmıştır.

**FlowDirection**

*Giriş sayfası. xaml:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Özelliği üzerinde olduğuna dikkat edin <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Controls.Page> . Bu özelliğin olarak değiştirilmesi, <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Controls.Page> ve alt öğelerinin, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Arapça bir kullanıcı tarafından beklenecek şekilde, bu öğenin düzeninin sağdan sola dönüşecek şekilde değiştirilmesini sağlayacak şekilde değişecek. Herhangi bir öğe üzerinde açık bir şekilde belirterek devralma davranışını geçersiz kılabilir <xref:System.Windows.FrameworkElement.FlowDirection%2A> . <xref:System.Windows.FrameworkElement.FlowDirection%2A>Özelliği herhangi bir <xref:System.Windows.FrameworkElement> veya belge ile ilgili herhangi bir öğede kullanılabilir ve örtülü bir değeri vardır <xref:System.Windows.FlowDirection.LeftToRight> .

Kök değiştirildiğinde arka plan gradyanı fırçalarının doğru şekilde çevrildiğini de gözlemleyin <xref:System.Windows.FrameworkElement.FlowDirection%2A> :

**FlowDirection = "Solttoright"**

![Soldan sağa gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection = "RightToLeft"**

![Sağdan sola gradyan akışını gösteren ekran görüntüsü.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Paneller ve denetimler için sabit boyutlar kullanmaktan kaçının**

Giriş sayfası. xaml ' ye göz atın, en üstte yer alan sabit genişlik ve yüksekliğin yanı sıra [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel> , başka bir sabit boyut olmadığına dikkat edin. Kaynak metinden daha uzun olabilecek Yerelleştirilmiş metnin kırpılmasını önlemek için sabit boyutlar kullanmaktan kaçının. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Panolar ve denetimler, içerdikleri içeriğe göre otomatik olarak yeniden boyutlandırılır. Çoğu denetim Ayrıca daha fazla denetim için ayarlayabileceğiniz en düşük ve en büyük boyutlara sahiptir (örneğin, MinWidth = "20"). İle <xref:System.Windows.Controls.Grid> , ' ' kullanarak göreli genişlikleri ve yükseklikleri de ayarlayabilirsiniz \* (örneğin, `Width="0.25*"` ) veya hücre boyutu paylaşım özelliğini kullanabilirsiniz.

**Yerelleştirme açıklamaları**

İçeriğin belirsiz ve çevrilme zor olabileceği birçok durum vardır. Geliştirici veya tasarımcı, yerelleştirme açıklamaları aracılığıyla Yereller için ek bağlam ve açıklamalar sağlama olanağına sahiptir. Örneğin, yerelleştirme. aşağıdaki açıklamalar ' &#124; ' karakterinin kullanımını açıklığa kavuşturulur.

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Bu yorum, TextBlock_1 içeriğiyle ve LocBaml aracı durumunda (bkz. [bir uygulamayı yerelleştirin](how-to-localize-an-application.md)) ilişkili hale gelir. Bu, output. csv dosyasındaki TextBlock_1 satırının 6 sütununda görülebilir:

|Kaynak anahtarı|Kategori|Ama|Düzenlenerek|Yorum|Değer|
|-|-|-|-|-|-|
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Metin|TRUE|TRUE|Bu karakter, dekoratif bir kural olarak kullanılır.|&#124;|

Açıklamalar, aşağıdaki sözdizimi kullanılarak herhangi bir öğenin içeriğine veya özelliğine yerleştirilebilir:

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Yerelleştirme öznitelikleri**

Genellikle geliştirici veya yerelleştirme Yöneticisi, Yerelleştiricilerin okuyup değiştirebilecekleri denetimi gerektirir. Örneğin, yerelleştiriciye şirketinizin adını ya da yasal bir şekilde çevirmesini istemeyebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yerelleştirme aracınızın öğeleri kilitlemek, gizlemek veya sıralamak için kullanabileceği bir öğenin içeriğinin veya özelliğinin okunabilirliğini, modifilebilirliği ve kategorisini ayarlamanıza olanak tanıyan öznitelikler sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Localization.Attributes%2A>. Bu örneğin amaçları doğrultusunda, LocBaml aracı yalnızca bu özniteliklerin değerlerini çıktı olarak verir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin hepsi bu öznitelikler için varsayılan değerlere sahiptir, ancak bunları geçersiz kılabilirsiniz. Örneğin, aşağıdaki örnek için varsayılan yerelleştirme özniteliklerini geçersiz kılar `TextBlock_1` ve içeriği yerellerde okunabilir ancak değiştirilemeyen olarak ayarlar.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Okunabilirlik ve modifibeceri özniteliklerinin yanı sıra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.LocalizationCategory> Yerelleştiricilerin daha fazla bağlam sağlamak için kullanılabilen ortak kullanıcı arabirimi kategorilerinin () bir listesini sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Platform denetimleri için varsayılan kategoriler de geçersiz kılınabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] :

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Sağlayan varsayılan yerelleştirme öznitelikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de kod aracılığıyla geçersiz kılınabilir, bu sayede özel denetimlerin doğru varsayılan değerlerini doğru şekilde ayarlayabilirsiniz. Örnek:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

İçinde ayarlanan örnek başına öznitelikler, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel denetimlerde kodda ayarlanan değerlere göre önceliğe sahip olur. Öznitelikler ve açıklamalar hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).

**Yazı tipi geri dönüş ve bileşik yazı tipleri**

Verilen bir kod noktası aralığını desteklemeyen bir yazı tipi belirtirseniz, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otomatik olarak Windows\Fonts dizininizde bulunan genel kullanıcı arabirimi. compositefont kullanılarak bunu otomatik olarak geri yüklenir. Bileşik yazı tipleri tıpkı diğer yazı tiplerinde olduğu gibi çalışır ve bir öğe `FontFamily` (örneğin,) ayarlanarak açıkça kullanılabilir `FontFamily="Global User Interface"` . Kendi bileşik yazı tipi oluşturarak ve belirli kod noktası aralıkları ve dilleri için kullanılacak yazı tipini belirterek kendi yazı tipi geri dönüş tercihinizi belirtebilirsiniz.

Bileşik yazı tipleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Media.FontFamily> ..

**Microsoft giriş sayfasını yerelleştirme**

Bu uygulamayı yerelleştirmek için Run Iletişim kutusuyla aynı adımları izleyebilirsiniz. Arapça için yerelleştirilmiş. csv dosyası, [Genelleştirme giriş sayfası örneğinde](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage)sizin için kullanılabilir.
