---
title: "WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19fd82daabd5ed12776b2deee6bc850529a6ef23
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]uygulamalar genellikle gibi yürütülebilir olmayan veri içeren dosyaları bağımlı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], resim, video ve ses. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]yapılandırma, tanımlayan ve bu tür bir uygulama verileri dosyaları adı verilen veri dosyalarını kullanmak için özel destek sağlar. Bu destek, uygulama verilerini dosya türleri dahil olmak üzere, belirli bir dizi döner:  
  
-   **Kaynak dosyaları**: bir yürütülebilir dosya veya kitaplık derlenmiş veri dosyaları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
-   **İçerik dosyaları**: yürütülebilir bir dosya ile açık bir ilişkisi olmayan bağımsız veri dosyaları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
-   **Kaynak dosyaları sitesi**: yürütülebilir bir dosya ile ilişkisi olmayan bağımsız veri dosyaları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derleme.  
  
 Bu dosyaları üç türleri arasında yapmak için bir önemli fark, kaynak dosyaları ve içerik dosyalarının derleme zamanında bilinen olur; bir derleme bunların açık bilgisine sahiptir. Kaynak dosyaları sitesi için Bununla birlikte, bir derlemeyi bunları olanağıyla hiç olabilir veya bir paketi aracılığıyla örtülü bilgisi [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvuru; durumunda İkincisi, kaynak dosya başvurulan sitesinin gerçekten var garantisi yoktur.  
  
 Uygulama verileri dosyaları, başvurmak için [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] paketi kullanan [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] içinde ayrıntılı olarak açıklanmıştır düzeni [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Bu konuda, yapılandırma ve uygulama verileri dosyaları kullanma açıklar.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Kaynak Dosyalar  
 Uygulama veri dosyası her zaman bir uygulama için kullanılabilir olması durumunda kullanılabilirliğini garanti etmek için tek bir uygulamanın ana çalıştırılabilir bütünleştirilmiş koduna veya başvurulan bütünleştirilmiş derlemek için yoludur. Bu tür bir uygulama veri dosyası olarak bilinen bir *kaynak dosyası*.  
  
 Kaynak kullanması gereken zaman dosyaları:  
  
-   Bütünleştirilmiş koda derlenmemiş sonra kaynak dosyanın içeriğini güncelleştirmeniz gerekmez.  
  
-   Dosya bağımlılıkları sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek isteyebilirsiniz.  
  
-   Uygulama veri dosyasının yerelleştirilebilir olması gerekir (bkz [WPF Genelleştirme ve yerelleştirme genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Bu bölümde açıklanan kaynak dosyaları kaynak dosyaları açıklanan farklı [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) ve açıklanan katıştırılmış veya bağlantılı kaynakları farklı [yönetme uygulama kaynakları (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Kaynak dosyalarını yapılandırma  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir kaynak dosyası yer aldığı bir dosyadır bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak bir `Resource` öğesi.  
  
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
>  İçinde [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], bir dosyayı bir proje ve ayarı ekleyerek kaynak dosyası oluşturma kendi `Build Action` için `Resource`.  
  
 Proje yapılandırıldığında [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kaynak bütünleştirilmiş koda derler.  
  
### <a name="using-resource-files"></a>Kaynak dosyalarını kullanma  
 Kaynak dosyayı yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetResourceStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] istenen kaynak dosyayı tanımlar. <xref:System.Windows.Application.GetResourceStream%2A>döndüren bir <xref:System.Windows.Resources.StreamResourceInfo> olarak kaynak dosyayı sunan nesnesi bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örnek olarak, aşağıdaki kodu nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetResourceStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> kaynak dosyasını ve içeriği olarak ayarlanmış bir <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Arama sırasında <xref:System.Windows.Application.GetResourceStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özellik türüne dönüştürme gerçekleştirmeniz gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgilenebilmek <xref:System.IO.Stream> tarafından doğrudan kodu kullanarak tür özelliğine bir kaynak dosyası yükleniyor.  
  
 Aşağıdaki örnekte nasıl yükleneceğini gösterir bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Aşağıdaki örnek biçimlendirmesi olan önceki örnekte eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Kaynak dosyaları olarak uygulama kod dosyaları  
 Özel kümesi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama kod dosyaları paketi kullanarak başvurulabilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]windows, sayfalar, akış belgeleri ve kaynak sözlükleri dahil olmak üzere. Örneğin, ayarlayabileceğiniz <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özellik paketi ile [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] penceresi veya bir uygulama başlatıldığında yüklemek istediğiniz sayfa başvuruyor.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Olduğunda bunu bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya dahil bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak bir `Page` öğesi.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], yeni eklediğiniz <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, veya <xref:System.Windows.ResourceDictionary> bir proje `Build Action` için biçimlendirme dosya için varsayılan `Page`.  
  
 Bir proje ile zaman `Page` öğeleri derlenmiş, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri ikili biçime dönüştürülür ve ilişkili bütünleştirilmiş koda derlenir. Sonuç olarak, bu dosyalar normal kaynak dosyaları aynı şekilde kullanılabilir.  
  
> [!NOTE]
>  Varsa bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya olarak yapılandırılmış bir `Resource` öğesi ve ham, arka plan kodu dosyanın yok [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham ikili sürümü yerine bir derleme derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>İçerik dosyaları  
 A *içerik dosyası* çalıştırılabilir bir bütünleştirilmiş kodun yanında gevşek bir dosya olarak dağıtılır. Bir bütünleştirilmiş koda derlenmemiş rağmen derlemeler her içerik dosyasının ile bir ilişki kurar meta verilerle derlenir.  
  
 Uygulamanız, bunları tüketir derleme derlemeden güncelleştirebilmek istediğiniz uygulama verileri dosyaları belirli bir dizi gerektirdiğinde, içerik dosyaları kullanmanız gerekir.  
  
### <a name="configuring-content-files"></a>İçerik dosyalarını yapılandırma  
 Bir içerik dosyası için bir proje eklemek için uygulama veri dosyası olarak dahil edilmelidir bir `Content` öğesi. Bir içerik dosyası doğrudan bütünleştirilmiş koda derlenmemiş olduğundan, ayrıca, ayarlamanız gerekir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` içerik dosyasını yerleşik bütünleştirilmiş göreli bir konuma kopyalanır belirtmek için meta veri öğesi. Her zaman yapı çıktı klasörüne Kopyalanacak kaynak istiyorsanız bir proje oluşturulmuştur, ayarladığınız `CopyToOutputDirectory` olan meta veri öğesi `Always` değeri. Aksi halde, kaynak yalnızca en yeni sürümünü kullanarak yapı çıktı klasörüne kopyalanır sağlayabilirsiniz `PreserveNewest` değeri.  
  
 Aşağıdaki klasörü kaynak yeni bir sürümü olduğunda projeye eklenir yapı kopyalanan bir içerik dosyası çıktı olarak yapılandırılmış bir dosya gösterir.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], bir dosyayı bir proje ve ayarı ekleyerek bir içerik dosyası oluşturma kendi `Build Action` için `Content`ve kendi `Copy to Output Directory` için `Copy always` (aynı `Always`) ve `Copy if newer` (aynı `PreserveNewest`).  
  
 Proje yapılandırıldığında, bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği her içerik dosyasının derlemenin meta verilerini derlenir.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Değeri <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> proje konumuna göre içerik dosyasının yolunu gösterir. Bir içerik dosyası projenin alt klasöründe bulunan, örneğin, ek yol bilgileri birleştirilir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Değeri değeridir ayrıca yapı çıkış klasöründe içerik dosyasının yolu.  
  
### <a name="using-content-files"></a>İçerik dosyalarını kullanma  
 Bir içerik dosyası yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetContentStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] istenen içerik dosyasını tanımlar. <xref:System.Windows.Application.GetContentStream%2A>döndüren bir <xref:System.Windows.Resources.StreamResourceInfo> olarak içerik dosyasını sunan nesnesi bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örnek olarak, aşağıdaki kodu nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetContentStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> içerik dosyasını ve içeriği olarak ayarlanmış bir <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Arama sırasında <xref:System.Windows.Application.GetContentStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özellik türüne dönüştürme gerçekleştirmeniz gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgilenebilmek <xref:System.IO.Stream> tarafından doğrudan kodu kullanarak tür özelliğine bir kaynak dosyası yükleniyor.  
  
 Aşağıdaki örnekte nasıl yükleneceğini gösterir bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Aşağıdaki örnek biçimlendirmesi olan önceki örnekte eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Kaynak dosyaları sitesi  
 Kaynak dosyalarınız yanı sıra, dağıtılmış derlemeler ile açık bir ilişkisi tarafından tanımlandığı şekilde <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Ancak, bir derlemeyi ve ne zaman dahil olmak üzere bir uygulama veri dosyası arasında örtük veya var olmayan bir ilişki kurmak istediğinizde zamanlar vardır:  
  
-   Bir dosya derleme zamanında yok.  
  
-   Derlemenizi çalışma zamanına kadar gerektirecektir hangi dosyaların bilinmiyor.  
  
-   Güncelleştirme dosyaları ile ilişkili derleme derlemeden kullanabilmek ister.  
  
-   Uygulamanız ses ve video gibi büyük veri dosyalarını kullanır ve yalnızca isterlerse bunları indirmek istediğiniz.  
  
 Bu tür kullanarak geleneksel dosyaları yüklemek mümkündür [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] file:/// ve http:// düzenleri gibi düzenleri.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Ancak, file:/// ve http:// düzenleri uygulamanızın tam güven gerektirir. Uygulamanız ise bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] Internet veya intranet tarafından başlatılmış ve yalnızca bu konumlardan başlatılan uygulamalara gevşek dosyalarını kaynağı (uygulamanın sitesinden yalnızca yüklenebilir izin verilen izinler kümesini istekleri Konum Başlat). Bu tür dosyalar olarak bilinir *kaynak site* dosyaları.  
  
 Kaynak dosyaları sitesi kısmi güven uygulamaları için tek seçenek olan ancak kısmi güven uygulamaları için sınırlı. Tam güven uygulamaları, bunlar derleme zamanında bilmiyor uygulama verileri dosyaları yüklemek hala gerekebilir; tam güven uygulamalarının file:/// kullanabilirken uygulama verileri dosyaları aynı klasörde veya bir alt klasörü, uygulama derleme yüklenecek olasıdır. File:/// kullanarak dosyanın tam yolunu çalışmanız gerekir çünkü bu durumda, kaynak sitesi kullanarak file:/// kullanmaktan daha kolaydır.  
  
> [!NOTE]
>  Kaynak dosyaları ile önbelleğe alınmaz site bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] içerik dosyaları açıkken bir istemci makine üzerinde. Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir. Varsa bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] uygulama büyük medya dosyalarını, kaynak dosyaları sitesi anlamına gelir başlangıç uygulaması başlatma çok daha hızlıdır ve yalnızca isteğe bağlı olarak indirilen dosyaları gibi yapılandırmadan sahiptir.  
  
### <a name="configuring-site-of-origin-files"></a>Kaynak dosyaları sitesi yapılandırma  
 Geleneksel dağıtım kullanmanıza gerek olmayan veya bilinmeyen sitenizi kaynak dosyaları derleme zamanında, gerekli dosyaları sağlamaya yönelik mekanizmalarını kullanarak da dahil olmak üzere çalışma zamanında kullanılabilir `XCopy` komut satırı programı veya [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Kaynak sitede bulunması istiyor ancak yine de açık bağımlılığı önlemek istiyor dosyaları derleme zamanında biliyorsanız, bu dosyalara ekleyebileceğiniz bir [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] proje olarak `None` öğesi. İçerik dosyaları ile ayarlamak gerek duyduğunuz [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` site kaynak dosya yerleşik derleme göreli ya da belirterek bir konuma kopyalanır belirtmek için özniteliği `Always` değeri veya `PreserveNewest` değeri.  
  
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
>  İçinde [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], bir dosyayı bir proje ve ayarı ekleyerek kaynak dosya bir site oluşturun, `Build Action` için `None`.  
  
 Proje yapılandırıldığında [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] belirtilen dosyaları yapı çıktı klasörüne kopyalar.  
  
### <a name="using-site-of-origin-files"></a>Kaynak dosyaları sitesi kullanma  
 Kaynak dosya sitesini yüklemek için çağırabilirsiniz <xref:System.Windows.Application.GetRemoteStream%2A> yöntemi <xref:System.Windows.Application> sınıfı, bir paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kaynak dosya istenen site tanımlar. <xref:System.Windows.Application.GetRemoteStream%2A>döndüren bir <xref:System.Windows.Resources.StreamResourceInfo> site kaynak dosya kullanıma sunar nesnesi bir <xref:System.IO.Stream> ve içerik türünü açıklar.  
  
 Örnek olarak, aşağıdaki kodu nasıl kullanılacağını gösterir. <xref:System.Windows.Application.GetRemoteStream%2A> yüklemek için bir <xref:System.Windows.Controls.Page> kaynak site dosya ve içeriği olarak ayarlanmış bir <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Arama sırasında <xref:System.Windows.Application.GetRemoteStream%2A> e erişmenizi <xref:System.IO.Stream>, ek iş, kendisiyle ayarlayacağınız özellik türüne dönüştürme gerçekleştirmeniz gerekir. Bunun yerine, sağlayabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açma ve dönüştürme ilgilenebilmek <xref:System.IO.Stream> tarafından doğrudan kodu kullanarak tür özelliğine bir kaynak dosyası yükleniyor.  
  
 Aşağıdaki örnekte nasıl yükleneceğini gösterir bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) kullanılarak kod.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Aşağıdaki örnek biçimlendirmesi olan önceki örnekte eşdeğer.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Yapı türü değiştirdikten sonra yeniden oluşturma  
 Uygulama veri dosyası derleme türünü değiştirdikten sonra bu değişikliklerin uygulandığından emin olmak için tüm uygulamayı yeniden yapılandırmanız gerekir. Yalnızca uygulamayı yapılandırdıysanız, değişiklikleri uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF içinde URI'leri paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
