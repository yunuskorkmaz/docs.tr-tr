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
ms.openlocfilehash: 57eae5067a72777db2c19331029b6df679a9fdce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956189"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]uygulamalar genellikle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], görüntü, video ve ses gibi yürütülebilir olmayan verileri içeren dosyalara bağımlıdır. Windows Presentation Foundation (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmaya, tanımlamaya ve kullanmaya yönelik özel destek sunar. Bu destek, aşağıdakiler de dahil olmak üzere belirli bir uygulama veri dosyası türü kümesinin etrafında döner:  
  
- **Kaynak dosyaları**: Çalıştırılabilir veya kitaplık [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bütünleştirilmiş koduna derlenen veri dosyaları.  
  
- **Içerik dosyaları**: Yürütülebilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir derlemeyle açık ilişkisi olan tek başına veri dosyaları.  
  
- **Kaynak dosyalarının sitesi**: Yürütülebilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir derlemeyle ilişkisi olmayan tek başına veri dosyaları.  
  
 Bu üç tür Dosya arasında yapılması gereken önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının derleme zamanında bilinmesinin bir örneğidir; bir derlemenin açık bilgisi vardır. Ancak, kaynak dosyalarının sitesi için bir derlemenin hiç bir bilgisi veya bir paket [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvurusu aracılığıyla örtük bilgi sahibi olmayabilir; ikincisi ise başvurulan kaynak dosyanın gerçekten mevcut sitesinin var olduğunu garanti etmez.  
  
 Uygulama veri dosyalarına başvurmak için Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanan paket düzenini kullanır.  
  
 Bu konuda, uygulama veri dosyalarının nasıl yapılandırılacağı ve kullanılacağı açıklanmaktadır.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Kaynak Dosyalar  
 Bir uygulama veri dosyasının her zaman bir uygulama için kullanılabilir olması gerekiyorsa, kullanılabilirliği güvence altına almanın tek yolu, uygulamayı uygulamanın ana yürütülebilir derlemesinde veya başvurulan derlemelerinden birinde derlemeniz gerekir. Bu tür bir uygulama veri dosyası *kaynak dosyası*olarak bilinir.  
  
 Kaynak dosyalarını şu durumlarda kullanmanız gerekir:  
  
- Bir derlemeye derlendikten sonra kaynak dosyanın içeriğini güncelleştirmeniz gerekmez.  
  
- Dosya bağımlılıklarının sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek isteyebilirsiniz.  
  
- Uygulama veri dosyanızın yerelleştirilebilir olması gerekir (bkz. [WPF Genelleştirme ve yerelleştirme genel bakış](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Bu bölümde açıklanan kaynak dosyaları, [xaml kaynaklarında](../advanced/xaml-resources.md) açıklanan kaynak dosyalarından farklıdır ve [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet)bölümünde açıklanan katıştırılmış veya bağlı kaynaklardan farklıdır.  
  
### <a name="configuring-resource-files"></a>Kaynak dosyalarını yapılandırma  
 ' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]De, bir kaynak dosyası, bir Microsoft Build Engine (MSBuild) projesinde `Resource` öğe olarak bulunan bir dosyadır.  
  
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
> ' [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]De, bir projeye dosya ekleyerek ve öğesini `Build Action` olarak `Resource`ayarlayarak bir kaynak dosyası oluşturursunuz.  
  
 Proje yapılandırıldığında, MSBuild kaynağı derlemeye derler.  
  
### <a name="using-resource-files"></a>Kaynak dosyalarını kullanma  
 Bir kaynak dosyasını yüklemek için, istenen kaynak dosyasını tanımlayan <xref:System.Windows.Application.GetResourceStream%2A> bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] geçirerek <xref:System.Windows.Application> sınıfının yöntemini çağırabilirsiniz. <xref:System.Windows.Application.GetResourceStream%2A>kaynak dosyasını <xref:System.Windows.Resources.StreamResourceInfo> bir <xref:System.IO.Stream> olarak kullanıma sunan ve içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, <xref:System.Windows.Application.GetResourceStream%2A> aşağıdaki kod, bir <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için nasıl kullanılacağını gösterir:  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Çağırma <xref:System.Windows.Application.GetResourceStream%2A> sırasında<xref:System.IO.Stream>öğesine erişiminizi sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek, öğesini açmayı ve dönüştürmeyi de sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) ' a nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Kaynak dosyaları olarak uygulama kodu dosyaları  
 Windows, sayfalar, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Flow belgeleri ve kaynak sözlükleri dahil olmak üzere [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]paket kullanılarak özel bir uygulama kodu dosyaları kümesine başvurulabilir. Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özelliğini, bir uygulama başlatıldığında yüklemek istediğiniz pencere veya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sayfaya başvuruda bulunan bir paketle ayarlayabilirsiniz.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Bir xaml dosyası bir MSBuild projesine `Page` öğe olarak dahil edildiğinde bunu yapabilirsiniz.  
  
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
> ' [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]De, bir projeye yeni <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> <xref:System.Windows.ResourceDictionary> `Build Action` ,,`Page`, veya ekler, biçimlendirme dosyası için varsayılan olarak olur. <xref:System.Windows.Documents.FlowDocument>  
  
 Öğeler içeren `Page` bir proje derlendiğinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , öğeler ikili biçime dönüştürülür ve ilişkili derlemeye derlenir. Sonuç olarak, bu dosyalar tipik kaynak dosyalarla aynı şekilde kullanılabilir.  
  
> [!NOTE]
> Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya bir `Resource` öğe olarak yapılandırıldıysa ve arka plan kod dosyasına sahip değilse, RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , ham [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dosyanın ikili sürümü yerine bir derlemeye derlenir.  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>İçerik dosyaları  
 Bir *içerik dosyası* , yürütülebilir bir bütünleştirilmiş kod ile gevşek bir dosya olarak dağıtılır. Derlemeler bir derlemeye derlenmese de, derlemeler her bir içerik dosyasıyla bir ilişki kuran meta veriler ile derlenir.  
  
 Uygulamanız, kendisini kullanan derlemeyi yeniden derlemeden güncelleştirebilmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmanız gerekir.  
  
### <a name="configuring-content-files"></a>Içerik dosyalarını yapılandırma  
 Bir projeye içerik dosyası eklemek için, bir uygulama veri dosyası bir `Content` öğe olarak dahil olmalıdır. Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmediği için, içerik dosyasının oluşturulan derlemeye göreli bir konuma kopyalanacağını belirtmek `CopyToOutputDirectory` için MSBuild meta verileri öğesini ayarlamanız gerekir. Bir proje oluşturulduğunda kaynağın yapı çıkış klasörüne kopyalanmasını isterseniz, `CopyToOutputDirectory` meta veri öğesini `Always` değeri ile ayarlarsınız. Aksi takdirde, yalnızca kaynağın en yeni sürümünün, `PreserveNewest` değeri kullanılarak derleme çıkış klasörüne kopyalandığından emin olabilirsiniz.  
  
 Aşağıda, yalnızca kaynağın yeni bir sürümü projeye eklendiğinde derleme çıkış klasörüne kopyalanmış bir içerik dosyası olarak yapılandırılmış bir dosya gösterilmektedir.  
  
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
> ' [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]De, bir projeye bir dosya ekleyerek ve `Copy always` `Content` `Copy if newer` `PreserveNewest` `Build Action` `Copy to Output Directory` öğesini olarak ayarlayarak ve (ile aynı) ve (ile aynı) olarak ayarlayarak bir içerik dosyası oluşturursunuz. `Always`  
  
 Proje yapılandırıldığında, bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> öznitelik her içerik dosyası için derlemenin meta verilerine derlenir.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Öğesinin değeri, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> projedeki konumuna göre içerik dosyasının yolunu belirtir. Örneğin, bir proje alt klasöründe bir içerik dosyası bulunuyorsa, ek yol bilgileri bu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değere dahil olur.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Değer aynı zamanda yapı çıkış klasöründeki içerik dosyası yolunun değeridir.  
  
### <a name="using-content-files"></a>Içerik dosyalarını kullanma  
 Bir içerik dosyasını yüklemek için, istenen içerik dosyasını tanımlayan <xref:System.Windows.Application.GetContentStream%2A> bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] geçirerek <xref:System.Windows.Application> sınıfının yöntemini çağırabilirsiniz. <xref:System.Windows.Application.GetContentStream%2A>içerik dosyasını <xref:System.Windows.Resources.StreamResourceInfo> bir <xref:System.IO.Stream> olarak kullanıma sunan ve içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, <xref:System.Windows.Application.GetContentStream%2A> aşağıdaki kod, bir <xref:System.Windows.Controls.Page> içerik dosyasını yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için kullanımını gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Çağırma <xref:System.Windows.Application.GetContentStream%2A> sırasında<xref:System.IO.Stream>öğesine erişiminizi sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek, öğesini açmayı ve dönüştürmeyi de sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) ' a nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Kaynak dosyalarının sitesi  
 Kaynak dosyaları, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>tarafından tanımlandığı gibi, birlikte dağıtılabilecek Derlemelerle açık bir ilişkiye sahiptir. Ancak, aşağıdakiler de dahil olmak üzere bir derleme ve uygulama veri dosyası arasında örtük veya mevcut olmayan bir ilişki oluşturmak isteyebileceğiniz durumlar vardır:  
  
- Derleme zamanında bir dosya yok.  
  
- Çalışma zamanına kadar derlemelerinizin hangi dosyaları gerektirdiğini bilemezsiniz.  
  
- Dosyaları, ilişkilendirildikleri derlemeyi yeniden derlemeden güncelleştirebilmek istiyorsunuz.  
  
- Uygulamanız, ses ve video gibi büyük veri dosyalarını kullanır ve yalnızca tercih ettikleri takdirde kullanıcıların bunları indirmesini istersiniz.  
  
 Bu dosya türlerini, File:///ve http://şemaları gibi geleneksel [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şemaları kullanarak yüklemek mümkündür.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Ancak, file:///ve http://şemaları uygulamanızın tam güvene sahip olmasını gerektirir. Uygulamanız [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] Internet 'ten veya intranetten başlatıldıysa ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izin kümesini isterse, gevşek dosyalar yalnızca uygulamanın kaynak sitesinden yüklenebilir ( başlatma konumu). Bu tür dosyalar, *kaynak dosyalarının sitesi* olarak bilinir.  
  
 Kaynak dosyalarının sitesi kısmi güven uygulamaları için tek seçenektir, ancak kısmi güven uygulamalarıyla sınırlı değildir. Tam güven uygulamalarının, derleme zamanında hakkında bilgi sahibi olmadıkları uygulama verileri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:///kullanabilir, ancak uygulama veri dosyalarının uygulama bütünleştirilmiş kodu ile aynı klasöre veya bir alt klasörüne yüklenebileceği olasıdır. Bu durumda, file:///kullanımı, dosyanın tam yolunu kullanmanızı gerektirdiğinden, kaynak başvuru sitesinin file:///kullanmaktan daha kolaydır.  
  
> [!NOTE]
> Kaynak dosyalarının sitesi, içerik dosyaları olduğu sırada bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] istemci makinesinde önbelleğe alınmaz. Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir. Bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] uygulamada büyük medya dosyaları varsa, bunları kaynak dosyaları sitesi olarak yapılandırmak, ilk uygulama başlatma işlemi çok daha hızlıdır ve dosyalar yalnızca isteğe bağlı olarak indirilir.  
  
