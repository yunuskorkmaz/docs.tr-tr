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
ms.openlocfilehash: 6b1a78ec56032d84d9699c2ecda89308779ee2da
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421143"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları
Microsoft Windows uygulamaları genellikle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], görüntü, video ve ses gibi yürütülebilir olmayan verileri içeren dosyalara bağımlıdır. Windows Presentation Foundation (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmaya, tanımlamaya ve kullanmaya yönelik özel destek sunar. Bu destek, aşağıdakiler de dahil olmak üzere belirli bir uygulama veri dosyası türü kümesinin etrafında döner:  
  
- **Kaynak dosyaları**: bir çalıştırılabilir veya kitaplık [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemesine derlenen veri dosyaları.  
  
- **Içerik dosyaları**: çalıştırılabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bütünleştirilmiş kodu ile açık ilişkiye sahip bağımsız veri dosyaları.  
  
- **Kaynak dosyalarının sitesi**: çalıştırılabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemesi ile ilişkisi olmayan tek başına veri dosyaları.  
  
 Bu üç tür Dosya arasında yapılması gereken önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının derleme zamanında bilinmesinin bir örneğidir; bir derlemenin açık bilgisi vardır. Ancak, kaynak dosyalarının sitesi için bir derlemenin hiç bilgisi olmayabilir veya bir paket tekdüzen kaynak tanımlayıcısı (URI) başvurusu aracılığıyla örtülü bilgi alabilir; İkinci durumda, başvurulan kaynak dosya sitesinin gerçekten var olduğu garanti yoktur.  
  
 Windows Presentation Foundation (WPF), uygulama veri dosyalarına başvurmak için, paket tekdüzen kaynak tanımlayıcısı (URI) şemasını kullanır ve bu, [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanmıştır.  
  
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
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], kaynak dosyası bir Microsoft Build Engine (MSBuild) projesinde `Resource` öğesi olarak bulunan bir dosyadır.  
  
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
> Visual Studio 'da bir projeye dosya ekleyerek ve `Build Action` `Resource`olarak ayarlayarak bir kaynak dosyası oluşturursunuz.  
  
 Proje yapılandırıldığında, MSBuild kaynağı derlemeye derler.  
  
### <a name="using-resource-files"></a>Kaynak dosyalarını kullanma  
 Bir kaynak dosyasını yüklemek için, istenen kaynak dosyasını tanımlayan bir paket URI 'sini geçirerek <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetResourceStream%2A> yöntemini çağırabilirsiniz. <xref:System.Windows.Application.GetResourceStream%2A>, kaynak dosyasını <xref:System.IO.Stream> olarak sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.  
  
 Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetResourceStream%2A> nasıl kullanacağınızı gösterir:  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <xref:System.Windows.Application.GetResourceStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Kaynak dosyaları olarak uygulama kodu dosyaları  
 Windows, sayfalar, Flow belgeleri ve kaynak sözlükleri dahil olmak üzere paket URI 'Leri kullanılarak özel bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama kodu dosyası kümesine başvurulabilir. Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özelliğini, bir uygulama başlatıldığında yüklemek istediğiniz pencere veya sayfaya başvuruda bulunan bir paket URI 'SI ile ayarlayabilirsiniz.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Bu işlemi, bir XAML dosyası `Page` öğesi olarak MSBuild projesine dahil edildiğinde yapabilirsiniz.  
  
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
> Visual Studio 'da, bir projeye yeni bir <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>veya <xref:System.Windows.ResourceDictionary> eklersiniz, biçimlendirme dosyasının `Build Action` varsayılan olarak `Page`olur.  
  
 `Page` öğeler içeren bir proje derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri ikili biçime dönüştürülür ve ilişkili derlemeye derlenir. Sonuç olarak, bu dosyalar tipik kaynak dosyalarla aynı şekilde kullanılabilir.  
  
> [!NOTE]
> Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası `Resource` öğesi olarak yapılandırılmışsa ve arka plan kod dosyası içermiyorsa, ham [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ikili sürümü yerine bir derlemeye derlenir.  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>İçerik dosyaları  
 Bir *içerik dosyası* , yürütülebilir bir bütünleştirilmiş kod ile gevşek bir dosya olarak dağıtılır. Derlemeler bir derlemeye derlenmese de, derlemeler her bir içerik dosyasıyla bir ilişki kuran meta veriler ile derlenir.  
  
 Uygulamanız, kendisini kullanan derlemeyi yeniden derlemeden güncelleştirebilmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmanız gerekir.  
  
### <a name="configuring-content-files"></a>Içerik dosyalarını yapılandırma  
 Bir projeye içerik dosyası eklemek için, bir uygulama veri dosyası `Content` öğesi olarak eklenmelidir. Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmediğinden, içerik dosyasının oluşturulan derlemeye göre bir konuma kopyalanacağını belirtmek için MSBuild `CopyToOutputDirectory` meta veri öğesini ayarlamanız gerekir. Bir proje oluşturulduğunda kaynağın yapı çıkış klasörüne kopyalanmasını isterseniz, `CopyToOutputDirectory` meta veri öğesini `Always` değeri ile ayarlarsınız. Aksi takdirde, `PreserveNewest` değerini kullanarak yalnızca kaynağın en yeni sürümünün derleme çıkış klasörüne kopyalandığından emin olabilirsiniz.  
  
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
> Visual Studio 'da, bir projeye dosya ekleyip `Build Action` `Content`ve `Copy to Output Directory` `Copy always` (`Always`ile aynı) ve `Copy if newer` (`PreserveNewest`ile aynı) olarak ayarlayarak bir içerik dosyası oluşturursunuz.  
  
 Proje yapılandırıldığında, her içerik dosyası için derlemenin meta verilerine bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği derlenir.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri, projedeki konumuna göre içerik dosyasının yolunu gösterir. Örneğin, bir proje alt klasöründe bir içerik dosyası bulunuyorsa, ek yol bilgileri <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değerine dahil olur.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri aynı zamanda yapı çıkış klasöründeki içerik dosyası yolunun değeridir.  
  
### <a name="using-content-files"></a>Içerik dosyalarını kullanma  
 Bir içerik dosyasını yüklemek için, istenen içerik dosyasını tanımlayan bir paket URI 'sini geçirerek <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetContentStream%2A> yöntemini çağırabilirsiniz. <xref:System.Windows.Application.GetContentStream%2A>, içerik dosyasını <xref:System.IO.Stream> olarak sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.  
  
 Örnek olarak, aşağıdaki kod, <xref:System.Windows.Controls.Page> bir içerik dosyası yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetContentStream%2A> nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <xref:System.Windows.Application.GetContentStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Kaynak dosyalarının sitesi  
 Kaynak dosyaları, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> tarafından tanımlandığı şekilde, birlikte dağıtılabilecek Derlemelerle açık bir ilişkiye sahiptir. Ancak, aşağıdakiler de dahil olmak üzere bir derleme ve uygulama veri dosyası arasında örtük veya mevcut olmayan bir ilişki oluşturmak isteyebileceğiniz durumlar vardır:  
  
- Derleme zamanında bir dosya yok.  
  
- Çalışma zamanına kadar derlemelerinizin hangi dosyaları gerektirdiğini bilemezsiniz.  
  
- Dosyaları, ilişkilendirildikleri derlemeyi yeniden derlemeden güncelleştirebilmek istiyorsunuz.  
  
- Uygulamanız, ses ve video gibi büyük veri dosyalarını kullanır ve yalnızca tercih ettikleri takdirde kullanıcıların bunları indirmesini istersiniz.  
  
 Bu dosya türlerini, file:///ve http://şemaları gibi geleneksel URI düzenlerini kullanarak yüklemek mümkündür.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Ancak, file:///ve http://şemaları uygulamanızın tam güvene sahip olmasını gerektirir. Uygulamanız Internet 'ten veya intranetten başlatılan bir XAML tarayıcı uygulaması (XBAP) ise ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izin kümesini isterse, gevşek dosyalar yalnızca uygulamanın kaynak sitesi (başlatma konumu). Bu tür dosyalar, *kaynak dosyalarının sitesi* olarak bilinir.  
  
 Kaynak dosyalarının sitesi kısmi güven uygulamaları için tek seçenektir, ancak kısmi güven uygulamalarıyla sınırlı değildir. Tam güven uygulamalarının, derleme zamanında hakkında bilgi sahibi olmadıkları uygulama verileri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:///kullanabilir, ancak uygulama veri dosyalarının uygulama bütünleştirilmiş kodu ile aynı klasöre veya bir alt klasörüne yüklenebileceği olasıdır. Bu durumda, file:///kullanımı, dosyanın tam yolunu kullanmanızı gerektirdiğinden, kaynak başvuru sitesinin file:///kullanmaktan daha kolaydır.  
  
> [!NOTE]
> Kaynak dosyalarının sitesi, istemci makinesindeki bir XAML tarayıcı uygulaması (XBAP) ile önbelleğe alınmaz, ancak içerik dosyaları. Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir. Bir XAML tarayıcı uygulaması (XBAP) uygulamasının büyük medya dosyaları varsa, bunları kaynak dosyaları sitesi olarak yapılandırmak, ilk uygulama başlatma işlemi çok daha hızlıdır ve dosyalar yalnızca isteğe bağlı olarak indirilir.  
  
### <a name="configuring-site-of-origin-files"></a>Kaynak dosyalarının sitesini yapılandırma  
 Kaynak dosyaları siteniz derleme sırasında mevcut değilse veya bilinmiyorsa, gerekli dosyaların çalışma zamanında kullanılabilir olmasını sağlamak için, `XCopy` komut satırı programını veya Microsoft Windows 'u kullanma dahil olmak üzere geleneksel dağıtım mekanizmalarını kullanmanız gerekir. Yükleyicinin.  
  
 Derleme zamanında, kaynak sitesinde bulunmasını istediğiniz dosyaları öğrenseniz, ancak yine de açık bir bağımlılığı önlemek istiyorsanız, bu dosyaları bir MSBuild projesine `None` öğesi olarak ekleyebilirsiniz. İçerik dosyalarında olduğu gibi, kaynak dosya sitesinin, `Always` değerini veya `PreserveNewest` değerini belirterek oluşturulan derlemeye göreli bir konuma kopyalandığını belirtmek için MSBuild `CopyToOutputDirectory` özniteliğini ayarlamanız gerekir.  
  
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
> Visual Studio 'da bir projeye dosya ekleyip `Build Action` `None`olarak ayarlayarak kaynak dosyanın bir sitesini oluşturun.  
  
 Proje yapılandırıldığında, MSBuild belirtilen dosyaları yapı çıkış klasörüne kopyalar.  
  
### <a name="using-site-of-origin-files"></a>Kaynak dosyalarının sitesini kullanma  
 Kaynak dosyasının bir sitesini yüklemek için, <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetRemoteStream%2A> yöntemini çağırıp, istenen kaynak dosyası sitesini tanımlayan bir paket URI 'SI geçirilerek. <xref:System.Windows.Application.GetRemoteStream%2A>, kaynak dosyasının sitesini bir <xref:System.IO.Stream> olarak kullanıma sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.  
  
 Örnek olarak, aşağıdaki kod, kaynak dosyanın <xref:System.Windows.Controls.Page> bir sitesini yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetRemoteStream%2A> nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <xref:System.Windows.Application.GetRemoteStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir. Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.  
  
 Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Derleme türünü değiştirdikten sonra yeniden oluşturma  
 Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, değişikliklerin uygulandığından emin olmak için tüm uygulamayı yeniden oluşturmanız gerekir. Yalnızca uygulamayı oluşturuyorsanız, değişiklikler uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
