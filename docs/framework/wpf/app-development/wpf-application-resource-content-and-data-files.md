---
title: Uygulama Kaynağı, İçerik ve Veri Dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186197"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
Microsoft Windows uygulamaları genellikle görüntü, video ve ses gibi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]yürütülemeyen veriler içeren dosyalara bağlıdır. Windows Sunu Temeli (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmak, tanımlamak ve kullanmak için özel destek sunar. Bu destek, şular da dahil olmak üzere belirli bir uygulama veri dosyası türü kümesi etrafında döner:  
  
- **Kaynak Dosyaları**: Yürütülebilir veya kitaplık WPF derlemesi içine derlenen veri dosyaları.  
  
- **İçerik Dosyaları**: Yürütülebilir bir WPF derlemesi ile açık bir ilişkisi olan bağımsız veri dosyaları.  
  
- **Site of Origin Files**: Yürütülebilir bir WPF derlemesi ile ilişkisi olmayan bağımsız veri dosyaları.  
  
 Bu üç dosya türü arasında önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının oluşturma zamanında bilinmesidir; bir derleme onlar hakkında açık bilgiye sahiptir. Ancak, kaynak dosyalarının site için, bir derleme nin bunlar hakkında hiçbir bilgisi olmayabilir veya bir paket tekdüzen kaynak tanımlayıcısı (URI) referansı aracılığıyla örtülü bilgi; ikincisi durumunda, kaynak dosyasının başvurulan site aslında var olduğunu garanti yoktur.  
  
 Uygulama veri dosyalarına başvurmak için, Windows Presentation Foundation (WPF), [WPF'deki Paket URI'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanan Paket üniformakaynak tanımlayıcısı (URI) Düzenini kullanır.  
  
 Bu konu, uygulama veri dosyalarının nasıl yapılandırılabildiğini ve kullanılacağını açıklar.  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>Kaynak Dosyalar  
 Bir uygulama veri dosyasının bir uygulama için her zaman kullanılabilir olması gerekiyorsa, kullanılabilirliği garanti etmenin tek yolu, dosyayı bir uygulamanın ana yürütülebilir derlemesine veya başvurulan derlemelerinden birine derlemektir. Bu tür bir uygulama veri dosyası *kaynak dosyası*olarak bilinir.  
  
 Kaynak dosyalarını şu anda kullanmalısınız:  
  
- Bir derlemeye derlendikten sonra kaynak dosyasının içeriğini güncelleştirmeniz gerekmez.  
  
- Dosya bağımlılıklarının sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek istiyorsunuz.  
  
- Uygulama veri dosyanızın yerelleştirilebilir olması gerekir (bkz. [WPF Genelleştirme ve Yerelleştirme Genel Bakış).](../advanced/wpf-globalization-and-localization-overview.md)  
  
> [!NOTE]
> Bu bölümde açıklanan kaynak dosyaları [XAML Kaynakları'nda](../../../desktop-wpf/fundamentals/xaml-resources-define.md) açıklanan kaynak dosyalarını ve Uygulama [Kaynaklarını Yönet 'de (.NET)](/visualstudio/ide/managing-application-resources-dotnet)açıklanan gömülü veya bağlantılı kaynaklardan farklıdır.  
  
### <a name="configuring-resource-files"></a>Kaynak Dosyalarını Yapılandırma  
 WPF'de kaynak dosyası, microsoft yapı altyapısı (MSBuild) projesine öğe `Resource` olarak dahil edilen bir dosyadır.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` `Resource`'ye ayarlayarak bir kaynak dosyası oluşturursunuz.  
  
 Proje oluşturulduğunda, MSBuild kaynağı derlemeye derler.  
  
### <a name="using-resource-files"></a>Kaynak Dosyalarını Kullanma  
 Kaynak dosyasını yüklemek için, <xref:System.Windows.Application.GetResourceStream%2A> istenen kaynak <xref:System.Windows.Application> dosyasını tanımlayan bir uri paketini geçerek sınıfın yöntemini arayabilirsiniz. <xref:System.Windows.Application.GetResourceStream%2A>kaynak <xref:System.Windows.Resources.StreamResourceInfo> dosyasını a olarak gösteren ve <xref:System.IO.Stream> içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, aşağıdaki <xref:System.Windows.Application.GetResourceStream%2A> kod bir <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek için nasıl kullanılacağını <xref:System.Windows.Controls.Frame> `pageFrame`gösterir ve bir ( ):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Arama, <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar. Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.  
  
 Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Kaynak Dosyaları Olarak Uygulama Kodu Dosyaları  
 Özel bir WPF uygulama kodu dosyası kümesi, windows, sayfalar, akış belgeleri ve kaynak sözlükleri de dahil olmak üzere paket URI'leri kullanılarak başvurulabilir. Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> bir uygulama başladığında yüklemek istediğiniz pencereye veya sayfaya başvurur bir URI paketiyle özelliği ayarlayabilirsiniz.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Bunu, bir XAML dosyası bir MSBuild projesine `Page` öğe olarak dahil edildiğinde yapabilirsiniz.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> Visual Studio'da, bir <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>projeye <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>yeni <xref:System.Windows.ResourceDictionary> , , , `Build Action` veya bir projeye, `Page`biçimlendirme dosyası için varsayılan olarak .  
  
 Öğeleri olan `Page` bir proje derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler ikili biçime dönüştürülür ve ilişkili derlemeye derlenir. Sonuç olarak, bu dosyalar tipik kaynak dosyalarıyla aynı şekilde kullanılabilir.  
  
> [!NOTE]
> Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya öğe `Resource` olarak yapılandırılır ve kod arkası dosyası yoksa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham ham'ın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ikili sürümü yerine bir derleme içine derlenir.  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>İçerik Dosyaları  
 *İçerik dosyası,* yürütülebilir bir derlemenin yanında gevşek bir dosya olarak dağıtılır. Derlemeye alınmasalar da derlemeler, her içerik dosyasıyla ilişki kuran meta verilerle derlenir.  
  
 Uygulamanız, bunları tüketen derlemeyi yeniden derlemeden güncelleştirmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmalısınız.  
  
### <a name="configuring-content-files"></a>İçerik Dosyalarını Yapılandırma  
 Projeye içerik dosyası eklemek için, uygulama veri dosyasının öğe `Content` olarak eklenmesi gerekir. Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmedığından, içerik dosyasının `CopyToOutputDirectory` yerleşik derlemeye göre bir konuma kopyalandığını belirtmek için MSBuild meta veri öğesini ayarlamanız gerekir. Bir proje her oluşturulunca kaynağın yapı çıktısı klasörüne kopyalanmasını `CopyToOutputDirectory` istiyorsanız, meta `Always` veri öğesini değerle birlikte ayarlarsınız. Aksi takdirde, `PreserveNewest` değeri kullanarak kaynağın yalnızca en yeni sürümünün yapı çıktısı klasörüne kopyalanmasını sağlayabilirsiniz.  
  
 Aşağıda, yalnızca kaynağın yeni bir sürümü projeye eklendiğinde yapı çıktıklasörüne kopyalanan bir içerik dosyası olarak yapılandırılan bir dosya gösterilmektedir.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` `Content` `Always` `Copy if newer` (aynı) ve `Copy always` (aynı) olarak ayarlayarak `Copy to Output Directory` bir içerik dosyası `PreserveNewest`oluşturursunuz.  
  
 Proje oluşturulduğunda, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> her içerik dosyası için derlemenin meta verilerine bir öznitelik derlenir.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Değer, içerik <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> dosyasının projedeki konumuna göre yolu ima eder. Örneğin, bir içerik dosyası bir proje alt klasöründe bulunuyorsa, ek yol <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> bilgileri değere dahil edilir.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Değer, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> yapı çıktıklasöründeki içerik dosyasına giden yolun değeridir.  
  
### <a name="using-content-files"></a>İçerik Dosyalarını Kullanma  
 İçerik dosyasını yüklemek için, <xref:System.Windows.Application.GetContentStream%2A> istenen içerik <xref:System.Windows.Application> dosyasını tanımlayan bir URI paketini geçerek sınıfın yöntemini arayabilirsiniz. <xref:System.Windows.Application.GetContentStream%2A>içerik <xref:System.Windows.Resources.StreamResourceInfo> dosyasını a <xref:System.IO.Stream> olarak gösteren ve içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, aşağıdaki <xref:System.Windows.Application.GetContentStream%2A> kod bir <xref:System.Windows.Controls.Page> içerik dosyasını yüklemek için nasıl kullanılacağını <xref:System.Windows.Controls.Frame> `pageFrame`gösterir ve içeriği olarak ayarlanır ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Arama, <xref:System.Windows.Application.GetContentStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar. Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.  
  
 Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>Menşe Dosyaları Sitesi  
 Kaynak dosyaları, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>'' nin tanımladığı şekilde, birlikte dağıtılan derlemelerle açık bir ilişkisi vardır. Ancak, derleme ve uygulama veri dosyası arasında örtük veya var olmayan bir ilişki kurmak isteyebileceğin zamanlar vardır:  
  
- Derleme zamanında bir dosya yok.  
  
- Çalışma süresine kadar derlemenizin hangi dosyalara ihtiyaç duyacağını bilemezsiniz.  
  
- İlişkili oldukları derlemeyi yeniden derlemeden dosyaları güncelleştirmek istiyorsunuz.  
  
- Uygulamanız ses ve video gibi büyük veri dosyaları kullanır ve kullanıcıların yalnızca istedikleri nde bunları karşıdan yüklemesini istersiniz.  
  
 Bu tür dosyaları, file:/// ve http:// düzenleri gibi geleneksel URI düzenlerini kullanarak yüklemek mümkündür.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Ancak, file:/// ve http:// düzenleri, uygulamanızın tam güvene sahip olmasını gerektirir. Uygulamanız Internet veya intranet'ten başlatılan bir XAML tarayıcı uygulamasıysa (XBAP) ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izinler kümesini istiyorsa, gevşek dosyalar yalnızca uygulamanın menşe sitesi (başlatma konumu). Bu tür *dosyalar, kaynak* dosyaları sitesi olarak bilinir.  
  
 Site kaynağı dosyaları kısmi güven uygulamaları için tek seçenekolmakla birlikte, kısmi güven uygulamalarıyla sınırlı değildir. Tam güven uygulamalarının, oluşturma zamanında bilmedikleri uygulama veri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:/// kullanabilirsiniz, ancak uygulama veri dosyaları aynı klasörde yüklü olması muhtemeldir, ya da bir alt klasörü, uygulama derleme. Bu durumda, file:/// kullanmak dosyanın tam yolunu çalışmanızı gerektirdiğinden, kaynak siteye başvurmak file:/// kullanmaktan daha kolaydır.  
  
> [!NOTE]
> Site kaynak dosyaları istemci makinesinde xaml tarayıcı uygulaması (XBAP) ile önbelleğe alınmaz, içerik dosyaları ise. Sonuç olarak, yalnızca özel olarak istendiğinde karşıdan yüklenirler. Bir XAML tarayıcı uygulaması (XBAP) uygulaması büyük medya dosyaları varsa, kaynak dosyaları sitesi olarak yapılandırılması ilk uygulama başlatma çok daha hızlı olduğu anlamına gelir ve dosyaları sadece isteğe bağlı olarak indirilir.  
  
### <a name="configuring-site-of-origin-files"></a>Menşe Sitesi Dosyalarını Yapılandırma  
 Kaynak sitenizin dosyaları derleme zamanında mevcut değilse veya bilinmiyorsa, `XCopy` komut satırı programını veya Microsoft Windows Yükleyicisini kullanmak da dahil olmak üzere gerekli dosyaların çalışma zamanında kullanılabilir olmasını sağlamak için geleneksel dağıtım mekanizmalarını kullanmanız gerekir.  
  
 Kaynak sitede yer almak istediğiniz dosyaları derleme saatinde biliyorsanız, ancak yine de açık bir bağımlılıktan kaçınmak istiyorsanız, bu dosyaları bir MSBuild projesine öğe olarak `None` ekleyebilirsiniz. İçerik dosyalarında olduğu gibi, MSBuild `CopyToOutputDirectory` özniteliğini, kaynak dosyasının `Always` sitenin, değeri veya `PreserveNewest` değeri belirterek yerleşik derlemeye göre bir konuma kopyalanmış olduğunu belirtmek için ayarlamanız gerekir.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` 'ye `None`ayarlayarak bir kaynak dosyası oluşturursunuz.  
  
 Proje oluşturulduğunda, MSBuild belirtilen dosyaları yapı çıktıklasörüne kopyalar.  
  
### <a name="using-site-of-origin-files"></a>Menşe Dosyalarının Sitesini Kullanma  
 Bir site kaynağı dosyasını yüklemek için, istenen <xref:System.Windows.Application> kaynak dosyasını tanımlayan bir URI paketini geçerek sınıfın <xref:System.Windows.Application.GetRemoteStream%2A> yöntemini arayabilirsiniz. <xref:System.Windows.Application.GetRemoteStream%2A>kaynak <xref:System.Windows.Resources.StreamResourceInfo> dosyasının sitesini a olarak gösteren ve <xref:System.IO.Stream> içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Application.GetRemoteStream%2A> menşe <xref:System.Windows.Controls.Page> dosyasının bir sitenin yüklenmesi <xref:System.Windows.Controls.Frame> için`pageFrame`nasıl kullanılacağını gösterir ve bir ( ) içeriği olarak ayarlayın.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Arama, <xref:System.Windows.Application.GetRemoteStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar. Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.  
  
 Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>Yapı Türünü Değiştirdikten Sonra Yeniden Oluşturma  
 Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, bu değişikliklerin uygulandığından emin olmak için uygulamanın tamamını yeniden oluşturmanız gerekir. Yalnızca uygulamayı oluşturursanız, değişiklikler uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
