---
title: Uygulama kaynağı, Içerik ve veri dosyaları
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
ms.openlocfilehash: 19cb530fc5c70df3a7af7ac41836b3dfd97594e9
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144818"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="2acc4-102">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2acc4-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="2acc4-103">Microsoft Windows uygulamaları genellikle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , görüntü, video ve ses gibi yürütülebilir olmayan verileri içeren dosyalara bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="2acc4-104">Windows Presentation Foundation (WPF), uygulama veri dosyaları olarak adlandırılan bu tür veri dosyalarını yapılandırmaya, tanımlamaya ve kullanmaya yönelik özel destek sunar.</span><span class="sxs-lookup"><span data-stu-id="2acc4-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="2acc4-105">Bu destek, aşağıdakiler de dahil olmak üzere belirli bir uygulama veri dosyası türü kümesinin etrafında döner:</span><span class="sxs-lookup"><span data-stu-id="2acc4-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="2acc4-106">**Kaynak dosyaları**: çalıştırılabilir veya kitaplık WPF derlemesinde derlenen veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2acc4-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="2acc4-107">**Içerik dosyaları**: YÜRÜTÜLEBILIR bir WPF derlemesiyle açık bir ilişkisi olan tek başına veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2acc4-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="2acc4-108">**Kaynak dosyalarının sitesi**: YÜRÜTÜLEBILIR bir WPF derlemesiyle ilişkisi olmayan tek başına veri dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2acc4-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="2acc4-109">Bu üç tür Dosya arasında yapılması gereken önemli bir ayrım, kaynak dosyalarının ve içerik dosyalarının derleme zamanında bilinmesinin bir örneğidir; bir derlemenin açık bilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="2acc4-110">Ancak, kaynak dosyalarının sitesi için bir derlemenin hiç bilgisi olmayabilir veya bir paket tekdüzen kaynak tanımlayıcısı (URI) başvurusu aracılığıyla örtülü bilgi alabilir; İkinci durumda, başvurulan kaynak dosya sitesinin gerçekten var olduğu garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="2acc4-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="2acc4-111">Windows Presentation Foundation (WPF), uygulama veri dosyalarına başvurmak için, paket tekdüzen kaynak tanımlayıcısı (URI) şemasını kullanır ve bu, [WPF 'de paket URI 'lerinde](pack-uris-in-wpf.md)ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="2acc4-112">Bu konuda, uygulama veri dosyalarının nasıl yapılandırılacağı ve kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="2acc4-113">Kaynak Dosyalar</span><span class="sxs-lookup"><span data-stu-id="2acc4-113">Resource Files</span></span>  
 <span data-ttu-id="2acc4-114">Bir uygulama veri dosyasının her zaman bir uygulama için kullanılabilir olması gerekiyorsa, kullanılabilirliği güvence altına almanın tek yolu, uygulamayı uygulamanın ana yürütülebilir derlemesinde veya başvurulan derlemelerinden birinde derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="2acc4-115">Bu tür bir uygulama veri dosyası *kaynak dosyası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="2acc4-116">Kaynak dosyalarını şu durumlarda kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2acc4-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="2acc4-117">Bir derlemeye derlendikten sonra kaynak dosyanın içeriğini güncelleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2acc4-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="2acc4-118">Dosya bağımlılıklarının sayısını azaltarak uygulama dağıtım karmaşıklığını basitleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="2acc4-119">Uygulama veri dosyanızın yerelleştirilebilir olması gerekir (bkz. [WPF Genelleştirme ve yerelleştirme genel bakış](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="2acc4-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2acc4-120">Bu bölümde açıklanan kaynak dosyaları, [xaml kaynaklarında](../../../desktop-wpf/fundamentals/xaml-resources-define.md) açıklanan kaynak dosyalarından farklıdır ve [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet)bölümünde açıklanan katıştırılmış veya bağlı kaynaklardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="2acc4-121">Kaynak dosyalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2acc4-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="2acc4-122">WPF 'de, kaynak dosyası bir Microsoft Build Engine (MSBuild) projesinde öğe olarak bulunan bir dosyadır `Resource` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="2acc4-123">Visual Studio 'da bir projeye dosya ekleyerek ve öğesini olarak ayarlayarak bir kaynak dosyası oluşturursunuz `Build Action` `Resource` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="2acc4-124">Proje yapılandırıldığında, MSBuild kaynağı derlemeye derler.</span><span class="sxs-lookup"><span data-stu-id="2acc4-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="2acc4-125">Kaynak dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="2acc4-125">Using Resource Files</span></span>  
 <span data-ttu-id="2acc4-126">Bir kaynak dosyasını yüklemek için, <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.Windows.Application> istenen kaynak dosyasını tanımlayan BIR paket URI 'sini geçirerek sınıfının yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="2acc4-127"><xref:System.Windows.Application.GetResourceStream%2A><xref:System.Windows.Resources.StreamResourceInfo>kaynak dosyasını bir olarak kullanıma sunan <xref:System.IO.Stream> ve içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="2acc4-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2acc4-128">Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.Windows.Controls.Page> kaynak dosyasını yüklemek ve bir () içeriği olarak ayarlamak için nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Frame> `pageFrame` :</span><span class="sxs-lookup"><span data-stu-id="2acc4-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="2acc4-129">Çağırma sırasında <xref:System.Windows.Application.GetResourceStream%2A> öğesine erişiminizi sağlar <xref:System.IO.Stream> . bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2acc4-130">Bunun yerine, <xref:System.IO.Stream> bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek, WPF 'in açma ve dönüştürme işlemini gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2acc4-131">Aşağıdaki örnek, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> kod kullanarak doğrudan bir () ' a nasıl yükleneceğini gösterir `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="2acc4-132">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="2acc4-133">Kaynak dosyaları olarak uygulama kodu dosyaları</span><span class="sxs-lookup"><span data-stu-id="2acc4-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="2acc4-134">Windows, sayfalar, Flow belgeleri ve kaynak sözlükleri dahil olmak üzere paket URI 'Leri kullanılarak özel bir WPF uygulama kodu dosyaları kümesine başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="2acc4-135">Örneğin, <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> özelliğini bir uygulama başlatıldığında yüklemek istediğiniz pencereye veya sayfaya başvuruda bulunan bir paket URI 'si ile ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="2acc4-136">Bir XAML dosyası bir MSBuild projesine öğe olarak dahil edildiğinde bunu yapabilirsiniz `Page` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="2acc4-137">Visual Studio 'da, bir projeye yeni,,, <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow> , ya da eklersiniz <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.ResourceDictionary> , `Build Action` biçimlendirme dosyası için varsayılan olarak olur `Page` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="2acc4-138">Öğeler içeren bir proje `Page` derlendiğinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler ikili biçime dönüştürülür ve ilişkili derlemeye derlenir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="2acc4-139">Sonuç olarak, bu dosyalar tipik kaynak dosyalarla aynı şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2acc4-140">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya bir öğe olarak yapılandırıldıysa `Resource` ve arka plan kod dosyasına sahip değilse, RAW, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Ham dosyanın ikili sürümü yerine bir derlemeye derlenir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2acc4-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="2acc4-141">İçerik dosyaları</span><span class="sxs-lookup"><span data-stu-id="2acc4-141">Content Files</span></span>  
 <span data-ttu-id="2acc4-142">Bir *içerik dosyası* , yürütülebilir bir bütünleştirilmiş kod ile gevşek bir dosya olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="2acc4-143">Derlemeler bir derlemeye derlenmese de, derlemeler her bir içerik dosyasıyla bir ilişki kuran meta veriler ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="2acc4-144">Uygulamanız, kendisini kullanan derlemeyi yeniden derlemeden güncelleştirebilmek istediğiniz belirli bir uygulama veri dosyaları kümesi gerektirdiğinde içerik dosyalarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="2acc4-145">Içerik dosyalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2acc4-145">Configuring Content Files</span></span>  
 <span data-ttu-id="2acc4-146">Bir projeye içerik dosyası eklemek için, bir uygulama veri dosyası bir öğe olarak dahil olmalıdır `Content` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="2acc4-147">Ayrıca, bir içerik dosyası doğrudan derlemeye derlenmediği `CopyToOutputDirectory` için, içerik dosyasının oluşturulan derlemeye göreli bir konuma kopyalanacağını belirtmek Için MSBuild meta verileri öğesini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="2acc4-148">Bir proje oluşturulduğunda kaynağın yapı çıkış klasörüne kopyalanmasını isterseniz, `CopyToOutputDirectory` meta veri öğesini değeri ile ayarlarsınız `Always` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="2acc4-149">Aksi takdirde, yalnızca kaynağın en yeni sürümünün, değeri kullanılarak derleme çıkış klasörüne kopyalandığından emin olabilirsiniz `PreserveNewest` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="2acc4-150">Aşağıda, yalnızca kaynağın yeni bir sürümü projeye eklendiğinde derleme çıkış klasörüne kopyalanmış bir içerik dosyası olarak yapılandırılmış bir dosya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="2acc4-151">Visual Studio 'da, bir projeye bir dosya ekleyerek ve öğesini olarak ayarlayarak ve (ile aynı) `Build Action` `Content` `Copy to Output Directory` `Copy always` `Always` ve `Copy if newer` (ile aynı `PreserveNewest` ) olarak ayarlayarak bir içerik dosyası oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="2acc4-152">Proje yapılandırıldığında, bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> öznitelik her içerik dosyası için derlemenin meta verilerine derlenir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="2acc4-153">Öğesinin değeri, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> projedeki konumuna göre içerik dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="2acc4-154">Örneğin, bir proje alt klasöründe bir içerik dosyası bulunuyorsa, ek yol bilgileri bu değere dahil olur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2acc4-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="2acc4-155"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>Değer aynı zamanda yapı çıkış klasöründeki içerik dosyası yolunun değeridir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="2acc4-156">Içerik dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="2acc4-156">Using Content Files</span></span>  
 <span data-ttu-id="2acc4-157">Bir içerik dosyasını yüklemek için, <xref:System.Windows.Application.GetContentStream%2A> <xref:System.Windows.Application> istenen içerik dosyasını tanımlayan BIR paket URI 'sini geçirerek sınıfının yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="2acc4-158"><xref:System.Windows.Application.GetContentStream%2A><xref:System.Windows.Resources.StreamResourceInfo>içerik dosyasını bir olarak kullanıma sunan <xref:System.IO.Stream> ve içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="2acc4-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2acc4-159">Örnek olarak, aşağıdaki kod, bir <xref:System.Windows.Application.GetContentStream%2A> <xref:System.Windows.Controls.Page> içerik dosyasını yüklemek ve bir () içeriği olarak ayarlamak için kullanımını gösterir <xref:System.Windows.Controls.Frame> `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="2acc4-160">Çağırma sırasında <xref:System.Windows.Application.GetContentStream%2A> öğesine erişiminizi sağlar <xref:System.IO.Stream> . bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2acc4-161">Bunun yerine, <xref:System.IO.Stream> bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek, WPF 'in açma ve dönüştürme işlemini gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2acc4-162">Aşağıdaki örnek, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> kod kullanarak doğrudan bir () ' a nasıl yükleneceğini gösterir `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="2acc4-163">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="2acc4-164">Kaynak dosyalarının sitesi</span><span class="sxs-lookup"><span data-stu-id="2acc4-164">Site of Origin Files</span></span>  
 <span data-ttu-id="2acc4-165">Kaynak dosyaları, tarafından tanımlandığı gibi, birlikte dağıtılabilecek Derlemelerle açık bir ilişkiye sahiptir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2acc4-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="2acc4-166">Ancak, aşağıdakiler de dahil olmak üzere bir derleme ve uygulama veri dosyası arasında örtük veya mevcut olmayan bir ilişki oluşturmak isteyebileceğiniz durumlar vardır:</span><span class="sxs-lookup"><span data-stu-id="2acc4-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="2acc4-167">Derleme zamanında bir dosya yok.</span><span class="sxs-lookup"><span data-stu-id="2acc4-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="2acc4-168">Çalışma zamanına kadar derlemelerinizin hangi dosyaları gerektirdiğini bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="2acc4-169">Dosyaları, ilişkilendirildikleri derlemeyi yeniden derlemeden güncelleştirebilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="2acc4-170">Uygulamanız, ses ve video gibi büyük veri dosyalarını kullanır ve yalnızca tercih ettikleri takdirde kullanıcıların bunları indirmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="2acc4-171">Ve şemaları gibi geleneksel URI düzenlerini kullanarak bu tür dosyaları yüklemek mümkündür `file:///` `http://` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-171">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="2acc4-172">Ancak, `file:///` ve `http://` şemaları uygulamanızın tam güvene sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-172">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="2acc4-173">Uygulamanız Internet 'ten veya intranetten başlatılan bir XAML tarayıcı uygulaması (XBAP) ise ve yalnızca bu konumlardan başlatılan uygulamalar için izin verilen izin kümesini isterse, gevşek dosyalar yalnızca uygulamanın kaynak sitesinden (başlatma konumu) yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="2acc4-174">Bu tür dosyalar, *kaynak dosyalarının sitesi* olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="2acc4-175">Kaynak dosyalarının sitesi kısmi güven uygulamaları için tek seçenektir, ancak kısmi güven uygulamalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="2acc4-176">Tam güven uygulamalarının, derleme zamanında hakkında bilgi sahibi olmadıkları uygulama verileri dosyalarını yüklemesi gerekebilir; tam güven uygulamaları file:///kullanabilir, ancak uygulama veri dosyalarının uygulama bütünleştirilmiş kodu ile aynı klasöre veya bir alt klasörüne yüklenebileceği olasıdır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="2acc4-177">Bu durumda, file:///kullanımı, dosyanın tam yolunu kullanmanızı gerektirdiğinden, kaynak başvuru sitesinin file:///kullanmaktan daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2acc4-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2acc4-178">Kaynak dosyalarının sitesi, istemci makinesindeki bir XAML tarayıcı uygulaması (XBAP) ile önbelleğe alınmaz, ancak içerik dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2acc4-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="2acc4-179">Sonuç olarak, bunlar yalnızca özellikle istendiğinde indirilir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="2acc4-180">Bir XAML tarayıcı uygulaması (XBAP) uygulamasının büyük medya dosyaları varsa, bunları kaynak dosyaları sitesi olarak yapılandırmak, ilk uygulama başlatma işlemi çok daha hızlıdır ve dosyalar yalnızca isteğe bağlı olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="2acc4-181">Kaynak dosyalarının sitesini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2acc4-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="2acc4-182">Kaynak dosyaları sitenizin derleme sırasında var olmayan veya bilinmeyen olması halinde, gerekli dosyaların çalışma zamanında kullanılabilir olmasını sağlamak için, `XCopy` komut satırı programını veya Microsoft Windows Installer kullanma da dahil olmak üzere geleneksel dağıtım mekanizmalarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="2acc4-183">Derleme zamanında, kaynak sitesinde bulunmasını istediğiniz dosyaları öğrenseniz, ancak yine de açık bir bağımlılığı önlemek istiyorsanız, bu dosyaları öğe olarak bir MSBuild projesine ekleyebilirsiniz `None` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="2acc4-184">İçerik dosyalarında olduğu gibi, `CopyToOutputDirectory` kaynak dosya sitesinin, `Always` değer veya değer belirterek oluşturulan derlemeye göreli bir konuma kopyalandığını belirtmek için MSBuild özniteliğini ayarlamanız gerekir `PreserveNewest` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="2acc4-185">Visual Studio 'da, bir projeye dosya ekleyerek ve öğesini olarak ayarlayarak kaynak dosyanın bir sitesini oluşturursunuz `Build Action` `None` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="2acc4-186">Proje yapılandırıldığında, MSBuild belirtilen dosyaları yapı çıkış klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2acc4-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="2acc4-187">Kaynak dosyalarının sitesini kullanma</span><span class="sxs-lookup"><span data-stu-id="2acc4-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="2acc4-188">Kaynak dosyasının bir sitesini yüklemek için, <xref:System.Windows.Application.GetRemoteStream%2A> <xref:System.Windows.Application> kaynak dosyanın istenen sitesini tanımlayan BIR paket URI 'sini geçirerek sınıfının yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="2acc4-189"><xref:System.Windows.Application.GetRemoteStream%2A><xref:System.Windows.Resources.StreamResourceInfo>kaynak dosyanın sitesini bir olarak kullanıma sunan <xref:System.IO.Stream> ve içerik türünü açıklayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="2acc4-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2acc4-190">Örnek olarak, aşağıdaki kod, <xref:System.Windows.Application.GetRemoteStream%2A> <xref:System.Windows.Controls.Page> kaynak dosyanın bir sitesini yüklemek ve bir () içeriği olarak ayarlamak için kullanımını gösterir <xref:System.Windows.Controls.Frame> `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="2acc4-191">Çağırma sırasında <xref:System.Windows.Application.GetRemoteStream%2A> öğesine erişiminizi sağlar <xref:System.IO.Stream> . bunu, ile ayarladığınız özelliğin türüne dönüştürmek için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2acc4-192">Bunun yerine, <xref:System.IO.Stream> bir kaynak dosyasını doğrudan kod kullanarak bir tür özelliğine yükleyerek, WPF 'in açma ve dönüştürme işlemini gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2acc4-193">Aşağıdaki örnek, <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> kod kullanarak doğrudan bir () ' a nasıl yükleneceğini gösterir `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="2acc4-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="2acc4-194">Aşağıdaki örnek, önceki örnekteki biçimlendirme eşdeğerini örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="2acc4-195">Derleme türünü değiştirdikten sonra yeniden oluşturma</span><span class="sxs-lookup"><span data-stu-id="2acc4-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="2acc4-196">Bir uygulama veri dosyasının yapı türünü değiştirdikten sonra, değişikliklerin uygulandığından emin olmak için tüm uygulamayı yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acc4-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="2acc4-197">Yalnızca uygulamayı oluşturuyorsanız, değişiklikler uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acc4-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2acc4-198">See also</span></span>

- [<span data-ttu-id="2acc4-199">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="2acc4-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
