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
ms.openlocfilehash: e50f542086aadc2f61412fe409d7df0f49422718
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920370"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="fc53b-102">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fc53b-102">WPF Application Resource, Content, and Data Files</span></span>
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] <span data-ttu-id="fc53b-103">uygulamalar genellikle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], görüntüler, video ve ses gibi yürütülebilir olmayan verileri içeren dosyalara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-103">applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="fc53b-104">Windows Presentation Foundation (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmaya, tanımlamaya ve kullanmaya yönelik özel destek sunar.</span><span class="sxs-lookup"><span data-stu-id="fc53b-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="fc53b-105">Bu destek, aşağıdakiler de dahil olmak üzere belirli bir uygulama veri dosyası türü kümesinin etrafında döner:</span><span class="sxs-lookup"><span data-stu-id="fc53b-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="fc53b-106">**Kaynak dosyaları**: bir çalıştırılabilir veya kitaplık [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemesine derlenen veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="fc53b-106">**Resource Files**: Data files that are compiled into either an executable or library [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
- <span data-ttu-id="fc53b-107">**Içerik dosyaları**: çalıştırılabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bütünleştirilmiş kodu ile açık ilişkiye sahip bağımsız veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="fc53b-107">**Content Files**: Standalone data files that have an explicit association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
- <span data-ttu-id="fc53b-108">**Kaynak dosyalarının sitesi**: çalıştırılabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemesi ile ilişkisi olmayan tek başına veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="fc53b-108">**Site of Origin Files**: Standalone data files that have no association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
 <span data-ttu-id="fc53b-109">Bu üç tür Dosya arasında yapılması gereken önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının derleme zamanında bilinmesinin bir örneğidir; bir derlemenin açık bilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="fc53b-110">Ancak, kaynak dosyalarının sitesi için bir derlemenin hiç bilgisi olmayabilir veya bir paket tekdüzen kaynak tanımlayıcısı (URI) başvurusu aracılığıyla örtülü bilgi alabilir; İkinci durumda, başvurulan kaynak dosya sitesinin gerçekten var olduğu garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc53b-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="fc53b-111">Windows Presentation Foundation (WPF), uygulama veri dosyalarına başvurmak için, paket tekdüzen kaynak tanımlayıcısı (URI) şemasını kullanır ve bu, [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="fc53b-112">Bu konuda, uygulama veri dosyalarının nasıl yapılandırılacağı ve kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="fc53b-113">Kaynak Dosyalar</span><span class="sxs-lookup"><span data-stu-id="fc53b-113">Resource Files</span></span>  
 <span data-ttu-id="fc53b-114">Bir uygulama veri dosyasının her zaman bir uygulama için kullanılabilir olması gerekiyorsa, kullanılabilirliği güvence altına almanın tek yolu, uygulamayı uygulamanın ana yürütülebilir derlemesinde veya başvurulan derlemelerinden birinde derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="fc53b-115">Bu tür bir uygulama veri dosyası *kaynak dosyası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="fc53b-116">Kaynak dosyalarını şu durumlarda kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc53b-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="fc53b-117">Bir derlemeye derlendikten sonra kaynak dosyanın içeriğini güncelleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fc53b-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="fc53b-118">Dosya bağımlılıklarının sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="fc53b-119">Uygulama veri dosyanızın yerelleştirilebilir olması gerekir (bkz. [WPF Genelleştirme ve yerelleştirme genel bakış](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="fc53b-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc53b-120">Bu bölümde açıklanan kaynak dosyaları, [xaml kaynaklarında](../advanced/xaml-resources.md) açıklanan kaynak dosyalarından farklıdır ve [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet)bölümünde açıklanan katıştırılmış veya bağlı kaynaklardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-120">The resource files described in this section are different than the resource files described in [XAML Resources](../advanced/xaml-resources.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="fc53b-121">Kaynak dosyalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc53b-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="fc53b-122">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], kaynak dosyası bir Microsoft Build Engine (MSBuild) projesinde `Resource` öğesi olarak bulunan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="fc53b-123">Visual Studio 'da bir projeye dosya ekleyerek ve `Build Action` `Resource`olarak ayarlayarak bir kaynak dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="fc53b-124">Proje yapılandırıldığında, MSBuild kaynağı derlemeye derler.</span><span class="sxs-lookup"><span data-stu-id="fc53b-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="fc53b-125">Kaynak dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="fc53b-125">Using Resource Files</span></span>  
 <span data-ttu-id="fc53b-126">Bir kaynak dosyasını yüklemek için, istenen kaynak dosyasını tanımlayan bir paket URI 'sini geçirerek <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetResourceStream%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="fc53b-127"><xref:System.Windows.Application.GetResourceStream%2A>, kaynak dosyasını <xref:System.IO.Stream> olarak sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc53b-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="fc53b-128">Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetResourceStream%2A> nasıl kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="fc53b-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="fc53b-129"><xref:System.Windows.Application.GetResourceStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="fc53b-130">Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-130">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="fc53b-131">Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="fc53b-132">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="fc53b-133">Kaynak dosyaları olarak uygulama kodu dosyaları</span><span class="sxs-lookup"><span data-stu-id="fc53b-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="fc53b-134">Windows, sayfalar, Flow belgeleri ve kaynak sözlükleri dahil olmak üzere paket URI 'Leri kullanılarak özel bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama kodu dosyası kümesine başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-134">A special set of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="fc53b-135">Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özelliğini, bir uygulama başlatıldığında yüklemek istediğiniz pencere veya sayfaya başvuruda bulunan bir paket URI 'SI ile ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="fc53b-136">Bu işlemi, bir XAML dosyası `Page` öğesi olarak MSBuild projesine dahil edildiğinde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="fc53b-137">Visual Studio 'da, bir projeye yeni bir <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>veya <xref:System.Windows.ResourceDictionary> eklersiniz, biçimlendirme dosyasının `Build Action` varsayılan olarak `Page`olur.</span><span class="sxs-lookup"><span data-stu-id="fc53b-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="fc53b-138">`Page` öğeler içeren bir proje derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri ikili biçime dönüştürülür ve ilişkili derlemeye derlenir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="fc53b-139">Sonuç olarak, bu dosyalar tipik kaynak dosyalarla aynı şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc53b-140">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası `Resource` öğesi olarak yapılandırılmışsa ve arka plan kod dosyası içermiyorsa, ham [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ham [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ikili sürümü yerine bir derlemeye derlenir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="fc53b-141">İçerik dosyaları</span><span class="sxs-lookup"><span data-stu-id="fc53b-141">Content Files</span></span>  
 <span data-ttu-id="fc53b-142">Bir *içerik dosyası* , yürütülebilir bir bütünleştirilmiş kod ile gevşek bir dosya olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="fc53b-143">Derlemeler bir derlemeye derlenmese de, derlemeler her bir içerik dosyasıyla bir ilişki kuran meta veriler ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="fc53b-144">Uygulamanız, kendisini kullanan derlemeyi yeniden derlemeden güncelleştirebilmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="fc53b-145">Içerik dosyalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc53b-145">Configuring Content Files</span></span>  
 <span data-ttu-id="fc53b-146">Bir projeye içerik dosyası eklemek için, bir uygulama veri dosyası `Content` öğesi olarak eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="fc53b-147">Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmediğinden, içerik dosyasının oluşturulan derlemeye göre bir konuma kopyalanacağını belirtmek için MSBuild `CopyToOutputDirectory` meta veri öğesini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="fc53b-148">Bir proje oluşturulduğunda kaynağın yapı çıkış klasörüne kopyalanmasını isterseniz, `CopyToOutputDirectory` meta veri öğesini `Always` değeri ile ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="fc53b-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="fc53b-149">Aksi takdirde, `PreserveNewest` değerini kullanarak yalnızca kaynağın en yeni sürümünün derleme çıkış klasörüne kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="fc53b-150">Aşağıda, yalnızca kaynağın yeni bir sürümü projeye eklendiğinde derleme çıkış klasörüne kopyalanmış bir içerik dosyası olarak yapılandırılmış bir dosya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="fc53b-151">Visual Studio 'da, bir projeye dosya ekleyip `Build Action` `Content`ve `Copy to Output Directory` `Copy always` (`Always`ile aynı) ve `Copy if newer` (`PreserveNewest`ile aynı) olarak ayarlayarak bir içerik dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="fc53b-152">Proje yapılandırıldığında, her içerik dosyası için derlemenin meta verilerine bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği derlenir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="fc53b-153"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri, projedeki konumuna göre içerik dosyasının yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="fc53b-154">Örneğin, bir proje alt klasöründe bir içerik dosyası bulunuyorsa, ek yol bilgileri <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değerine dahil olur.</span><span class="sxs-lookup"><span data-stu-id="fc53b-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="fc53b-155"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> değeri aynı zamanda yapı çıkış klasöründeki içerik dosyası yolunun değeridir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="fc53b-156">Içerik dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="fc53b-156">Using Content Files</span></span>  
 <span data-ttu-id="fc53b-157">Bir içerik dosyasını yüklemek için, istenen içerik dosyasını tanımlayan bir paket URI 'sini geçirerek <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetContentStream%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="fc53b-158"><xref:System.Windows.Application.GetContentStream%2A>, içerik dosyasını <xref:System.IO.Stream> olarak sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc53b-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="fc53b-159">Örnek olarak, aşağıdaki kod, <xref:System.Windows.Controls.Page> bir içerik dosyası yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetContentStream%2A> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="fc53b-160"><xref:System.Windows.Application.GetContentStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="fc53b-161">Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-161">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="fc53b-162">Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="fc53b-163">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="fc53b-164">Kaynak dosyalarının sitesi</span><span class="sxs-lookup"><span data-stu-id="fc53b-164">Site of Origin Files</span></span>  
 <span data-ttu-id="fc53b-165">Kaynak dosyaları, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> tarafından tanımlandığı şekilde, birlikte dağıtılabilecek Derlemelerle açık bir ilişkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="fc53b-166">Ancak, aşağıdakiler de dahil olmak üzere bir derleme ve uygulama veri dosyası arasında örtük veya mevcut olmayan bir ilişki oluşturmak isteyebileceğiniz durumlar vardır:</span><span class="sxs-lookup"><span data-stu-id="fc53b-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="fc53b-167">Derleme zamanında bir dosya yok.</span><span class="sxs-lookup"><span data-stu-id="fc53b-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="fc53b-168">Çalışma zamanına kadar derlemelerinizin hangi dosyaları gerektirdiğini bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="fc53b-169">Dosyaları, ilişkilendirildikleri derlemeyi yeniden derlemeden güncelleştirebilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="fc53b-170">Uygulamanız, ses ve video gibi büyük veri dosyalarını kullanır ve yalnızca tercih ettikleri takdirde kullanıcıların bunları indirmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="fc53b-171">Bu dosya türlerini, file:///ve http://şemaları gibi geleneksel URI düzenlerini kullanarak yüklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fc53b-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="fc53b-172">Ancak, file:///ve http://şemaları uygulamanızın tam güvene sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="fc53b-173">Uygulamanız Internet 'ten veya intranetten başlatılan bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izin kümesini isterse, gevşek dosyalar yalnızca uygulamanın kaynak sitesinden yüklenebilir ( başlatma konumu).</span><span class="sxs-lookup"><span data-stu-id="fc53b-173">If your application is a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="fc53b-174">Bu tür dosyalar, *kaynak dosyalarının sitesi* olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="fc53b-175">Kaynak dosyalarının sitesi kısmi güven uygulamaları için tek seçenektir, ancak kısmi güven uygulamalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="fc53b-176">Tam güven uygulamalarının, derleme zamanında hakkında bilgi sahibi olmadıkları uygulama verileri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:///kullanabilir, ancak uygulama veri dosyalarının uygulama bütünleştirilmiş kodu ile aynı klasöre veya bir alt klasörüne yüklenebileceği olasıdır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="fc53b-177">Bu durumda, file:///kullanımı, dosyanın tam yolunu kullanmanızı gerektirdiğinden, kaynak başvuru sitesinin file:///kullanmaktan daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc53b-178">Kaynak dosyalarının sitesi, istemci makinesindeki bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] önbelleğe alınmaz, ancak içerik dosyaları vardır.</span><span class="sxs-lookup"><span data-stu-id="fc53b-178">Site of origin files are not cached with an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] on a client machine, while content files are.</span></span> <span data-ttu-id="fc53b-179">Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="fc53b-180">Bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] uygulamasının büyük medya dosyaları varsa, bunları kaynak dosyaları sitesi olarak yapılandırmak, ilk uygulama başlatma işlemi çok daha hızlıdır ve dosyalar yalnızca isteğe bağlı olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-180">If an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="fc53b-181">Kaynak dosyalarının sitesini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc53b-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="fc53b-182">Kaynak dosyaları siteniz derleme sırasında mevcut değilse veya bilinmiyorsa, gerekli dosyaların `XCopy` komut satırı programını veya [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)]kullanma dahil olmak üzere çalışma zamanında kullanılabilir olmasını sağlamak için geleneksel dağıtım mekanizmalarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span></span>  
  
 <span data-ttu-id="fc53b-183">Derleme zamanında, kaynak sitesinde bulunmasını istediğiniz dosyaları öğrenseniz, ancak yine de açık bir bağımlılığı önlemek istiyorsanız, bu dosyaları bir MSBuild projesine `None` öğesi olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="fc53b-184">İçerik dosyalarında olduğu gibi, kaynak dosya sitesinin, `Always` değerini veya `PreserveNewest` değerini belirterek oluşturulan derlemeye göreli bir konuma kopyalandığını belirtmek için MSBuild `CopyToOutputDirectory` özniteliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="fc53b-185">Visual Studio 'da bir projeye dosya ekleyip `Build Action` `None`olarak ayarlayarak kaynak dosyanın bir sitesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc53b-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="fc53b-186">Proje yapılandırıldığında, MSBuild belirtilen dosyaları yapı çıkış klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="fc53b-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="fc53b-187">Kaynak dosyalarının sitesini kullanma</span><span class="sxs-lookup"><span data-stu-id="fc53b-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="fc53b-188">Kaynak dosyasının bir sitesini yüklemek için, <xref:System.Windows.Application> sınıfının <xref:System.Windows.Application.GetRemoteStream%2A> yöntemini çağırıp, istenen kaynak dosyası sitesini tanımlayan bir paket URI 'SI geçirilerek.</span><span class="sxs-lookup"><span data-stu-id="fc53b-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="fc53b-189"><xref:System.Windows.Application.GetRemoteStream%2A>, kaynak dosyasının sitesini bir <xref:System.IO.Stream> olarak kullanıma sunan ve içerik türünü açıklayan bir <xref:System.Windows.Resources.StreamResourceInfo> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc53b-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="fc53b-190">Örnek olarak, aşağıdaki kod, kaynak dosyanın <xref:System.Windows.Controls.Page> bir sitesini yüklemek ve bir <xref:System.Windows.Controls.Frame> (`pageFrame`) içeriği olarak ayarlamak için <xref:System.Windows.Application.GetRemoteStream%2A> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="fc53b-191"><xref:System.Windows.Application.GetRemoteStream%2A> çağırırken <xref:System.IO.Stream>erişim sağlar. bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="fc53b-192">Bunun yerine, bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek <xref:System.IO.Stream> açıp dönüştürmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-192">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="fc53b-193">Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Controls.Page> doğrudan bir <xref:System.Windows.Controls.Frame> (`pageFrame`) nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="fc53b-194">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="fc53b-195">Derleme türünü değiştirdikten sonra yeniden oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc53b-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="fc53b-196">Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, değişikliklerin uygulandığından emin olmak için tüm uygulamayı yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc53b-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="fc53b-197">Yalnızca uygulamayı oluşturuyorsanız, değişiklikler uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc53b-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc53b-198">See also</span></span>

- [<span data-ttu-id="fc53b-199">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="fc53b-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
