---
title: Uygulamalarla Yazı Tiplerini Paketleme
description: Yazı tiplerini içerik ve kaynak öğeleri olarak ekleme ve yazı tipi kullanımı sınırları gibi Windows Presentation Foundation bir uygulamayla nasıl paketleyeceğinizi öğrenin.
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
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166360"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="643d9-103">Uygulamalarla Yazı Tiplerini Paketleme</span><span class="sxs-lookup"><span data-stu-id="643d9-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="643d9-104">Bu konu, yazı tiplerinin uygulamanıza nasıl paketlenecek hakkında genel bakış sağlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="643d9-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="643d9-105">Çoğu yazılım türünde olduğu gibi, satılan değil, yazı tipi dosyaları lisanslanır.</span><span class="sxs-lookup"><span data-stu-id="643d9-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="643d9-106">Yazı tiplerinin kullanımını yöneten lisanslar satıcıdan satıcıya farklılık gösterir, ancak Microsoft 'un uygulamalar ve Windows ile birlikte bulunan yazı tiplerini kapsaanlar da dahil olmak üzere çoğu lisans, yazı tiplerinin uygulamalara katıştırılması veya yeniden dağıtılması için izin vermez.</span><span class="sxs-lookup"><span data-stu-id="643d9-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="643d9-107">Bu nedenle, bir geliştirici olarak, bir uygulama içine eklediğiniz veya başka bir şekilde yeniden dağıtırabilmeniz gereken herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="643d9-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="643d9-108">Paketleme yazı tiplerine giriş</span><span class="sxs-lookup"><span data-stu-id="643d9-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="643d9-109">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Kullanıcı arabirimi metnini ve diğer metin tabanlı içerik türlerini görüntüleyecek şekilde, yazı tiplerini uygulamalarınızdaki kaynaklar olarak kolayca paketleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643d9-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="643d9-110">Yazı tipleri, uygulamanın derleme dosyalarından ayrı veya katıştırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="643d9-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="643d9-111">Ayrıca, uygulamanızın başvurbileceği yalnızca kaynak yazı tipi kitaplığı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643d9-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="643d9-112">OpenType ve TrueType® yazı tiplerinde yazı tipi için, yazı tipi ekleme lisanslama haklarını belirten bir tür bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="643d9-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="643d9-113">Ancak, bu tür bayrağı yalnızca bir belgede depolanan katıştırılmış yazı tiplerine başvurur. bir uygulamaya katıştırılmış olan yazı tiplerine başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="643d9-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="643d9-114">Bir <xref:System.Windows.Media.GlyphTypeface> nesne oluşturarak ve özelliğine başvurarak bir yazı tipi için yazı tipi ekleme haklarını alabilirsiniz <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> .</span><span class="sxs-lookup"><span data-stu-id="643d9-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="643d9-115">FsType bayrağı hakkında daha fazla bilgi için [OpenType belirtiminin](https://www.microsoft.com/typography/otspec/os2.htm) "OS/2 ve Windows ölçümleri" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="643d9-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="643d9-116">[Microsoft Tipografi](https://docs.microsoft.com/typography/) Web sitesi, belirli bir yazı tipi satıcısının yerini bulmanıza veya özel iş için bir yazı tipi satıcısı bulmanıza yardımcı olabilecek iletişim bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="643d9-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="643d9-117">Yazı tiplerini Içerik öğeleri olarak ekleme</span><span class="sxs-lookup"><span data-stu-id="643d9-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="643d9-118">Uygulamanıza, uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak yazı tipi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643d9-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="643d9-119">Bu, içerik öğelerinin bir bütünleştirilmiş kod içinde kaynak olarak katıştırılmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="643d9-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="643d9-120">Aşağıdaki proje dosyası örneği, içerik öğelerinin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-120">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="643d9-121">Uygulamanın çalışma zamanında yazı tiplerini kullanabilmesi için, yazı tiplerinin uygulamanın dağıtım dizininde erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="643d9-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="643d9-122">`<CopyToOutputDirectory>`Uygulamanın proje dosyasındaki öğesi, derleme işlemi sırasında yazı tiplerini uygulama dağıtım dizinine otomatik olarak kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="643d9-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="643d9-123">Aşağıdaki proje dosyası örneği, yazı tiplerinin dağıtım dizinine nasıl kopyalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="643d9-124">Aşağıdaki kod örneği, uygulamanın yazı tipine içerik öğesi olarak nasıl başvurulacağını gösterir — başvurulan içerik öğesi, uygulamanın derleme dosyalarıyla aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="643d9-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="643d9-125">Yazı tiplerini kaynak öğe olarak ekleme</span><span class="sxs-lookup"><span data-stu-id="643d9-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="643d9-126">Uygulamanıza, uygulamanın derleme dosyaları içine katıştırılmış proje kaynak öğeleri olarak yazı tipi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643d9-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="643d9-127">Kaynaklar için ayrı bir alt dizin kullanılması, uygulamanın proje dosyalarını düzenlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="643d9-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="643d9-128">Aşağıdaki proje dosyası örneği, yazı tiplerinin ayrı bir alt dizinde kaynak öğe olarak nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="643d9-129">Uygulamanıza kaynak olarak yazı tipi eklediğinizde, `<Resource>` uygulamanızın proje dosyasındaki öğesini değil, öğesini ayarladığınızdan emin olun `<EmbeddedResource>` .</span><span class="sxs-lookup"><span data-stu-id="643d9-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="643d9-130">`<EmbeddedResource>`Derleme eyleminin öğesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="643d9-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="643d9-131">Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="643d9-132">Koddan yazı tipi kaynak öğelerine başvurma</span><span class="sxs-lookup"><span data-stu-id="643d9-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="643d9-133">Koddan yazı tipi kaynak öğelerine başvurmak için, iki bölümlü bir yazı tipi kaynak başvurusu sağlamanız gerekir: Temel Tekdüzen Kaynak tanımlayıcısı (URI); ve yazı tipi konumu başvurusu.</span><span class="sxs-lookup"><span data-stu-id="643d9-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="643d9-134">Bu değerler, yöntemi için parametreler olarak kullanılır <xref:System.Windows.Media.FontFamily.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="643d9-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="643d9-135">Aşağıdaki kod örneği, adlı proje alt dizinindeki uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir `resources` .</span><span class="sxs-lookup"><span data-stu-id="643d9-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="643d9-136">Temel Tekdüzen Kaynak tanımlayıcısı (URI), yazı tipi kaynağının bulunduğu uygulama alt dizinini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="643d9-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="643d9-137">Bu durumda, yazı tipi konumu başvurusunun bir dizin belirtmesi gerekmez, ancak `./` yazı tipi kaynağının Temel Tekdüzen Kaynak tanımlayıcısı (URI) tarafından belirtilen dizinde olduğunu belirten önünde bir "" içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="643d9-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="643d9-138">Aşağıdaki kod örneği, yazı tipi kaynak öğesine başvurmak için alternatif bir yol gösterir; önceki kod örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="643d9-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="643d9-139">Aynı uygulama alt dizininden yazı tiplerine başvurma</span><span class="sxs-lookup"><span data-stu-id="643d9-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="643d9-140">Hem uygulama içeriğini hem de kaynak dosyalarını uygulama projenizin Kullanıcı tanımlı aynı alt dizinine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643d9-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="643d9-141">Aşağıdaki proje dosyası örneği, aynı alt dizinde tanımlanan bir içerik sayfası ve yazı tipi kaynaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="643d9-142">Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu uygulama içeriğine göre değişir.</span><span class="sxs-lookup"><span data-stu-id="643d9-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="643d9-143">Aşağıdaki örneklerde, yazı tipi uygulamayla aynı dizinde olduğunda uygulamanın yazı tipi kaynağına nasıl başvurulacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="643d9-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="643d9-144">Bir uygulamadaki yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="643d9-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="643d9-145">Yazı tiplerini uygulamanızdaki kaynak öğeleri olarak numaralandırmak için <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> ya da <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="643d9-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="643d9-146">Aşağıdaki örnek, <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> <xref:System.Windows.Media.FontFamily> uygulama yazı tipi konumundan nesne koleksiyonunu döndürmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="643d9-147">Bu durumda, uygulama "resources" adlı bir alt dizin içerir.</span><span class="sxs-lookup"><span data-stu-id="643d9-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="643d9-148">Aşağıdaki örnek, <xref:System.Windows.Media.Fonts.GetTypefaces%2A> <xref:System.Windows.Media.Typeface> uygulama yazı tipi konumundan nesne koleksiyonunu döndürmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="643d9-149">Bu durumda, uygulama "resources" adlı bir alt dizin içerir.</span><span class="sxs-lookup"><span data-stu-id="643d9-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="643d9-150">Yazı tipi kaynak kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="643d9-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="643d9-151">Yalnızca yazı tiplerini içeren yalnızca kaynak kitaplığı oluşturabilirsiniz — kod, bu tür kitaplık projesi parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="643d9-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="643d9-152">Yalnızca kaynak kitaplığı oluşturma, kaynakları kullanan uygulama kodundan ayrılmış kaynaklar için ortak bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="643d9-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="643d9-153">Bu Ayrıca, kitaplık derlemesinin birden çok uygulama projesine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="643d9-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="643d9-154">Aşağıdaki proje dosyası örneği, kaynak kitaplığı projesinin önemli kısımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="643d9-155">Kaynak kitaplığındaki bir yazı tipine başvurma</span><span class="sxs-lookup"><span data-stu-id="643d9-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="643d9-156">Uygulamanızdan bir kaynak kitaplığındaki bir yazı tipine başvurmak için, yazı tipi başvurusunu kitaplık derlemesinin adı ile önekle uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="643d9-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="643d9-157">Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir.</span><span class="sxs-lookup"><span data-stu-id="643d9-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="643d9-158">Derleme adını derleme içindeki başvurudan ayırmak için '; ' karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="643d9-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="643d9-159">"Component" anahtar sözcüğünü ve ardından yazı tipi adının başvurusunu eklemek, yazı tipi kitaplığının kaynağına tam başvuruyu tamamlar.</span><span class="sxs-lookup"><span data-stu-id="643d9-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="643d9-160">Aşağıdaki kod örneği, bir kaynak kitaplığı derlemesinde bir yazı tipine nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="643d9-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="643d9-161">Bu SDK, uygulamalarla kullanabileceğiniz örnek bir OpenType yazı tipi kümesi içerir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="643d9-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="643d9-162">Yazı tipleri yalnızca kaynak kitaplığında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="643d9-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="643d9-163">Daha fazla bilgi için bkz. [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="643d9-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="643d9-164">Yazı tipi kullanımı sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="643d9-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="643d9-165">Aşağıdaki listede, uygulamalarda yazı tiplerinin paketlenmesi ve kullanımıyla ilgili çeşitli sınırlamalar açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="643d9-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="643d9-166">**Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar herhangi bir yazı tipi ekleme izni bitini denetlemez veya zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="643d9-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="643d9-167">Daha fazla bilgi için [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="643d9-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="643d9-168">**Kaynak yazı tiplerinin sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, http veya FTP Tekdüzen Kaynak tanımlayıcısı (URI) için yazı tipi başvurusuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="643d9-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="643d9-169">**Paketi kullanan mutlak URI: Gösterim:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar <xref:System.Windows.Media.FontFamily> , bir yazı tipine mutlak Tekdüzen Kaynak tanımlayıcısı (URI) başvurusunun bir parçası olarak "Pack:" kullanarak programlı bir nesne oluşturmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="643d9-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="643d9-170">Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.</span><span class="sxs-lookup"><span data-stu-id="643d9-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="643d9-171">**Otomatik yazı tipi ekleme:** Tasarım zamanı sırasında uygulamanın yazı tipi kullanımını arama ve yazı tiplerini uygulamanın kaynaklarına otomatik olarak katıştırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="643d9-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="643d9-172">**Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, sabit olmayan belgeler için yazı tipi alt kümelerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="643d9-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="643d9-173">Yanlış bir başvuru olduğu durumlarda, uygulama kullanılabilir bir yazı tipi kullanmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="643d9-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643d9-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="643d9-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="643d9-175">Microsoft Tipografi: bağlantılar, Haberler ve kişiler</span><span class="sxs-lookup"><span data-stu-id="643d9-175">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="643d9-176">OpenType belirtimi</span><span class="sxs-lookup"><span data-stu-id="643d9-176">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="643d9-177">OpenType Yazı Tipi Özellikleri</span><span class="sxs-lookup"><span data-stu-id="643d9-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="643d9-178">Örnek OpenType Yazı Tipi Paketi</span><span class="sxs-lookup"><span data-stu-id="643d9-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
