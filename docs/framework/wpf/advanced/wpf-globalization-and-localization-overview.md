---
title: WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 957ba16886669acdfa5501ffe02501cbe6e57198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549623"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış
Yalnızca bir dil için ürününüzün kullanılabilirlik sınırladığınızda, potansiyel müşteri bizim dünyanın 6.5 milyar popülasyondaki kesir için temel sınırlayın. Düşük maliyetli yerelleştirme ürününüzün global çapta kullanıcılar ulaşması uygulamalarınızı istiyorsanız, daha fazla müşterilere ulaşmak için en iyi ve en ekonomik yollarından biridir.  
  
 Genelleştirme ve yerelleştirme, bu genel bakış sunar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Genelleştirme tasarım ve geliştirme birden fazla konumda gerçekleştirmek uygulamaların ' dir. Örneğin, farklı kültürler kullanıcılar için yerelleştirilmiş kullanıcı arabirimi ve bölgesel veri Genelleştirme destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Otomatik düzeni, uydu derlemelerini ve yerelleştirilmiş öznitelikleri gibi ve yorum globalized tasarım özellikleri de sağlar.
  
 Yerelleştirme uygulama kaynakları uygulamasının desteklediği spesifik kültürler için yerelleştirilmiş sürümleri içine çevrilmesidir. Yerelleştirme zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], API'leri kullanın <xref:System.Windows.Markup.Localizer> ad alanı. Bu API güç [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016) komut satırı aracı. Derleme ve LocBaml kullanma hakkında daha fazla bilgi için bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Genelleştirme ve yerelleştirme WPF'de için en iyi yöntemler  
 İçinde yerleşik en Genelleştirme ve yerelleştirme işlevleri yapabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] UI tasarım ve bu bölümde yerelleştirme ile ilgili ipuçları izleyerek.  
  
### <a name="best-practices-for-wpf-ui-design"></a>WPF kullanıcı Arabirimi tasarımı için en iyi yöntemler  
 Tasarlarken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– temel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bu en iyi yöntemleri uygulayın:  
  
-   Yazma, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; oluşturmamak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kod. Oluşturduğunuzda, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], yerleşik yerelleştirme API'leri kullanıma sunar.  
  
-   İçerik teslim alma düzenlemek için Mutlak Konumlar ve sabit boyutları kullanmaktan kaçının; Bunun yerine, göreli veya otomatik boyutlandırma kullanın.
  
    -   Kullanım <xref:System.Windows.Window.SizeToContent%2A>; genişlik ve yükseklik kümesine tutmanızı `Auto`.  
  
    -   Kullanmaktan kaçının <xref:System.Windows.Controls.Canvas> düzenlenmesine izin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Kullanım <xref:System.Windows.Controls.Grid> ve onun boyutu paylaşımı özellik.  
  
-   Yerelleştirilmiş metin genellikle daha fazla alan gerektirdiğinden kenar boşluklarını boşluk sağlar. Ek boşluk için olası overhanging karaktere izin verilir.  
  
-   Etkinleştirme <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> üzerinde <xref:System.Windows.Controls.TextBlock> kırpma önlemek için.
  
