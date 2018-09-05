---
title: WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
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
ms.openlocfilehash: 5bf1a0e1d4d8f620f83aab50aa50009a0f6a6cf4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561450"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] uygulamalar genellikle gibi yürütülebilir olmayan veriler içeren dosyaları bağımlıdır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], görüntü, video ve ses. Windows Presentation Foundation (WPF), yapılandırma, belirlemekten ve bu tür bir uygulama verileri dosyaları olarak adlandırılan veri dosyalarını kullanarak özel destek sunar. Bu destek, uygulama verilerini dosya türleri dahil olmak üzere, belirli bir dizi döner:  
  
-   **Kaynak dosyaları**: bir yürütülebilir veya kitaplık derlenmiş veri dosyalarını [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
-   **İçerik dosyaları**: yürütülebilir bir dosya ile açık bir ilişkisi olmayan tek başına veri dosyalarını [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
-   **Kaynak dosyaları sitesi**: yürütülebilir bir dosya ile ilişkisi olmayan tek başına veri dosyalarını [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
 Kaynak dosyalar ve içerik dosyalarını, derleme zamanında bilinen dosyaları bu üç tür arasında olmak için önemli bir ayrım olduğundan; bir derleme, bunların açık bilgisine sahiptir. Kaynak dosyaları sitesi için ancak, bir derleme bunları olanağıyla, olabilir veya bir paketi aracılığıyla örtük bilgiye [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvuru; İkincisi, durum başvurulan site kaynak dosyasının gerçekten var olduğunu garanti yoktur.  
  
 Windows Presentation Foundation (WPF) uygulaması veri dosyalara başvurmak için paketi kullanır [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ayrıntılı olarak açıklanan düzeni [paketi URI ' WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Bu konuda, yapılandırma ve uygulama verileri dosyaları kullanma açıklar.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Kaynak Dosyalar  
 Uygulama veri dosyası her zaman bir uygulama için kullanılabilir olması gerekiyorsa, kullanılabilirlik düzeyi garanti yalnızca uygulamanın ana çalıştırılabilir derlemesinin veya onun başvurulmuş derlemeler içinde derlemek için yoludur. Bu tür bir uygulama veri dosyası olarak da bilinen bir *kaynak dosyası*.  
  
 Kaynak kullanmanız gerektiği zaman dosyaları:  
  
-   Bütünleştirilmiş kod içine derlenmiş olan sonra kaynak dosyanın içeriği güncelleştirmeniz gerekmez.  
  
-   Uygulama dağıtım karmaşıklığı bağımlılıklar sayısını azaltarak basitleştirmek isteyebilirsiniz.  
  
-   Uygulama verileri dosyanızı yerelleştirilebilir olması gerekir (bkz [WPF genelleştirmesi ve yerelleştirmesine genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Bu bölümde açıklanan kaynak dosyaları kaynak dosyaları açıklanan farklı [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) ve açıklanan gömülü veya bağlantılı kaynakların farklı [uygulama kaynaklarını yönetme (.NET) ](https://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Kaynak dosyalarını yapılandırma  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], kaynak dosya yer aldığı bir dosya, bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak bir `Resource` öğesi.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  İçinde [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], bir dosya için bir proje ve ayarı ekleyerek bir kaynak dosyası oluşturun, `Build Action` için `Resource`.  
  
 Proje derlenirken [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kaynak bütünleştirilmiş kod içine derler.  
  
### <a name="using-resource-files"></a>Kaynak dosyalarını kullanma  
 Kaynak dosyayı yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetResourceStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , istenen kaynak dosyasını belirtir. <xref:System.Windows.Application.GetResourceStream%2A> döndürür bir <xref:System.Windows.Resources.StreamResourceInfo> kaynak dosyası olarak sunan bir nesne bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örneğin, aşağıdaki kod nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetResourceStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> kaynak dosya ve içeriği olarak ayarlanmış bir <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Çağrılırken <xref:System.Windows.Application.GetResourceStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özelliği türüne dönüştürme yapılması gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgileniriz <xref:System.IO.Stream> tarafından kaynak dosyası kod kullanarak bir tür özelliği doğrudan yükleniyor.  
  
 Aşağıdaki örnek nasıl yükleneceğini gösterir. bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Aşağıdaki örnek, biçimlendirme, önceki örnekte bulunan eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Kaynak dosyaları olarak uygulama kod dosyaları  
 Özel kümesi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] paketi kullanarak uygulama kodunu dosyaları başvurulabilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]windows, sayfalar, akış belgeleri ve kaynak sözlükleri dahil. Örneğin, ayarlayabilirsiniz <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özellik paketi ile [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pencere veya bir uygulaması başladığında yüklenmesini istediğiniz sayfa başvuruyor.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Olduğunda bunu yapabilirsiniz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası dahil bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak bir `Page` öğesi.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], yeni eklediğiniz <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, veya <xref:System.Windows.ResourceDictionary> bir projeye `Build Action` için biçimlendirme dosya için varsayılan `Page`.  
  
 Bir proje ile zaman `Page` öğeleri derlendiğinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri ikili biçime dönüştürülür ve ilişkili bütünleştirilmiş kod içine derlenmiş. Sonuç olarak, bu dosyalar, genel kaynak dosyaları aynı şekilde kullanılabilir.  
  
> [!NOTE]
>  Varsa bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya olarak yapılandırılmış bir `Resource` öğesi ekleyin ve ham, arka plan kod dosyası yoksa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham bir ikili sürümünü yerine bir bütünleştirilmiş kod derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>İçerik dosyaları  
 A *içerik dosyası* yürütülebilir bir bütünleştirilmiş kodun yanında gevşek bir dosya olarak dağıtılır. Bütünleştirilmiş kod içine derlenmiş değil olsa da, derlemeleri her içerik dosyası ile bir ilişki kurar meta verileri ile derlenir.  
  
 Uygulamanız, bunları kullanan derleme yeniden derlemeden DLL'yi güncelleştirebilirsiniz olmasını istediğiniz uygulama verileri dosyaları belirli bir dizi gerektirdiğinde, içerik dosyalarını kullanmanız gerekir.  
  
### <a name="configuring-content-files"></a>İçerik dosyalarını yapılandırma  
 Bir içerik dosyası bir projeye eklemek için uygulama veri dosyası olarak dahil edilmesi gereken bir `Content` öğesi. Bir içerik dosyası doğrudan bütünleştirilmiş koda derlenmemiş olduğundan, ayrıca ayarlamanız gerekir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` içerik dosya derlemesi göreli bir konuma kopyalanır belirtmek için bir meta veri öğesi. Her yapı çıkış klasörüne Kopyalanacak kaynak istiyorsanız, bir projenin, ayarladığınız `CopyToOutputDirectory` meta veri öğesi ile `Always` değeri. Aksi takdirde, kaynağın yalnızca en yeni sürümünü kullanarak yapı çıktı klasörüne kopyalandığından emin olabilirsiniz `PreserveNewest` değeri.  
  
 Aşağıdaki yapıya kopyalanan bir içerik dosyası klasör kaynağın için yeni bir sürümü, projeye eklenir çıktı olarak yapılandırılmış bir dosya gösterir.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], bir dosya için bir proje ve ayarı ekleyerek bir içerik dosyası oluşturabilir, `Build Action` için `Content`ve onun `Copy to Output Directory` için `Copy always` (aynı `Always`) ve `Copy if newer` (aynı `PreserveNewest`).  
  
 Proje oluşturulduğunda bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği, her bir içerik dosyası için derleme meta verileri derlenir.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Değerini <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> projedeki konumuna göre içerik dosyasının yolunu gösterir. Bir içerik dosyası bir proje alt klasörde bulunuyorsa, örneğin, ek yol bilgileri birleştirilir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Değeri değeridir ayrıca yapı çıkış klasöründe içerik dosyasının yolu.  
  
### <a name="using-content-files"></a>İçerik dosyalarını kullanma  
 Bir içerik dosyası yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetContentStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] istenen içerik dosyası tanımlar. <xref:System.Windows.Application.GetContentStream%2A> döndürür bir <xref:System.Windows.Resources.StreamResourceInfo> içerik dosyası olarak sunan bir nesne bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örneğin, aşağıdaki kod nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetContentStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> içerik dosyasını ve içeriği olarak ayarlanmış bir <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Çağrılırken <xref:System.Windows.Application.GetContentStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özelliği türüne dönüştürme yapılması gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgileniriz <xref:System.IO.Stream> tarafından kaynak dosyası kod kullanarak bir tür özelliği doğrudan yükleniyor.  
  
 Aşağıdaki örnek nasıl yükleneceğini gösterir. bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Aşağıdaki örnek, biçimlendirme, önceki örnekte bulunan eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Kaynak dosyaları sitesi  
 Kaynak dosyaları tarafından tanımlanan yanı sıra, dağıtılmış derlemeler ile açık bir ilişkisi olan <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Ancak, bir derleme ve ne zaman dahil olmak üzere bir uygulama veri dosyası arasında örtük veya var olmayan bir ilişki ne zaman ya da kurmak isteyebilirsiniz zamanlar vardır:  
  
-   Bir dosya, derleme zamanında yok.  
  
-   Derlemenizin çalışma zamanına kadar gerektirecek hangi dosyaların bilmiyorum.  
  
-   Güncelleştirme dosyaları ile ilişkili derleme yeniden derlemeye gerek kalmadan yönetebilmek istiyorsunuz.  
  
-   Ses ve video gibi büyük veri dosyalarını uygulamanızın kullandığı ve kullanıcılar için seçerseniz, bunları indirmek için yalnızca istersiniz.  
  
 Bu tür kullanarak geleneksel dosyaları yüklemek mümkündür [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzenleri, file:/// ve http:// düzeni gibi.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Ancak file:/// ve http:// düzeni uygulamanızın tam güven gerektirir. Uygulamanız bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] Internet veya intranet başlatıldı ve yalnızca bu konumlardan başlatılan uygulamalar için gevşek dosyalar kaynak (uygulamanın sitesinden yalnızca yüklenebilir izin verilen izinler kümesini ister Konum başlatın). Bu tür dosyalar olarak bilinir *kaynak siteyi* dosyaları.  
  
 Kaynak dosyaları sitesi olan tek seçenek kısmi güven uygulamaları, ancak bunlarla sınırlı olmamak kısmi güven uygulamaları için. Tam güven uygulamaları, oluşturma zamanında bilmiyor uygulama verileri dosyaları yüklemek yine de gerekebilir. tam güven uygulamalarının file:/// kullanabilirken uygulama verileri dosyaları aynı klasörde veya alt, uygulama derlemesine yüklenecek olasıdır. File:/// kullanarak dosyanın tam yolunu çalışmanız gerekir çünkü bu durumda, kaynak sitesi kullanarak file:/// kullanmaktan daha kolaydır.  
  
> [!NOTE]
>  Kaynak dosyaları ile önbelleğe alınmaz siteyi bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] içerik dosyalarını olsa da bir istemci makine üzerinde. Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir. Varsa bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] uygulamanın büyük medya dosyalarını, kaynak dosyaları sitesi ilk uygulama başlatma çok daha hızlıdır ve yalnızca isteğe bağlı olarak indirilen dosyaları anlamına gelir. bunları yapılandırma vardır.  
  
### <a name="configuring-site-of-origin-files"></a>Kaynak dosyaları sitesi yapılandırma  
 Mevcut olmayan veya bilinmeyen derleme zamanında kaynak dosyaları, site, geleneksel dağıtım kullanmanız gerekir gerekli dosyaları sağlamaya yönelik bir mekanizma kullanarak da dahil olmak üzere, çalışma zamanında kullanılabilir `XCopy` komut satırı programı veya [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Kaynak sitede bulunmasını gibi ancak yine de açık bağımlılığı önlemek istiyor dosyaları derleme zamanında biliyorsanız, bu dosyalara ekleyebileceğiniz bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak `None` öğesi. İçerik dosyaları ayarlamak gerek duyduğunuz [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` site kaynak dosya derlemesi göre ya da belirterek bir konuma kopyalanır belirtmek için özniteliği `Always` değeri veya `PreserveNewest` değeri.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], bir dosya için bir proje ve ayarı ekleyerek kaynak dosyasının bir site oluşturun, `Build Action` için `None`.  
  
 Proje derlenirken [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] belirtilen dosyaları yapı çıktı klasörüne kopyalar.  
  
### <a name="using-site-of-origin-files"></a>Kaynak dosyaları sitesi kullanma  
 Kaynak dosyasının bir siteyi yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetRemoteStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] istenen site kaynak dosyası tanımlar. <xref:System.Windows.Application.GetRemoteStream%2A> döndürür bir <xref:System.Windows.Resources.StreamResourceInfo> site kaynak dosyası sunan bir nesne bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örneğin, aşağıdaki kod nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetRemoteStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> kaynak siteyi içeriği olarak ayarlayın ve dosya bir <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Çağrılırken <xref:System.Windows.Application.GetRemoteStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özelliği türüne dönüştürme yapılması gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgileniriz <xref:System.IO.Stream> tarafından kaynak dosyası kod kullanarak bir tür özelliği doğrudan yükleniyor.  
  
 Aşağıdaki örnek nasıl yükleneceğini gösterir. bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Aşağıdaki örnek, biçimlendirme, önceki örnekte bulunan eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Yapı türü değiştirildikten sonra yeniden oluşturma  
 Uygulama veri dosyası derleme türü değiştirdikten sonra bu değişikliklerin uygulandığından emin olmak için uygulamanın tamamını yeniden derlemek gerekir. Yalnızca uygulama oluşturuyorsanız, değişiklikler uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF İçinde URI'leri Paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
