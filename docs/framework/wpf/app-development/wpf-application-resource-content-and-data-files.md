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
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="01d57-102">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="01d57-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="01d57-103">Microsoft Windows uygulamaları genellikle görüntü, video ve ses gibi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]yürütülemeyen veriler içeren dosyalara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="01d57-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="01d57-104">Windows Sunu Temeli (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmak, tanımlamak ve kullanmak için özel destek sunar.</span><span class="sxs-lookup"><span data-stu-id="01d57-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="01d57-105">Bu destek, şular da dahil olmak üzere belirli bir uygulama veri dosyası türü kümesi etrafında döner:</span><span class="sxs-lookup"><span data-stu-id="01d57-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="01d57-106">**Kaynak Dosyaları**: Yürütülebilir veya kitaplık WPF derlemesi içine derlenen veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="01d57-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="01d57-107">**İçerik Dosyaları**: Yürütülebilir bir WPF derlemesi ile açık bir ilişkisi olan bağımsız veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="01d57-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="01d57-108">**Site of Origin Files**: Yürütülebilir bir WPF derlemesi ile ilişkisi olmayan bağımsız veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="01d57-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="01d57-109">Bu üç dosya türü arasında önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının oluşturma zamanında bilinmesidir; bir derleme onlar hakkında açık bilgiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="01d57-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="01d57-110">Ancak, kaynak dosyalarının site için, bir derleme nin bunlar hakkında hiçbir bilgisi olmayabilir veya bir paket tekdüzen kaynak tanımlayıcısı (URI) referansı aracılığıyla örtülü bilgi; ikincisi durumunda, kaynak dosyasının başvurulan site aslında var olduğunu garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="01d57-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="01d57-111">Uygulama veri dosyalarına başvurmak için, Windows Presentation Foundation (WPF), [WPF'deki Paket URI'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanan Paket üniformakaynak tanımlayıcısı (URI) Düzenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="01d57-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="01d57-112">Bu konu, uygulama veri dosyalarının nasıl yapılandırılabildiğini ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="01d57-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="01d57-113">Kaynak Dosyalar</span><span class="sxs-lookup"><span data-stu-id="01d57-113">Resource Files</span></span>  
 <span data-ttu-id="01d57-114">Bir uygulama veri dosyasının bir uygulama için her zaman kullanılabilir olması gerekiyorsa, kullanılabilirliği garanti etmenin tek yolu, dosyayı bir uygulamanın ana yürütülebilir derlemesine veya başvurulan derlemelerinden birine derlemektir.</span><span class="sxs-lookup"><span data-stu-id="01d57-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="01d57-115">Bu tür bir uygulama veri dosyası *kaynak dosyası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="01d57-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="01d57-116">Kaynak dosyalarını şu anda kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="01d57-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="01d57-117">Bir derlemeye derlendikten sonra kaynak dosyasının içeriğini güncelleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="01d57-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="01d57-118">Dosya bağımlılıklarının sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="01d57-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="01d57-119">Uygulama veri dosyanızın yerelleştirilebilir olması gerekir (bkz. [WPF Genelleştirme ve Yerelleştirme Genel Bakış).](../advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="01d57-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d57-120">Bu bölümde açıklanan kaynak dosyaları [XAML Kaynakları'nda](../../../desktop-wpf/fundamentals/xaml-resources-define.md) açıklanan kaynak dosyalarını ve Uygulama [Kaynaklarını Yönet 'de (.NET)](/visualstudio/ide/managing-application-resources-dotnet)açıklanan gömülü veya bağlantılı kaynaklardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="01d57-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="01d57-121">Kaynak Dosyalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01d57-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="01d57-122">WPF'de kaynak dosyası, microsoft yapı altyapısı (MSBuild) projesine öğe `Resource` olarak dahil edilen bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="01d57-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="01d57-123">Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` `Resource`'ye ayarlayarak bir kaynak dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="01d57-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="01d57-124">Proje oluşturulduğunda, MSBuild kaynağı derlemeye derler.</span><span class="sxs-lookup"><span data-stu-id="01d57-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="01d57-125">Kaynak Dosyalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="01d57-125">Using Resource Files</span></span>  
 <span data-ttu-id="01d57-126">Kaynak dosyasını yüklemek için, <xref:System.Windows.Application.GetResourceStream%2A> istenen kaynak <xref:System.Windows.Application> dosyasını tanımlayan bir uri paketini geçerek sınıfın yöntemini arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="01d57-127"><xref:System.Windows.Application.GetResourceStream%2A>kaynak <xref:System.Windows.Resources.StreamResourceInfo> dosyasını a olarak gösteren ve <xref:System.IO.Stream> içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="01d57-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="01d57-128">Örnek olarak, aşağıdaki <xref:System.Windows.Application.GetResourceStream%2A> kod bir <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek için nasıl kullanılacağını <xref:System.Windows.Controls.Frame> `pageFrame`gösterir ve bir ( ):</span><span class="sxs-lookup"><span data-stu-id="01d57-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="01d57-129">Arama, <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01d57-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="01d57-130">Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="01d57-131">Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="01d57-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="01d57-132">Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="01d57-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="01d57-133">Kaynak Dosyaları Olarak Uygulama Kodu Dosyaları</span><span class="sxs-lookup"><span data-stu-id="01d57-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="01d57-134">Özel bir WPF uygulama kodu dosyası kümesi, windows, sayfalar, akış belgeleri ve kaynak sözlükleri de dahil olmak üzere paket URI'leri kullanılarak başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="01d57-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="01d57-135">Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> bir uygulama başladığında yüklemek istediğiniz pencereye veya sayfaya başvurur bir URI paketiyle özelliği ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="01d57-136">Bunu, bir XAML dosyası bir MSBuild projesine `Page` öğe olarak dahil edildiğinde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="01d57-137">Visual Studio'da, bir <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>projeye <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>yeni <xref:System.Windows.ResourceDictionary> , , , `Build Action` veya bir projeye, `Page`biçimlendirme dosyası için varsayılan olarak .</span><span class="sxs-lookup"><span data-stu-id="01d57-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="01d57-138">Öğeleri olan `Page` bir proje derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler ikili biçime dönüştürülür ve ilişkili derlemeye derlenir.</span><span class="sxs-lookup"><span data-stu-id="01d57-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="01d57-139">Sonuç olarak, bu dosyalar tipik kaynak dosyalarıyla aynı şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01d57-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d57-140">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya öğe `Resource` olarak yapılandırılır ve kod arkası dosyası yoksa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham ham'ın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ikili sürümü yerine bir derleme içine derlenir.</span><span class="sxs-lookup"><span data-stu-id="01d57-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="01d57-141">İçerik Dosyaları</span><span class="sxs-lookup"><span data-stu-id="01d57-141">Content Files</span></span>  
 <span data-ttu-id="01d57-142">*İçerik dosyası,* yürütülebilir bir derlemenin yanında gevşek bir dosya olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="01d57-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="01d57-143">Derlemeye alınmasalar da derlemeler, her içerik dosyasıyla ilişki kuran meta verilerle derlenir.</span><span class="sxs-lookup"><span data-stu-id="01d57-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="01d57-144">Uygulamanız, bunları tüketen derlemeyi yeniden derlemeden güncelleştirmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="01d57-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="01d57-145">İçerik Dosyalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01d57-145">Configuring Content Files</span></span>  
 <span data-ttu-id="01d57-146">Projeye içerik dosyası eklemek için, uygulama veri dosyasının öğe `Content` olarak eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d57-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="01d57-147">Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmedığından, içerik dosyasının `CopyToOutputDirectory` yerleşik derlemeye göre bir konuma kopyalandığını belirtmek için MSBuild meta veri öğesini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d57-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="01d57-148">Bir proje her oluşturulunca kaynağın yapı çıktısı klasörüne kopyalanmasını `CopyToOutputDirectory` istiyorsanız, meta `Always` veri öğesini değerle birlikte ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="01d57-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="01d57-149">Aksi takdirde, `PreserveNewest` değeri kullanarak kaynağın yalnızca en yeni sürümünün yapı çıktısı klasörüne kopyalanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="01d57-150">Aşağıda, yalnızca kaynağın yeni bir sürümü projeye eklendiğinde yapı çıktıklasörüne kopyalanan bir içerik dosyası olarak yapılandırılan bir dosya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="01d57-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="01d57-151">Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` `Content` `Always` `Copy if newer` (aynı) ve `Copy always` (aynı) olarak ayarlayarak `Copy to Output Directory` bir içerik dosyası `PreserveNewest`oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="01d57-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="01d57-152">Proje oluşturulduğunda, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> her içerik dosyası için derlemenin meta verilerine bir öznitelik derlenir.</span><span class="sxs-lookup"><span data-stu-id="01d57-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="01d57-153">Değer, içerik <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> dosyasının projedeki konumuna göre yolu ima eder.</span><span class="sxs-lookup"><span data-stu-id="01d57-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="01d57-154">Örneğin, bir içerik dosyası bir proje alt klasöründe bulunuyorsa, ek yol <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> bilgileri değere dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="01d57-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="01d57-155">Değer, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> yapı çıktıklasöründeki içerik dosyasına giden yolun değeridir.</span><span class="sxs-lookup"><span data-stu-id="01d57-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="01d57-156">İçerik Dosyalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="01d57-156">Using Content Files</span></span>  
 <span data-ttu-id="01d57-157">İçerik dosyasını yüklemek için, <xref:System.Windows.Application.GetContentStream%2A> istenen içerik <xref:System.Windows.Application> dosyasını tanımlayan bir URI paketini geçerek sınıfın yöntemini arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="01d57-158"><xref:System.Windows.Application.GetContentStream%2A>içerik <xref:System.Windows.Resources.StreamResourceInfo> dosyasını a <xref:System.IO.Stream> olarak gösteren ve içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="01d57-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="01d57-159">Örnek olarak, aşağıdaki <xref:System.Windows.Application.GetContentStream%2A> kod bir <xref:System.Windows.Controls.Page> içerik dosyasını yüklemek için nasıl kullanılacağını <xref:System.Windows.Controls.Frame> `pageFrame`gösterir ve içeriği olarak ayarlanır ( ).</span><span class="sxs-lookup"><span data-stu-id="01d57-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="01d57-160">Arama, <xref:System.Windows.Application.GetContentStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01d57-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="01d57-161">Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="01d57-162">Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="01d57-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="01d57-163">Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="01d57-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="01d57-164">Menşe Dosyaları Sitesi</span><span class="sxs-lookup"><span data-stu-id="01d57-164">Site of Origin Files</span></span>  
 <span data-ttu-id="01d57-165">Kaynak dosyaları, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>'' nin tanımladığı şekilde, birlikte dağıtılan derlemelerle açık bir ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="01d57-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="01d57-166">Ancak, derleme ve uygulama veri dosyası arasında örtük veya var olmayan bir ilişki kurmak isteyebileceğin zamanlar vardır:</span><span class="sxs-lookup"><span data-stu-id="01d57-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="01d57-167">Derleme zamanında bir dosya yok.</span><span class="sxs-lookup"><span data-stu-id="01d57-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="01d57-168">Çalışma süresine kadar derlemenizin hangi dosyalara ihtiyaç duyacağını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="01d57-169">İlişkili oldukları derlemeyi yeniden derlemeden dosyaları güncelleştirmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="01d57-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="01d57-170">Uygulamanız ses ve video gibi büyük veri dosyaları kullanır ve kullanıcıların yalnızca istedikleri nde bunları karşıdan yüklemesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="01d57-171">Bu tür dosyaları, file:/// ve http:// düzenleri gibi geleneksel URI düzenlerini kullanarak yüklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="01d57-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="01d57-172">Ancak, file:/// ve http:// düzenleri, uygulamanızın tam güvene sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="01d57-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="01d57-173">Uygulamanız Internet veya intranet'ten başlatılan bir XAML tarayıcı uygulamasıysa (XBAP) ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izinler kümesini istiyorsa, gevşek dosyalar yalnızca uygulamanın menşe sitesi (başlatma konumu).</span><span class="sxs-lookup"><span data-stu-id="01d57-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="01d57-174">Bu tür *dosyalar, kaynak* dosyaları sitesi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="01d57-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="01d57-175">Site kaynağı dosyaları kısmi güven uygulamaları için tek seçenekolmakla birlikte, kısmi güven uygulamalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="01d57-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="01d57-176">Tam güven uygulamalarının, oluşturma zamanında bilmedikleri uygulama veri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:/// kullanabilirsiniz, ancak uygulama veri dosyaları aynı klasörde yüklü olması muhtemeldir, ya da bir alt klasörü, uygulama derleme.</span><span class="sxs-lookup"><span data-stu-id="01d57-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="01d57-177">Bu durumda, file:/// kullanmak dosyanın tam yolunu çalışmanızı gerektirdiğinden, kaynak siteye başvurmak file:/// kullanmaktan daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="01d57-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d57-178">Site kaynak dosyaları istemci makinesinde xaml tarayıcı uygulaması (XBAP) ile önbelleğe alınmaz, içerik dosyaları ise.</span><span class="sxs-lookup"><span data-stu-id="01d57-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="01d57-179">Sonuç olarak, yalnızca özel olarak istendiğinde karşıdan yüklenirler.</span><span class="sxs-lookup"><span data-stu-id="01d57-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="01d57-180">Bir XAML tarayıcı uygulaması (XBAP) uygulaması büyük medya dosyaları varsa, kaynak dosyaları sitesi olarak yapılandırılması ilk uygulama başlatma çok daha hızlı olduğu anlamına gelir ve dosyaları sadece isteğe bağlı olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="01d57-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="01d57-181">Menşe Sitesi Dosyalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01d57-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="01d57-182">Kaynak sitenizin dosyaları derleme zamanında mevcut değilse veya bilinmiyorsa, `XCopy` komut satırı programını veya Microsoft Windows Yükleyicisini kullanmak da dahil olmak üzere gerekli dosyaların çalışma zamanında kullanılabilir olmasını sağlamak için geleneksel dağıtım mekanizmalarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d57-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="01d57-183">Kaynak sitede yer almak istediğiniz dosyaları derleme saatinde biliyorsanız, ancak yine de açık bir bağımlılıktan kaçınmak istiyorsanız, bu dosyaları bir MSBuild projesine öğe olarak `None` ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="01d57-184">İçerik dosyalarında olduğu gibi, MSBuild `CopyToOutputDirectory` özniteliğini, kaynak dosyasının `Always` sitenin, değeri veya `PreserveNewest` değeri belirterek yerleşik derlemeye göre bir konuma kopyalanmış olduğunu belirtmek için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d57-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="01d57-185">Visual Studio'da, bir projeye dosya ekleyerek ve dosyayı `Build Action` 'ye `None`ayarlayarak bir kaynak dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="01d57-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="01d57-186">Proje oluşturulduğunda, MSBuild belirtilen dosyaları yapı çıktıklasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="01d57-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="01d57-187">Menşe Dosyalarının Sitesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="01d57-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="01d57-188">Bir site kaynağı dosyasını yüklemek için, istenen <xref:System.Windows.Application> kaynak dosyasını tanımlayan bir URI paketini geçerek sınıfın <xref:System.Windows.Application.GetRemoteStream%2A> yöntemini arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="01d57-189"><xref:System.Windows.Application.GetRemoteStream%2A>kaynak <xref:System.Windows.Resources.StreamResourceInfo> dosyasının sitesini a olarak gösteren ve <xref:System.IO.Stream> içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="01d57-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="01d57-190">Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Application.GetRemoteStream%2A> menşe <xref:System.Windows.Controls.Page> dosyasının bir sitenin yüklenmesi <xref:System.Windows.Controls.Frame> için`pageFrame`nasıl kullanılacağını gösterir ve bir ( ) içeriği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01d57-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="01d57-191">Arama, <xref:System.Windows.Application.GetRemoteStream%2A> <xref:System.IO.Stream>", onu ayarladığınız özellik türüne dönüştürme ek çalışmasını gerçekleştirmeniz gerekir" özelliğine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01d57-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="01d57-192">Bunun yerine, WPF'nin bir kaynak dosyasını doğrudan kod kullanarak bir türün özelliğine <xref:System.IO.Stream> yükleyerek açma ve dönüştürme yle ilgilenmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d57-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="01d57-193">Aşağıdaki örnek, kodu kullanarak <xref:System.Windows.Controls.Page> doğrudan <xref:System.Windows.Controls.Frame> a`pageFrame`( )'ye nasıl yüklenirken gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="01d57-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="01d57-194">Aşağıdaki örnek, önceki örneğin biçimlendirme eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="01d57-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="01d57-195">Yapı Türünü Değiştirdikten Sonra Yeniden Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01d57-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="01d57-196">Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, bu değişikliklerin uygulandığından emin olmak için uygulamanın tamamını yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d57-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="01d57-197">Yalnızca uygulamayı oluşturursanız, değişiklikler uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="01d57-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d57-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d57-198">See also</span></span>

- [<span data-ttu-id="01d57-199">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="01d57-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
