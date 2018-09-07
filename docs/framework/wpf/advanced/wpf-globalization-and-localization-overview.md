---
title: WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 54c5caaf3ade07f342e94ad0359f00c1418eace4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076995"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
Yalnızca bir dil için ürününüzün kullanılabilirlik sınırladığınızda, müşterilerimizin dünyanın 6.5 milyar popülasyonun bir kesir olarak temel potansiyel müşteri sınırlayın. Uygun maliyetli yerelleştirme ürününüzden uygulamalarınız küresel bir hedef kitlesine ulaşmak için isterseniz daha fazla müşteriye ulaşmak için en iyi ve en ekonomik yolu biridir.  
  
 Genelleştirme ve yerelleştirme, bu genel bakış sunar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Genelleştirme, birden fazla konumda gerçekleştirmek uygulamaların geliştirilmesini ve Tasarım ' dir. Örneğin, kullanıcılar farklı kültürler için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri Genelleştirme destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Otomatik Düzen, uydu derlemeleri ve yerelleştirilmiş öznitelikleri gibi ve yorum genelleştirilmiş tasarım özellikleri sağlar.
  
 Uygulama kaynaklarını çevirisi uygulamanın desteklediği özel kültürler için yerelleştirilmiş sürüm yerelleştirmesidir. Yerelleştirme zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], API'leri kullanmak <xref:System.Windows.Markup.Localizer> ad alanı. Bu API'leri güç [LocBaml aracı örneği](https://go.microsoft.com/fwlink/?LinkID=160016) komut satırı aracı. Derleme ve LocBaml kullanma hakkında daha fazla bilgi için bkz: [bir uygulamayı yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Genelleştirme ve yerelleştirme ' WPF'de için en iyi uygulamalar  
 Yerleşik olan en iyi Genelleştirme ve yerelleştirme işlevselliğinin yapabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu bölümde, yerelleştirme ile ilgili ipuçları ve kullanıcı Arabirimi tasarımı izleyerek.  
  
### <a name="best-practices-for-wpf-ui-design"></a>WPF kullanıcı Arabirimi tasarımı için en iyi uygulamalar  
 Tasarlarken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– temel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bu en iyi uygulamayı düşünün:  
  
-   Yazma, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; oluşturmaktan kaçının [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kod. Oluşturduğunuzda, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], yerleşik yerelleştirme API'leri kullanıma sunar.  
  
-   Mutlak Konumlar ve sabit boyutlar kullanarak içeriği teslim düzenlemek kaçının; Bunun yerine, göreli ya da otomatik boyutlandırma kullanın.
  
    -   Kullanım <xref:System.Windows.Window.SizeToContent%2A>; ve genişlik ve yükseklik ayarlayın tutmak `Auto`.  
  
    -   Kullanmaktan kaçının <xref:System.Windows.Controls.Canvas> düzenlenmesine izin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Kullanım <xref:System.Windows.Controls.Grid> ve onun boyutu Paylaşımı özelliği.  
  
-   Yerelleştirilmiş metin genellikle daha fazla alan gerektirdiğinden, kenar boşlukları ek alanı sağlar. Ek alan için olası overhanging karaktere izin verilir.  
  
-   Etkinleştirme <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> üzerinde <xref:System.Windows.Controls.TextBlock> kırpma önlemek için.
  
-   Ayarlama **XML: lang** özniteliği. Bu öznitelik, kültür, belirli bir öğeyi ve onun alt öğeleri açıklar. Bu özelliğin değeri çeşitli özellikleri davranışını değiştiren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Örneğin, heceleme, yazım denetimi, numarası değiştirme, karmaşık kod şekillendirme ve yazı tipi geri dönüş davranışını değiştirir. Bkz: [WPF için genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ayarı hakkında daha fazla bilgi için [XML: lang işleme XAML içinde](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Farklı diller için kullanılan yazı tipi daha iyi denetim elde etmek için özelleştirilmiş bir bileşik yazı oluşturun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\\Fonts dizininizdeki GlobalUserInterface.composite yazı kullanır.  
  
-   Yerelleştirilebilir Gezinti uygulamaları oluştururken bir kültürde sağdan sola biçiminde metin sunan, açıkça ayarlanmış <xref:System.Windows.FlowDirection> sayfa devralmaz emin olmak için her sayfanın <xref:System.Windows.FlowDirection> gelen <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Bir tarayıcı dışında barındırılan tek başına Gezinti uygulamaları oluşturduğunuzda <xref:System.Windows.Application.StartupUri%2A> ilk uygulamanız için bir <xref:System.Windows.Navigation.NavigationWindow> yerine bir sayfaya (örneğin, `<Application StartupUri="NavigationWindow.xaml">`). Bu tasarım değiştirmenize olanak tanır <xref:System.Windows.FlowDirection> penceresinin ve gezinti çubuğu. Daha fazla bilgi ve örnek için bkz. [Genelleştirme giriş sayfası örnek](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>WPF yerelleştirme için en iyi uygulamalar  
 Ne zaman yerelleştirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– tabanlı uygulamalar, bu en iyi yöntemleri uygulayarak göz önünde bulundurun:  
  
-   Yerelleştirme açıklamalarını çevirmenler için ek bağlam sağlamak için kullanın.  
  
-   Yerelleştirme öznitelikleri seçerek atlama yerine yerelleştirme denetlemek için kullanmak <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> öğelerde özellikleri. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) daha fazla bilgi için.  
  
-   Kullanım **msbuild /t:updateuid** ve **/t:checkuid** ekleyin ve denetlemek için <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Kullanım <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> geliştirme ve yerelleştirme değişiklikleri izlemek için özellikler. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikler yeni geliştirme değişiklikler yerelleştirmek yardımcı olur. El ile eklerseniz <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerine bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], genellikle sıkıcı ve daha az doğru görevdir.  
  
    -   Düzen değiştirmek veya <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> yerelleştirme başladıktan sonra Özellikler.  
  
    -   Yinelenen kullanmayın <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri (unutmayın bu ipucu, Kopyala ve Yapıştır komut kullandığınızda).  
  
    -   Ayarlama `UltimateResourceFallback` geri dönüş için uygun dili belirtmek için AssemblyInfo.* konuma (örneğin, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Gt;(yok) ana derlemede kaynak dilinizi eklemeye karar `<UICulture>` ayarlamak, etiketi proje dosyanızda `UltimateResourceFallback` ana derlemenin uydu yerine konuma (örneğin, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>Bir WPF uygulamasını yerelleştirme  
 Yerelleştirme ne zaman bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, çeşitli seçenekleriniz vardır. Örneğin, uygulamanızdaki yerelleştirilebilir kaynaklar adlarınıza bağlayabileceğiniz bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya, yerelleştirilebilir metin resx tablolarında depolayın veya kullanın, yerelleştiriciye sahip [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları. Bu bölüm, çeşitli avantajlar sağlayan XAML BAML formu kullanan bir Yerelleştirme iş akışını açıklar:  
  
-   Derledikten sonra yerelleştirebilirsiniz.  
  
-   Böylece geliştirdiğiniz aynı anda yerelleştirebilirsiniz BAML formu XAML'ın eski bir sürümden BAML formu XAMLwith yerelleştirmeler'ın daha yeni bir sürümüne güncelleştirebilirsiniz.  
  
-   XAML, BAML formu derlenmiş biçiminde olduğundan, özgün kaynak öğeleri ve anlamı derleme zamanında doğrulayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Yapı işlemi yerelleştirme  
 Geliştirirken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı yerelleştirme için yapı işlemini aşağıdaki gibidir:  
  
-   Geliştirici oluşturur ve globalizes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Projede Geliştirici ayarlar dosyası `<UICulture>en-US</UICulture>` uygulamanın ne zaman derlenir, böylece bir dilden ana derleme oluşturulur. Bu derleme bir uydu sahiptir. resources.dll dosyasını, tüm yerelleştirilebilir kaynakları içerir. İsteğe bağlı olarak, çünkü ana derlemede kaynak dili tutabilirsiniz bizim yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ana derleme ayıklama destekler.  
  
-   Yapıda dosyası derlendiğinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML BAML biçime dönüştürülür. Duyarlıymış nötr `MyDialog.exe` ve kültürel bağımlı (İngilizce) `MyDialog.resources.dll` dosyaları İngilizce konuşan müşteriye yayımlanmış.  
  
### <a name="localization-workflow"></a>Yerelleştirme iş akışı  
 Yerelleştirme işlemi yerelleştirilmemiş sonra başlar `MyDialog.resources.dll` dosyası oluşturulur. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğeleri ve orijinal özelliklerinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML anahtar-değer çiftlerine BAML formu kullanarak ayıklandığı [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] altında <xref:System.Windows.Markup.Localizer>. Uygulamayı yerelleştirmek için anahtar-değer çiftleri yerelleştiriciler kullanın. Yeni bir oluşturabilirsiniz. resource.dll yerelleştirme tamamlandıktan sonra yeni değerlerinin.  
  
 Anahtar-değer çiftleri anahtarlar `x:Uid` özgün geliştirici tarafından yerleştirilen değerleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bunlar `x:Uid` değerleri etkinleştir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] izlemek ve geliştirici arasında yerelleştiriciye yerelleştirme sırasında gerçekleşen değişiklikleri birleştirir. Örneğin, geliştirici değişirse [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yerelleştirme yerelleştiriciye başladıktan sonra en az bir çeviri iş böylece geliştirme değişiklik zaten tamamlanmış yerelleştirme çalışması ile birleştirebilirsiniz.  
  
 Aşağıdaki grafikte, XAML bir BAML formu temel alan bir yerelleştirme tipik iş akışı gösterilmektedir. Bu diyagram, geliştirici bir uygulama İngilizce olarak yazar. varsayar. Geliştirici oluşturur ve WPF uygulaması globalizes. Projede Geliştirici ayarlar dosyası `<UICulture>en-US</UICulture>` derleme üzerinde dil nötr ana derleme bir uydu ile oluşturulan. tüm yerelleştirilebilir kaynakları içeren resources.dll. Alternatif olarak, WPF yerelleştirme API ana derleme ayıklama desteklediğinden bir kaynak dili ana derlemede tutun. Derleme işleminden sonra XAML derlenmiş BAML. Duyarlıymış nötr MyDialog.exe.resources.dll İngilizce konuşan müşteriye sevk.  
  
 ![Yerelleştirme iş akışı](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![İş akışı yerelleştirilmemiş](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>WPF yerelleştirme örnekleri  
 Bu bölüm, yerelleştirilmiş uygulamalar oluşturup yerelleştirmek anlamanıza yardımcı olması için örnekleri içerir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
#### <a name="run-dialog-box-example"></a>Çalıştır iletişim kutusu örneği  
 Aşağıdaki grafik çıktısını Göster **çalıştırma** iletişim kutusu örnek.  
  
 **İngilizce:**  
  
 ![Çalıştır iletişim kutusu](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Almanca:**  
  
 ![Almanca Çalıştır iletişim kutusu](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Bir genel çalıştırma iletişim kutusu tasarlama**  
  
 Bu örnek üretir bir **çalıştırma** iletişim kutusunu kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bu iletişim kutusunu eşdeğerdir **çalıştırma** kullanılabilir iletişim kutusu [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Başlat menüsü.  
  
 Genel iletişim kutuları yapmak için bazı önemli noktalar şunlardır:  
  
 **Otomatik Düzen**  
  
 *Window1.XAML içinde:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Önceki pencere özelliği otomatik olarak içerik boyutuna göre boyutlandırır. Bu özellik, yerelleştirme sonra boyutunu artırır içeriğini kesmek penceresi engeller; içerik boyutu sonra yerelleştirme azalttığında gereksiz boşluk da kaldırır.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikler için sırayla gereklidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] düzgün çalışması için.  
  
 Tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] yerelleştirilmesi ve geliştirme değişiklikleri izlemek için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri etkinleştirmek, daha yeni bir sürümü birleştirmek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daha eski bir yerelleştirme ile [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Eklediğiniz bir <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> çalıştırarak özelliği **msbuild /t:updateuid RunDialog.csproj** komut kabuğu'nda. Ekleme önerilen yöntem budur <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri el ile ekleme, genellikle zaman alan ve daha az doğru olduğu için. Bunu kontrol edebiliriz <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikler doğru ayarlandığını çalıştırarak **msbuild /t:checkuid RunDialog.csproj**.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Kullanarak yapılandırılmış <xref:System.Windows.Controls.Grid> otomatik düzen yararlanarak için faydalı bir denetim denetimi içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. İletişim kutusunda üç satır ve beş sütunlar halinde bölme unutmayın. Satır ve sütun tanımları birinin değil, sabit bir boyutu vardır; Bu nedenle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her hücreye konumlandırılmış öğeler bir artış uyum sağlamak ve yerelleştirme sırasında boyutunu azaltır.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 İlk iki sütun burada **açık:** etiket ve <xref:System.Windows.Controls.ComboBox> yerleştirilir yüzde 10 kullanmak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplam genişlik.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Paylaşılan boyutlandırma özelliği kullanır, örneğin Not <xref:System.Windows.Controls.Grid>. Son üç sütun bu kendileri aynı yerleştirerek yararlanmak <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Bu, bir özellik adından beklediğiniz gibi aynı boyutta paylaşmak sütunları sağlar. Bu nedenle uzun dize "Durchsuchen..." "Gözat..." yerelleştirileceği, tüm düğmeler küçük bir "Tamam" düğmesini ve orantısız büyük bir "Durchsuchen..." düğmesi yerine genişlik büyütün.  
  
 **XML: lang**  
  
 `Xml:lang="en-US"`  
  
 Bildirim [XML: lang işleme XAML içinde](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) kök öğe yerleştirilen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu özellik, kültür, belirli bir öğeyi ve alt öğeleri açıklar. Bu değer çeşitli özellikler tarafından kullanılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve yerelleştirme sırasında uygun şekilde değiştirilmelidir. Bu değer, hangi dil sözlüğü heceleme ve yazım denetimi sözcükler kullanın değiştirir. Ayrıca, rakam ve yazı tipi geri dönüş sistemi kullanılacak yazı tipini nasıl seçtiği görüntülenmesini etkiler. Son olarak, şekilde sayılar görüntülenir özelliğini etkiler ve karmaşık betiklerde yazılmış şekilde metinleri şeklinde. "En-US" varsayılan değerdir.  
  
 **Uydu kaynak derlemesi oluşturma**  
  
 *.Csproj içinde:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Ek fark bir `UICulture` değeri. Bu ayarlandığında geçerli bir <xref:System.Globalization.CultureInfo> değeri en-US, proje oluşturma gibi tüm yerelleştirilebilir kaynakları içeren bir uydu derleme içinde oluşturacağını.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Tüm kültürler için aynı görünmelidir çünkü yerelleştirilmiş gerekmez. `Localizable` ayarlanır `false` böylece dil nötr ana derlemenin uydu derlemesini yerine kalır. Varsayılan değer tüm noncompilable kaynakların `Localizable` kümesine `true`.  
  
 **Çalıştır iletişim yerelleştirme**  
  
 **Parse**  
  
 Uygulamayı oluşturduktan sonra ilk adımı, yerelleştirme yerelleştirilebilir kaynakları uydu derlemesinin dışında ayrıştırılıyor. Bu konunun amacı doğrultusunda, şurada bulunabilir örnek LocBaml aracı kullanma [LocBaml aracı örneği](https://go.microsoft.com/fwlink/?LinkID=160016). LocBaml yalnızca uygun bir yerelleştirme aracı yerelleştirme işleminizi oluşturmaya başlamanıza yardımcı olmak için gereken bir örnek araç olduğunu unutmayın. LocBaml, kullanarak ayrıştırmak için aşağıdakileri çalıştırın: **LocBaml/RunDialog.resources.dll ayrıştırma/out:** "RunDialog.resources.dll.CSV" dosyası oluşturmak için.  
  
 **Yerelleştirme**  
  
 Bu dosyayı düzenlemek için Unicode desteği tercih ettiğiniz CSV düzenleyiciyi kullanın. Yerelleştirme kategorisi "None" tüm girişlerle filtreleyin. Aşağıdaki girdiler görmeniz gerekir:  
  
|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Düğme|Tamam|  
|Button_2:System.Windows.Controls.Button.$Content|Düğme|İptal|  
|Button_3:System.Windows.Controls.Button.$Content|Düğme|Göz at...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Metin|Bir program, klasör, belge veya Internet kaynağının adını yazın ve Windows için açılır.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Metin|Açık:|  
|Window_1:System.Windows.Window.Title|Başlık|Çalıştır|  
  
 Almanca için uygulamayı yerelleştirme aşağıdaki çevirileri gerekir:  
  
|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Düğme|Tamam|  
|Button_2:System.Windows.Controls.Button.$Content|Düğme|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|Düğme|Durchsuchen...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Metin|Geben SIE bey Namen eines Programms, Ordners, Dokuments sıralanan einer Internetresource bir.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Metin|Öffnen:|  
|Window_1:System.Windows.Window.Title|Başlık|Çalıştır|  
  
 **Oluştur**  
  
 Yerelleştirme, son adım, yeni yerelleştirilmiş bir uydu derleme oluşturma içerir. Bu, aşağıdaki LocBaml komutu ile gerçekleştirilebilir:  
  
 **LocBaml.exe'yi / RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV Oluştur/out:. /CUL:de-Gizle**  
  
 Almanca üzerinde [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], bu resources.dll ana derleme yanında bir de-DE klasördeki yerleştirilmişse, bu kaynak en-US klasöründe yerine otomatik olarak yüklenecektir. Almanca sürümünü yoksa [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bunu test etmek için kültürü ne olursa olsun kültürü ayarlamanıza [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] (yani en-US) kullanıyorsanız ve özgün resources.dll değiştirin.  
  
 **Uydu kaynak yükleniyor**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kod|Orijinal İngilizce BAML|Yerelleştirilmiş BAML|  
|Kültürel olarak bağımsız kaynaklar|Diğer kaynakları, İngilizce|Almanca yerelleştirilmiş diğer kaynaklar|  
  
 .NET framework uygulamanın üzerinde tabanlı yüklemek için hangi uydu kaynak derleme otomatik olarak seçer `Thread.CurrentThread.CurrentUICulture`. Bu kültür için varsayılan olarak, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] işletim sistemi. Almanca kullanıyorsanız bunu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], de-DE\MyDialog.resources.dll yükler, İngilizce kullanıyorsanız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], en-US\MyDialog.resources.dll yükler. İçinde projenizin AssemblyInfo.* NeutralResourcesLanguage belirterek, uygulamanız için ultimate geri dönüş kaynak ayarlayabilirsiniz. Örneğin, belirtirseniz:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 de-DE\MyDialog.resources.dll veya de\MyDialog.resources.dll her ikisi de kullanılabilir olduğunda en-US\MyDialog.resources.dll Almanca Windows ile kullanılır.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Suudi Arabistan giriş sayfası  
 Aşağıdaki grafik, bir İngilizce ve Arapça giriş sayfası gösterir. Bu grafik üreten tam örnek için bkz [Genelleştirme giriş sayfası örnek](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **İngilizce:**  
  
 ![İngilizce sayfayı](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arapça:**  
  
 ![Arapça sayfa](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Genel bir Microsoft giriş tasarlama  
 Bu sahte ayarlama, Microsoft web sitesi RightToLeft diller için sağlanan Genelleştirme özellikleri gösterilmiştir Arabistan. İbranice ve Arapça gibi dillerde mevcuttur sağdan sola okuma düzeni kadar düzenini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle düzenlenmelidir İngilizce gibi sağdan sola diller olacaktır oldukça farklı. Sağdan sola dil ya da tam tersi bir soldan sağa dili yerelleştirme oldukça zor olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu tür yerelleştirmeler çok daha kolay hale getirmek için tasarlanmıştır.  
  
 **FlowDirection**  
  
 *Homepage.XAML:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Bildirim <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellikte <xref:System.Windows.Controls.Page>. Bu özellik için değiştirme <xref:System.Windows.FlowDirection.RightToLeft> değiştirecek <xref:System.Windows.FrameworkElement.FlowDirection%2A> , <xref:System.Windows.Controls.Page> ve onun alt öğeleri böylece bu düzenini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Arapça bir kullanıcı beklediğiniz gibi sağdan sola olmasını çevrilmiş. Bir geçersiz kılma kalıtım davranışını açık bir belirterek <xref:System.Windows.FrameworkElement.FlowDirection%2A> herhangi bir öğede. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Özelliği kullanılabilir herhangi <xref:System.Windows.FrameworkElement> veya belge ilgili öğe ve bir örtük değerini <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Bile arka plan gradyan Fırçalar doğru zaman çevrilmiş olduğunu gözlemek kök <xref:System.Windows.FrameworkElement.FlowDirection%2A> değiştirilir:  
  
 **FlowDirection="LeftToRight"**  
  
 ![Akış soldan sağa](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![Sağdan sola akış](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Sabit boyutlar paneller ve denetimler için kullanmaktan kaçının**  
  
 Homepage.xaml aracılığıyla göz atın, sabit genişlik ve yükseklik tüm belirtilen yanı sıra dikkat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] üst <xref:System.Windows.Controls.DockPanel>, herhangi bir sabit boyutu vardır. Kaynak metin uzun yerelleştirilmiş metin kırpmayı önlemek için sabit boyutlar kullanmaktan kaçının. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paneller ve denetimleri yeniden boyutlandırma içerdikleri içeriğine göre otomatik olarak ayarlanır. Çoğu denetimleri de daha fazla denetim için belirleyebileceğiniz minimum ve maksimum boyut (yani MinWidth = "20"). İle <xref:System.Windows.Controls.Grid>, kullanarak göreli genişlik ve yükseklik de ayarlayabilirsiniz ' *' (yani Width = "0,25\*") veya hücre boyutuna paylaşımı özelliğini kullanın.  
  
 **Yerelleştirme açıklamalarını**  
  
 Burada içerik belirsiz ve çevirme zor olabilir, birçok durumlar vardır. Geliştirici ve tasarımcı yerelleştiriciler yerelleştirme açıklamalarını aracılığıyla ek bağlam ve açıklama sağlamak için özelliğine sahiptir. Örneğin aşağıdaki Localization.Comments karakter kullanımını açıklar '&#124;'.  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Bu açıklamayı LocBaml aracı söz konusu olduğunda TextBlock_1'ın içeriği ile ilişkilendirilir (bkz [bir uygulamayı yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), çıkış .csv dosyasına TextBlock_1 satırın 6 sütunda görülebilir:  
  
|Kaynak anahtarı|Kategori|Okunabilir|Değiştirilebilir|Yorum|Değer|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Metin|TRUE|TRUE|Bu karakter dekoratif bir kural olarak kullanılır.|&#124;|  
  
 İçerik veya özelliği aşağıdaki sözdizimini kullanarak herhangi bir öğenin açıklamaları yerleştirilebilir:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Yerelleştirme öznitelikleri**  
  
 Genellikle geliştirici veya yerelleştirme Yöneticisi'ne yerelleştiriciler okuyun ve değiştirebileceği denetim gerekiyor. Örneğin, şirketinizin veya yasal ifadesi adı çevrilemedi yerelleştiriciye istemeyebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Okunabilirlik, Modifiability'e göre ve bir öğenin içerik ya da, yerelleştirme aracı kilitlemek, gizleme veya öğeleri sıralamak için kullanabileceğiniz özellik kategorisi ayarlamanıza olanak sağlayan öznitelikleri sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Localization.Attributes%2A>. LocBaml aracı, bu örnek amacı doğrultusunda, bu öznitelik değerleri, yalnızca çıkarır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Tüm bu öznitelikler için varsayılan değerleri denetiminiz olsa da, can geçersiz. Örneğin, aşağıdaki örnekte varsayılan Yerelleştirme öznitelikleri için geçersiz kılmaları `TextBlock_1` ve okunabilir olması için içeriği için yerelleştiriciler ancak değiştirilemeyen ayarlar.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Okunabilirlik ve Modifiability'e göre öznitelikleri ek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ortak kullanıcı Arabirimi kategorileri numaralandırmasını sağlar (<xref:System.Windows.LocalizationCategory>) daha fazla bağlam yerelleştiriciler vermek için kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Platformu denetimleri için varsayılan kategorileri kılınabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Varsayılan Yerelleştirme öznitelikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlar kodda, böylece doğru özel denetimler için doğru varsayılan değerleri ayarlayabilirsiniz ayrıca kılınabilir. Örneğin:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Örnek öznitelikleri kümesi başına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodda özel denetimler üzerinde ayarlanan değerlerle öncelikli. Öznitelikleri ve Yorumlar hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Yazı tipi geri dönüşü ve bileşik yazı tipleri**  
  
 Belirli bir kod noktası aralığı desteği olmayan bir yazı tipi belirtirseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\\Fonts dizininizde bulunan genel kullanıcı Interface.compositefont kullanarak yapan bir otomatik olarak geri dönüş olacaktır. Bileşik yazı tipleri yalnızca diğer yazı tipi çalışır ve bir öğenin FontFamily ayarlayarak açıkça kullanılabilir (yani FontFamily = "Genel kullanıcı arabirimi"). Bileşik yazı oluşturmaya ve belirli bir kod noktası aralığı ve diller için kullanılacak hangi yazı tipi belirterek kendi yazı tipi geri dönüş tercih belirtebilirsiniz.  
  
 Bileşik yazı tipleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Media.FontFamily>.  
  
 **Microsoft giriş yerelleştirme**  
  
 Bu uygulamayı yerelleştirmek için Çalıştır iletişim örnek ile aynı adımları izleyebilirsiniz. Arapça için yerelleştirilmiş bir .csv dosyası uygulamasında kullanılabilir [Genelleştirme giriş sayfası örnek](https://go.microsoft.com/fwlink/?LinkID=159990).