-   Ayarlama **XML: lang** özniteliği. Bu öznitelik, belirli bir öğeyi ve alt öğeleri kültürünü açıklar. Bu özelliğin değeri çeşitli özellikler davranışını değiştiren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Örneğin, heceleme ve yazım denetimi, numarası değiştirme, karmaşık komut dosyası şekillendirme ve yazı tipi geri dönüş davranışını değiştirir. Bkz: [WPF için genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ayarı hakkında daha fazla bilgi için [XML: lang XAML'de işleme](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Farklı diller için kullanılan yazı tipi daha iyi denetim elde etmek için özelleştirilmiş bir bileşik font oluşturun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\\Fonts dizininizde GlobalUserInterface.composite yazı tipini kullanır.  
  
-   Yerelleştirilebilir Gezinti uygulamaları oluştururken bir kültür sağdan sola biçiminde metin sunan, açık olarak ayarlanıp <xref:System.Windows.FlowDirection> sayfa devralmaz emin olmak için her sayfanın <xref:System.Windows.FlowDirection> gelen <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Bir tarayıcı dışında barındırılan tek başına Gezinti uygulamaları oluşturduğunuzda <xref:System.Windows.Application.StartupUri%2A> ilk uygulamanız için bir <xref:System.Windows.Navigation.NavigationWindow> yerine bir sayfaya (örneğin, `<Application StartupUri="NavigationWindow.xaml">`). Bu tasarım değiştirmenize olanak tanır <xref:System.Windows.FlowDirection> penceresinin ve gezinti çubuğu. Daha fazla bilgi ve bir örnek için bkz: [Genelleştirme giriş sayfası örnek](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>WPF yerelleştirme için en iyi yöntemler  
 Ne zaman yerelleştirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– tabanlı uygulamalar, bu en iyi yöntemleri uygulayarak göz önünde bulundurun:  
  
-   Yerelleştirme açıklamalarını fazladan bağlam için çevirmenler sağlamak için kullanın.  
  
-   Yerelleştirme öznitelikleri seçerek atlama yerine yerelleştirme denetlemek için kullandığı <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> öğelerde özellikleri. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) daha fazla bilgi için.  
  
-   Kullanım **msbuild /t:updateuid** ve **/t:checkuid** eklemek ve denetlemek için <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Kullanım <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> geliştirme ve yerelleştirme değişiklikleri izlemek için özellikler. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Özellikler yeni geliştirme değişiklikleri yerelleştirme yardımcı olur. El ile eklerseniz <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özelliklerine bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], genellikle yorucu ve daha az kesin bir görevdir.  
  
    -   Düzen değiştirmek veya <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> yerelleştirme başladıktan sonra özellikleri.  
  
    -   Yinelenen kullanmayın <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri (unutmayın bu ipucu kopyalama ve yapıştırma komutunu kullandığınızda).  
  
    -   Ayarlama `UltimateResourceFallback` geri dönüş için uygun dili belirtmek için AssemblyInfo.* konuma (örneğin, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Kaldırarak ana derlemede kaynak dilinizi eklemeye karar `<UICulture>` etiketi proje dosyanızda, Ayarla `UltimateResourceFallback` uydu yerine ana derlemeyle konum (örneğin, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>WPF uygulaması yerelleştirme  
 Ne zaman yerelleştirme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, birkaç seçenek vardır. Örneğin, uygulamanızdaki yerelleştirilebilir kaynakları bağlayabileceğiniz bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya, yerelleştirilebilir metni resx tablolarda depolamak veya kullanın, yerelleştiriciye sahip [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları. Bu bölümde birkaç avantaj sağlar XAML BAML formu kullanan bir yerelleştirme tanımlanmaktadır:  
  
-   Oluşturacağınız sonra yerelleştirebilirsiniz.  
  
-   Böylece, geliştirdiğiniz aynı anda yerelleştirebilirsiniz XAML BAML formunun eski bir sürümden XAMLwith yerelleştirmeler BAML biçiminde daha yeni bir sürüme güncelleştirebilirsiniz.  
  
-   XAML BAML form derlenmiş biçiminde olduğundan, özgün kaynak öğeleri ve semantiği derleme zamanında doğrulayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Yerelleştirme derleme işlemi  
 Geliştirirken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, yerelleştirme için yapılandırma işlemi aşağıdaki gibidir:  
  
-   Geliştirici oluşturur ve globalizes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Projede dosya Geliştirici kümeleri `<UICulture>en-US</UICulture>` uygulamanın ne zaman derlenmiş böylece dilden ana derleme oluşturulur. Bu derleme uydu sahip. tüm yerelleştirilebilir kaynaklarını içeren resources.dll dosyası. İsteğe bağlı olarak, çünkü ana derlemede kaynak dili tutabilirsiniz bizim yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ana derleme ayıklama destekler.  
  
-   Dosya yapıda derlendiğinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML BAML biçime dönüştürülür. Culturally nötr `MyDialog.exe` ve culturally bağımlı (İngilizce) `MyDialog.resources.dll` dosyaları İngilizce konuşan müşteriye yayımladı.  
  
### <a name="localization-workflow"></a>Yerelleştirme iş akışı  
 Yerelleştirme işlemi yerelleştirilmemiş sonra başlar `MyDialog.resources.dll` dosyası oluşturulur. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğeleri ve orijinal özelliklerinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anahtar-değer çiftleri XAML BAML forma kullanarak ayıklandığı [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] altında <xref:System.Windows.Markup.Localizer>. Çevirmenler anahtar-değer çiftleri uygulama yerelleştirme için kullanın. Yeni bir oluşturabilir. yerelleştirme tamamlandıktan sonra yeni değerlerinden resource.dll.  
  
 Anahtar-değer çiftleri anahtarlar `x:Uid` orijinal geliştirici tarafından yerleştirilen değerleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bunlar `x:Uid` değerleri etkinleştir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] izlemek ve geliştirici ve yerelleştiriciye arasında yerelleştirme sırasında gerçekleşen değişiklikleri birleştirir. Örneğin, geliştirici değişirse [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yerelleştirme yerelleştiriciye başladıktan sonra en az çeviri iş böylece zaten tamamlanmış Yerelleştirme iş geliştirme değişiklikle birleştirebilirsiniz.  
  
 Aşağıdaki grafikte XAML BAML formu temel alan bir tipik Yerelleştirme iş akışı gösterilmektedir. Bu diyagramda Geliştirici uygulama İngilizce Yazar varsayar. Geliştirici oluşturur ve WPF uygulaması globalizes. Projede dosya Geliştirici kümeleri `<UICulture>en-US</UICulture>` böylece derleme üzerinde bir dil belirsiz ana derleme uydu ile oluşturulan. tüm yerelleştirilebilir kaynakları içeren resources.dll. Alternatif olarak, WPF yerelleştirme API'lerini ana derleme ayıklama desteklemediğinden bir kaynak dili ana derlemede tutun. Derleme işleminden sonra XAML derlenmiş BAML. Culturally nötr MyDialog.exe.resources.dll İngilizce bilmeyen müşteriye sevk.  
  
 ![Yerelleştirme iş akışı](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![İş akışı yerelleştirilmemiş](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>WPF yerelleştirme örnekleri  
 Bu bölümde nasıl oluşturulacağı ve yerelleştirme anlamanıza yardımcı olması için yerelleştirilmiş uygulamaları örnekleri içeren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
#### <a name="run-dialog-box-example"></a>İletişim kutusu örneği çalıştırma  
 Aşağıdaki grafik çıktısını Göster **çalıştırmak** iletişim kutusu örnek.  
  
 **İngilizce:**  
  
 ![Çalıştır iletişim kutusu](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Almanca:**  
  
 ![Almanca Çalıştır iletişim kutusunu](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Bir genel çalıştırma iletişim kutusu tasarlama**  
  
 Bu örnek üreten bir **çalıştırmak** iletişim kutusunu kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bu iletişim kutusunu eşdeğerdir **çalıştırmak** kullanılabilir iletişim kutusu [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Başlat menüsü.  
  
 Genel iletişim kutusu sağlama bazı önemli şunlardır:  
  
 **Otomatik düzeni**  
  
 *Window1.XAML içinde:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Önceki pencere özelliği otomatik olarak içeriğinin boyutuna göre yeniden boyutlandırır. Bu özellik kesim boyutu sonra yerelleştirme artırır içerik kapalı penceresi engeller; içerik boyutu sonra yerelleştirme azaldıkça gereksiz alanı de kaldırır.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri gereken sırayla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] düzgün çalışması için.  
  
 Tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] yerelleştirilmesi ve geliştirme değişiklikleri izlemek için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri etkinleştirin, daha yeni bir sürümü birleştirmek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daha eski bir yerelleştirme ile [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Eklediğiniz bir <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> çalıştırarak özelliği **msbuild /t:updateuid RunDialog.csproj** komut kabuğunda. Bu, ekleme, önerilen yöntemdir <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri el ile eklemeden genellikle zaman alan ve daha az doğru olduğundan. Bu kontrol edebilirsiniz <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> özellikleri doğru ayarlandığını çalıştırarak **msbuild /t:checkuid RunDialog.csproj**.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Kullanarak yapılandırılmış <xref:System.Windows.Controls.Grid> otomatik düzen yararlanarak için yararlı bir denetimdir denetim içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. İletişim kutusu üç satır ve beş sütunlar halinde bölünür unutmayın. Satır ve sütun tanımları birini değil, sabit bir boyutu vardır; Bu nedenle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her hücre konumlandırılmış öğeler artışları uyum ve yerelleştirme sırasında boyutu azalır.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 İlk iki sütun nerede **açık:** etiket ve <xref:System.Windows.Controls.ComboBox> yerleştirilir yüzde 10'luk kullanmak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplam genişlik.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Paylaşılan boyutlandırma özelliğini kullanır, örneğin Not <xref:System.Windows.Controls.Grid>. Son üç sütun bu kendilerini aynı koyarak yararlanmak <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Bir özellik adından beklediğiniz gibi bu sütunların aynı boyutta paylaşmak sağlar. Böyle olduğunda "Gözat..." yerelleştirilmiş uzun dizeye "Durchsuchen..." küçük "Tamam" düğmesini ve bir orantısız büyük "Durchsuchen..." sahip olmak yerine genişliği tüm düğmeleri büyütün. düğme.  
  
 **XML: lang**  
  
 `Xml:lang="en-US"`  
  
 Bildirim [XML: lang XAML'de işleme](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) kök öğesinin yerleştirilen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu özellik belirli bir öğeyi ve alt öğelerini kültürünü açıklar. Bu değer çeşitli özellikleri tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve yerelleştirme sırasında uygun şekilde değiştirilmesi gerekir. Bu değer, hangi sözlükle heceleme ve onay sözcükleri yazım için kullandığı değişir. Ayrıca, rakamları ve yazı tipi geri dönüş sistemi kullanılacak yazı tipini nasıl seçtiği görünümünü etkiler. Son olarak, karmaşık komut dosyalarında yazılmış şekilde metinleri ve yol sayılar görüntülenir özelliği etkiler şeklinde. "En-US" varsayılan değerdir.  
  
 **Uydu kaynak derlemesi oluşturma**  
  
 *.Csproj içinde:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Eklenmesi fark bir `UICulture` değeri. Bu ayarlandığında geçerli bir <xref:System.Globalization.CultureInfo> değeri en-US, proje oluşturma gibi tüm yerelleştirilebilir kaynaklarla uydu derlemesi içinde üretir.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Tüm kültürler için aynı görüntülenmesi gerekir çünkü yerelleştirilmesi gerekmez. `Localizable` ayarlanmış `false` böylece dil belirsiz ana derleme uydu derlemesi yerine kalır. Varsayılan değer tüm noncompilable kaynakların `Localizable` kümesine `true`.  
  
 **Çalıştır iletişim yerelleştirme**  
  
 **Ayrıştırma**  
  
 Uygulamayı oluşturduktan sonra onu yerelleştirme ilk adımı uydu derlemesi dışında yerelleştirilebilir kaynakları ayrıştırmaya. Bu konuda amacıyla konumunda bulunan örnek LocBaml aracını kullanmak [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016). LocBaml yalnızca uygun bir yerelleştirme aracını yerelleştirme işlemine oluşturmaya başlamanıza yardımcı yönelik bir örnek araç olduğuna dikkat edin. LocBaml, kullanarak ayrıştırmak için aşağıdakini çalıştırın: **LocBaml/RunDialog.resources.dll ayrıştırma/out:** "RunDialog.resources.dll.CSV" dosyası oluşturmak için.  
  
 **Yerelleştirme**  
  
 Bu dosyayı düzenlemek için Unicode'u destekler, sık kullanılan CSV düzenleyicisi kullanın. Tüm girişleri "None" yerelleştirme kategorisiyle filtreler. Aşağıdaki girdiler görmeniz gerekir:  
  
|Kaynak anahtarı|Yerelleştirme kategorisi|Değer|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Düğme|Tamam|  
|Button_2:System.Windows.Controls.Button.$Content|Düğme|İptal|  
|Button_3:System.Windows.Controls.Button.$Content|Düğme|Gözat...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Metin|Program, klasör, belge veya Internet kaynağının adını yazın ve Windows sizin için açılır.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Metin|Aç:|  
|Window_1:System.Windows.Window.Title|Başlık|Çalıştır|  
  
 Almanca uygulamayı yerelleştirme aşağıdaki çevirileri gerektirir:  
  
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
  
 Yerelleştirme son adımı yeni yerelleştirilmiş uydu derlemesini oluşturursunuz. Bu aşağıdaki LocBaml komutuyla gerçekleştirilebilir:  
  
 **LocBaml.exe'yi / RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV Oluştur/out:. /CUL:de-Gizle**  
  
 Almanca üzerinde [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], bu resources.dll ana derleme yanında bir de-DE klasördeki girilirse, bu kaynak yerine en-US klasöründe bir otomatik olarak yükler. Almanca sürümünü yoksa [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bunu test etmek için kültürü için hangi kültürünü ayarlamak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] (örneğin en-US) kullanarak ve özgün resources.dll değiştirin.  
  
 **Uydu kaynak yükleme**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kod|Özgün İngilizce BAML|Yerelleştirilmiş BAML|  
|Culturally bağımsız kaynaklar|İngilizce diğer kaynaklar|Almanca için yerelleştirilmiş kaynaklar|  
  
 .NET framework uygulamanın üzerinde tabanlı yüklemek için hangi uydu kaynakları derlemesi otomatik olarak seçer `Thread.CurrentThread.CurrentUICulture`. Bu kültür için varsayılan olarak, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] işletim sistemi. Almanca kullanıyorsanız, bunu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], de-DE\MyDialog.resources.dll yükler, İngilizce kullanıyorsanız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], en-US\MyDialog.resources.dll yükler. Projenizin AssemblyInfo.* NeutralResourcesLanguage belirterek, uygulamanız için ultimate geri dönüş kaynak ayarlayabilirsiniz. Belirtirseniz, örneğin:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 de-DE\MyDialog.resources.dll veya de\MyDialog.resources.dll her ikisi de kullanılabilir olduğunda en-US\MyDialog.resources.dll Almanca Windows ile kullanılır.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Suudi Arabistan giriş sayfası  
 İngilizce ve Arapça giriş sayfası aşağıdaki grafik gösterir. Bu grafik üreten tam bir örnek için bkz: [Genelleştirme giriş sayfası örnek](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **İngilizce:**  
  
 ![İngilizce sayfa](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arapça:**  
  
 ![Arapça sayfa](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Genel Microsoft giriş sayfası tasarlama  
 Bu mock yukarı, Microsoft web sitesi RightToLeft diller için sağlanan Genelleştirme özellikleri gösterilmektedir Arabistan. İbranice ve Arapça gibi dilleri sahip bir sağdan sola okuma sırası böylece düzenini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle düzenlenmelidir İngilizce gibi soldan sağa dillerde olacaktır oldukça farklı. Soldan sağa dilden sağdan sola bir dil veya tersi yerelleştirme oldukça zor olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu tür yerelleştirmeler çok kolaylaştırmak için tasarlanmıştır.  
  
 **FlowDirection**  
  
 *Homepage.XAML:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Bildirim <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği <xref:System.Windows.Controls.Page>. Bu özelliğin değiştirilmesi <xref:System.Windows.FlowDirection.RightToLeft> değiştirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> , <xref:System.Windows.Controls.Page> ve alt öğelerini böylece bu düzenini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sağdan sola Arap kullanıcı beklediğiniz gibi olmasını çevrilebilir. Bir geçersiz kılabilirsiniz devralma davranışı açık bir belirterek <xref:System.Windows.FrameworkElement.FlowDirection%2A> herhangi bir öğe üzerinde. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Özelliği kullanılabilir herhangi <xref:System.Windows.FrameworkElement> veya belge ilgili öğe ve bir örtük değerine sahip <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Bile arka plan gradyan Fırçalar doğru olduğunda çevrilmiş olduğunu gözleyin kök <xref:System.Windows.FrameworkElement.FlowDirection%2A> değiştirilir:  
  
 **FlowDirection="LeftToRight"**  
  
 ![Akış soldan sağa](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![Sağdan sola akışından](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Pano ve denetimler için sabit boyut kullanmaktan kaçının**  
  
 Homepage.xaml üzerinden göz atın, sabit genişlik ve yükseklik tüm belirtilen yanı sıra dikkat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] üstte <xref:System.Windows.Controls.DockPanel>, herhangi bir sabit boyutu vardır. Kaynak metni uzun olabilir yerelleştirilmiş metin kırpma önlemek için sabit boyut kullanmaktan kaçının. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paneller ve denetimleri yeniden boyutlandırma içerdikleri içeriğine göre otomatik olarak ayarlanır. Çoğu denetimler de daha fazla denetim için ayarladığınız minimum ve maksimum boyut (yani değeri MinWidth = "20"). İle <xref:System.Windows.Controls.Grid>, kullanarak göreli genişlik ve yükseklik de ayarlayabilirsiniz ' *' (yani Width = "0,25\*") veya hücre boyutuna paylaşımı özelliğini kullanın.  
  
 **Yerelleştirme yorumları**  
  
 Çoğu durumda içerik belirsiz ve Çevir zor olduğu olabilir vardır. Geliştirici veya Tasarımcısı çevirmenler yerelleştirme açıklamalarını aracılığıyla ek bağlam ve açıklamalar sağlamak için özelliğine sahiptir. Örneğin Localization.Comments karakter kullanımını kavuşturuldu '&#124;'.  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Bu açıklama TextBlock_1'ın içeriği ve LocBaml aracı söz konusu olduğunda ilişkilendirilir (bkz [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), çıktı .csv dosyasında TextBlock_1 satır 6 sütununda görülebilir:  
  
|Kaynak anahtarı|Kategori|Okunabilir|Değiştirilebilir|Yorum|Değer|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Metin|TRUE|TRUE|Bu karakter dekoratif bir kural olarak kullanılır.|&#124;|  
  
 Açıklamalar, içerik ya da şu sözdizimini kullanarak öğesi özelliği yerleştirilebilir:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Yerelleştirme öznitelikleri**  
  
 Genellikle geliştirici veya yerelleştirme Yöneticisi'ne çevirmenler okuyun ve değiştirebileceği denetim gerekiyor. Örneğin, şirketiniz veya yasal ifadesi adını çevirmek için yerelleştiriciye istemeyebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Okunabilirlik, Modifiability'e göre ve kategoriyi bir öğenin içeriği veya yerelleştirme aracınızı kilitlemek Gizle veya öğeleri sıralamak için kullanabileceğiniz özelliği ayarlamanıza olanak tanır öznitelikleri sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Localization.Attributes%2A>. Bu örnek amaçları doğrultusunda, LocBaml aracını yalnızca bu öznitelik değerleri çıkarır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tüm denetimler bu öznitelikler için varsayılan değerlere sahip, ancak can kılmadığınız. Örneğin, aşağıdaki örnekte varsayılan Yerelleştirme öznitelikleri için geçersiz kılmaları `TextBlock_1` ve okunabilir olması için içeriği için çevirmenler ancak değiştirilemeyen ayarlar.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Okunabilirlik ve Modifiability'e göre öznitelikler, ek olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ortak UI kategorileri numaralandırması sağlar (<xref:System.Windows.LocalizationCategory>) daha fazla bağlam çevirmenler vermek için kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Platform denetimleri için varsayılan kategorileri geçersiz kılınmış içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Varsayılan Yerelleştirme öznitelikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlayan özel denetimler için doğru varsayılan değerleri düzgün ayarlanabilmesi için ayrıca kod üzerinden geçersiz kılınabilir. Örneğin:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Örnek öznitelikleri kümesinde başına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel denetimlerinde kodda ayarlanan değerlerle önceliğe sahip olur. Öznitelikler ve açıklamaları hakkında daha fazla bilgi için bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Yazı tipi geri dönüşü ve bileşik yazı tipleri**  
  
 Verilen codepoint aralığı desteklemeyen bir yazı tipi belirtirseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\\Fonts dizininde bulunan genel kullanıcı Interface.compositefont kullanarak yapan bir otomatik olarak geri dönüş olacaktır. Bileşik yazı tipleri yalnızca gibi diğer yazı tipi çalışır ve bir öğenin FontFamily ayarlayarak açıkça kullanılabilir (yani FontFamily = "Genel kullanıcı arabirimi"). Bileşik yazı oluşturma ve belirli codepoint aralıkları ve diller için kullanmak üzere hangi yazı tipinin belirterek kendi yazı tipi geri dönüş tercihinizi belirtin.  
  
 Bileşik yazı tipleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Media.FontFamily>.  
  
 **Microsoft giriş sayfası yerelleştirme**  
  
 Bu uygulama yerelleştirmeye Çalıştır iletişim örnekle aynı adımları izleyebilirsiniz. Arapça için yerelleştirilmiş .csv dosyası uygulamasında kullanılabilir [Genelleştirme giriş sayfası örnek](http://go.microsoft.com/fwlink/?LinkID=159990).