### <a name="configuring-site-of-origin-files"></a>Kaynak dosyalarının sitesini yapılandırma  
 Kaynak dosyaları sitenizin derleme sırasında var olmayan veya bilinmeyen olması halinde, gerekli dosyaların çalışma zamanında kullanılabilir olmasını sağlamak için geleneksel dağıtım mekanizmalarını kullanmanız gerekir; `XCopy` Örneğin, komut satırı programını ya da [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Derleme zamanında, kaynak sitesinde bulunmasını istediğiniz dosyaları öğrenseniz, ancak yine de açık bir bağımlılığı önlemek istiyorsanız, bu dosyaları öğe olarak `None` bir MSBuild projesine ekleyebilirsiniz. İçerik dosyalarında olduğu gibi, kaynak dosya sitesinin, `CopyToOutputDirectory` `Always` değer veya `PreserveNewest` değer belirterek oluşturulan derlemeye göreli bir konuma kopyalandığını belirtmek için MSBuild özniteliğini ayarlamanız gerekir.  
  
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
> ' [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]De, bir projeye dosya ekleyerek ve öğesini `Build Action` olarak `None`ayarlayarak kaynak dosyanın bir sitesini oluşturun.  
  
 Proje yapılandırıldığında, MSBuild belirtilen dosyaları yapı çıkış klasörüne kopyalar.  
  
### <a name="using-site-of-origin-files"></a>Kaynak dosyalarının sitesini kullanma  
 Kaynak dosyasının bir sitesini yüklemek için, kaynak dosyanın istenen sitesini tanımlayan <xref:System.Windows.Application.GetRemoteStream%2A> bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] geçirerek <xref:System.Windows.Application> sınıfının yöntemini çağırabilirsiniz. <xref:System.Windows.Application.GetRemoteStream%2A>kaynak dosyanın <xref:System.Windows.Resources.StreamResourceInfo> sitesini bir <xref:System.IO.Stream> olarak kullanıma sunan ve içerik türünü açıklayan bir nesne döndürür.  
  
 Örnek olarak, aşağıdaki kod <xref:System.Windows.Application.GetRemoteStream%2A> , kaynak dosyanın bir <xref:System.Windows.Controls.Page> sitesini yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için kullanımını gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Çağırma <xref:System.Windows.Application.GetRemoteStream%2A> sırasında<xref:System.IO.Stream>öğesine erişiminizi sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek, öğesini açmayı ve dönüştürmeyi de sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) ' a nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Derleme türünü değiştirdikten sonra yeniden oluşturma  
 Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, değişikliklerin uygulandığından emin olmak için tüm uygulamayı yeniden oluşturmanız gerekir. Yalnızca uygulamayı oluşturuyorsanız, değişiklikler uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
