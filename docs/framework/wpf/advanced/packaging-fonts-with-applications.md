---
title: Uygulamalarla Yazı Tiplerini Paketleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 18a8037b6b4433a4a83860eae205174f3036d6e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005019"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="818f2-102">Uygulamalarla Yazı Tiplerini Paketleme</span><span class="sxs-lookup"><span data-stu-id="818f2-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="818f2-103">Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamanız ile yazı tiplerinin nasıl paketlenecek hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="818f2-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="818f2-104">Çoğu yazılım türünde olduğu gibi, satılan değil, yazı tipi dosyaları lisanslanır.</span><span class="sxs-lookup"><span data-stu-id="818f2-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="818f2-105">Yazı tiplerinin kullanımını yöneten lisanslar satıcıdan satıcıya farklılık gösterir, ancak Microsoft 'un uygulamalar ve Windows ile birlikte bulunan yazı tiplerini kapsaanlar da dahil olmak üzere çoğu lisans, yazı tiplerinin uygulamalara katıştırılması veya yeniden dağıtılması için izin vermez.</span><span class="sxs-lookup"><span data-stu-id="818f2-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="818f2-106">Bu nedenle, bir geliştirici olarak, bir uygulama içine eklediğiniz veya başka bir şekilde yeniden dağıtırabilmeniz gereken herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="818f2-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="818f2-107">Paketleme yazı tiplerine giriş</span><span class="sxs-lookup"><span data-stu-id="818f2-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="818f2-108">Kullanıcı arabirimi metnini ve diğer metin tabanlı içerik türlerini göstermek için, yazı tiplerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarınızın içinde kaynak olarak kolayca paketleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="818f2-109">Yazı tipleri, uygulamanın derleme dosyalarından ayrı veya katıştırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="818f2-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="818f2-110">Ayrıca, uygulamanızın başvurbileceği yalnızca kaynak yazı tipi kitaplığı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="818f2-111">OpenType ve TrueType® yazı tiplerinde yazı tipi için, yazı tipi ekleme lisanslama haklarını belirten bir tür bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="818f2-111">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="818f2-112">Ancak, bu tür bayrağı yalnızca bir belgede depolanan katıştırılmış yazı tiplerine başvurur. bir uygulamaya katıştırılmış olan yazı tiplerine başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="818f2-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="818f2-113">@No__t-0 nesnesi oluşturup <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliğine başvurarak bir yazı tipi için yazı tipi ekleme haklarını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="818f2-114">FsType bayrağı hakkında daha fazla bilgi için [OpenType belirtiminin](https://www.microsoft.com/typography/otspec/os2.htm) "OS/2 ve Windows ölçümleri" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="818f2-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="818f2-115">[Microsoft Tipografi](https://docs.microsoft.com/typography/) Web sitesi, belirli bir yazı tipi satıcısının yerini bulmanıza veya özel iş için bir yazı tipi satıcısı bulmanıza yardımcı olabilecek iletişim bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="818f2-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="818f2-116">Yazı tiplerini Içerik öğeleri olarak ekleme</span><span class="sxs-lookup"><span data-stu-id="818f2-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="818f2-117">Uygulamanıza, uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak yazı tipi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="818f2-118">Bu, içerik öğelerinin bir bütünleştirilmiş kod içinde kaynak olarak katıştırılmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="818f2-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="818f2-119">Aşağıdaki proje dosyası örneği, içerik öğelerinin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-119">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="818f2-120">Uygulamanın çalışma zamanında yazı tiplerini kullanabilmesi için, yazı tiplerinin uygulamanın dağıtım dizininde erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="818f2-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="818f2-121">Uygulamanın proje dosyasındaki `<CopyToOutputDirectory>` öğesi, derleme işlemi sırasında yazı tiplerini uygulama dağıtım dizinine otomatik olarak kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="818f2-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="818f2-122">Aşağıdaki proje dosyası örneği, yazı tiplerinin dağıtım dizinine nasıl kopyalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="818f2-123">Aşağıdaki kod örneği, uygulamanın yazı tipine içerik öğesi olarak nasıl başvurulacağını gösterir — başvurulan içerik öğesi, uygulamanın derleme dosyalarıyla aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="818f2-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="818f2-124">Yazı tiplerini kaynak öğe olarak ekleme</span><span class="sxs-lookup"><span data-stu-id="818f2-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="818f2-125">Uygulamanıza, uygulamanın derleme dosyaları içine katıştırılmış proje kaynak öğeleri olarak yazı tipi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="818f2-126">Kaynaklar için ayrı bir alt dizin kullanılması, uygulamanın proje dosyalarını düzenlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="818f2-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="818f2-127">Aşağıdaki proje dosyası örneği, yazı tiplerinin ayrı bir alt dizinde kaynak öğe olarak nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="818f2-128">Uygulamanıza kaynak olarak yazı tipi eklediğinizde, uygulamanızın proje dosyasında `<EmbeddedResource>` öğesi değil `<Resource>` öğesini ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="818f2-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="818f2-129">Derleme eyleminin `<EmbeddedResource>` öğesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="818f2-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="818f2-130">Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="818f2-131">Koddan yazı tipi kaynak öğelerine başvurma</span><span class="sxs-lookup"><span data-stu-id="818f2-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="818f2-132">Koddan yazı tipi kaynak öğelerine başvurmak için, iki bölümlü bir yazı tipi kaynak başvurusu sağlamanız gerekir: taban [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; ve yazı tipi konumu başvurusu.</span><span class="sxs-lookup"><span data-stu-id="818f2-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="818f2-133">Bu değerler <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntemi için parametreler olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="818f2-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="818f2-134">Aşağıdaki kod örneği, `resources` adlı proje alt dizinindeki uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="818f2-135">Temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], yazı tipi kaynağının bulunduğu uygulama alt dizinini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="818f2-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="818f2-136">Bu durumda, yazı tipi konumu başvurusunun bir dizin belirtmesi gerekmez, ancak yazı tipi kaynağının temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] tarafından belirtilen dizinde olduğunu gösteren önünde bir "`./`" içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="818f2-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="818f2-137">Aşağıdaki kod örneği, yazı tipi kaynak öğesine başvurmak için alternatif bir yol gösterir; önceki kod örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="818f2-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="818f2-138">Aynı uygulama alt dizininden yazı tiplerine başvurma</span><span class="sxs-lookup"><span data-stu-id="818f2-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="818f2-139">Hem uygulama içeriğini hem de kaynak dosyalarını uygulama projenizin Kullanıcı tanımlı aynı alt dizinine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="818f2-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="818f2-140">Aşağıdaki proje dosyası örneği, aynı alt dizinde tanımlanan bir içerik sayfası ve yazı tipi kaynaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="818f2-141">Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu uygulama içeriğine göre değişir.</span><span class="sxs-lookup"><span data-stu-id="818f2-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="818f2-142">Aşağıdaki örneklerde, yazı tipi uygulamayla aynı dizinde olduğunda uygulamanın yazı tipi kaynağına nasıl başvurulacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="818f2-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="818f2-143">Bir uygulamadaki yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="818f2-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="818f2-144">Yazı tiplerini uygulamanızdaki kaynak öğeleri olarak numaralandırmak için <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> veya <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="818f2-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="818f2-145">Aşağıdaki örnek, uygulama yazı tipi konumundaki <xref:System.Windows.Media.FontFamily> nesnelerinin koleksiyonunu döndürmek için <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="818f2-146">Bu durumda, uygulama "resources" adlı bir alt dizin içerir.</span><span class="sxs-lookup"><span data-stu-id="818f2-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="818f2-147">Aşağıdaki örnek, uygulama yazı tipi konumundaki <xref:System.Windows.Media.Typeface> nesnelerinin koleksiyonunu döndürmek için <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="818f2-148">Bu durumda, uygulama "resources" adlı bir alt dizin içerir.</span><span class="sxs-lookup"><span data-stu-id="818f2-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="818f2-149">Yazı tipi kaynak kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="818f2-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="818f2-150">Yalnızca yazı tiplerini içeren yalnızca kaynak kitaplığı oluşturabilirsiniz — kod, bu tür kitaplık projesi parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="818f2-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="818f2-151">Yalnızca kaynak kitaplığı oluşturma, kaynakları kullanan uygulama kodundan ayrılmış kaynaklar için ortak bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="818f2-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="818f2-152">Bu Ayrıca, kitaplık derlemesinin birden çok uygulama projesine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="818f2-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="818f2-153">Aşağıdaki proje dosyası örneği, kaynak kitaplığı projesinin önemli kısımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="818f2-154">Kaynak kitaplığındaki bir yazı tipine başvurma</span><span class="sxs-lookup"><span data-stu-id="818f2-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="818f2-155">Uygulamanızdan bir kaynak kitaplığındaki bir yazı tipine başvurmak için, yazı tipi başvurusunu kitaplık derlemesinin adı ile önekle uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="818f2-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="818f2-156">Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir.</span><span class="sxs-lookup"><span data-stu-id="818f2-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="818f2-157">Derleme adını derleme içindeki başvurudan ayırmak için '; ' karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="818f2-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="818f2-158">"Component" anahtar sözcüğünü ve ardından yazı tipi adının başvurusunu eklemek, yazı tipi kitaplığının kaynağına tam başvuruyu tamamlar.</span><span class="sxs-lookup"><span data-stu-id="818f2-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="818f2-159">Aşağıdaki kod örneği, bir kaynak kitaplığı derlemesinde bir yazı tipine nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="818f2-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="818f2-160">Bu SDK, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarıyla kullanabileceğiniz örnek bir OpenType yazı tipi kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="818f2-160">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="818f2-161">Yazı tipleri yalnızca kaynak kitaplığında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="818f2-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="818f2-162">Daha fazla bilgi için bkz. [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="818f2-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="818f2-163">Yazı tipi kullanımı sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="818f2-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="818f2-164">Aşağıdaki listede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarında yazı tiplerinin paketlenmesi ve kullanımıyla ilgili çeşitli sınırlamalar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="818f2-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="818f2-165">**Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, hiçbir yazı tipi ekleme izin bitlerini denetlemez veya zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="818f2-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="818f2-166">Daha fazla bilgi için [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="818f2-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="818f2-167">**Kaynak yazı tiplerinin sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, http veya FTP [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ' ye bir yazı tipi başvurusuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="818f2-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
- <span data-ttu-id="818f2-168">**Paketi kullanarak mutlak URI: NOTATION:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları, bir yazı tipine yönelik mutlak [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvurusunun bir parçası olarak "Pack:" kullanarak program aracılığıyla <xref:System.Windows.Media.FontFamily> nesnesi oluşturmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="818f2-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="818f2-169">Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.</span><span class="sxs-lookup"><span data-stu-id="818f2-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="818f2-170">**Otomatik yazı tipi ekleme:** Tasarım zamanı sırasında uygulamanın yazı tipi kullanımını arama ve yazı tiplerini uygulamanın kaynaklarına otomatik olarak katıştırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="818f2-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="818f2-171">**Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, sabit olmayan belgeler için yazı tipi alt kümelerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="818f2-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="818f2-172">Yanlış bir başvuru olduğu durumlarda, uygulama kullanılabilir bir yazı tipi kullanmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="818f2-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818f2-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="818f2-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="818f2-174">Microsoft Tipografi: bağlantılar, Haberler ve kişiler</span><span class="sxs-lookup"><span data-stu-id="818f2-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="818f2-175">OpenType belirtimi</span><span class="sxs-lookup"><span data-stu-id="818f2-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="818f2-176">OpenType Yazı Tipi Özellikleri</span><span class="sxs-lookup"><span data-stu-id="818f2-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="818f2-177">Örnek OpenType Yazı Tipi Paketi</span><span class="sxs-lookup"><span data-stu-id="818f2-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
