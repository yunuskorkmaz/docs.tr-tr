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
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187084"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="5b2a9-102">Uygulamalarla Yazı Tiplerini Paketleme</span><span class="sxs-lookup"><span data-stu-id="5b2a9-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="5b2a9-103">Bu konu, uygulamanızla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tiplerini nasıl paketleeceğine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b2a9-104">Çoğu yazılım türünde olduğu gibi, yazı tipi dosyaları satılmak yerine lisanslanır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="5b2a9-105">Yazı tiplerinin kullanımını yöneten lisanslar satıcıdan satıcıya değişir, ancak Microsoft'un uygulamaları ve Windows ile sağladığı yazı tiplerini kapsayanlar da dahil olmak üzere genel olarak çoğu lisans, yazı tiplerinin uygulamalara katıştırılmasına veya başka bir şekilde yeniden dağıtılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="5b2a9-106">Bu nedenle, bir geliştirici olarak, bir uygulamanın içine katıştırdığınız veya başka bir şekilde yeniden dağıttığınız herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="5b2a9-107">Ambalaj Yazı Tiplerine Giriş</span><span class="sxs-lookup"><span data-stu-id="5b2a9-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="5b2a9-108">Kullanıcı arabirimi metnini ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer metin tabanlı içerik türlerini görüntülemek için yazı tiplerini uygulamalarınızda kaynak olarak kolayca paketleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="5b2a9-109">Yazı tipleri, uygulamanın derleme dosyalarından ayrılabilir veya içine katışabilir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="5b2a9-110">Ayrıca, uygulamanızın başvuruedebileceği yalnızca kaynak yazı tipi kitaplığı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="5b2a9-111">OpenType ve TrueType® yazı tipleri, yazı tipi için yazı tipi katıştırma lisanslama haklarını gösteren bir tür bayrağı, fsType içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-111">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="5b2a9-112">Ancak, bu tür bayrağı yalnızca bir belgede depolanan katışılmış yazı tiplerini ifade eder-bir uygulamaya katışılmış yazı tiplerine atıfta bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="5b2a9-113">Bir <xref:System.Windows.Media.GlyphTypeface> nesne oluşturup <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliğine başvurarak yazı tipi nin yazı tipi katıştırma haklarını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="5b2a9-114">fsType bayrağı hakkında daha fazla bilgi için [OpenType Belirtimi'nin](https://www.microsoft.com/typography/otspec/os2.htm) "OS/2 ve Windows Ölçümleri" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="5b2a9-115">[Microsoft Tipografi](https://docs.microsoft.com/typography/) Web sitesi, belirli bir yazı tipi satıcısını bulmanıza veya özel çalışma için bir yazı tipi satıcısı bulmanıza yardımcı olabilecek kişi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="5b2a9-116">İçerik Öğesi Olarak Yazı Tipleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="5b2a9-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="5b2a9-117">Uygulamanıza, uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak yazı tipleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="5b2a9-118">Bu, içerik öğelerinin derleme içinde kaynak olarak katıştırılmış olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="5b2a9-119">Aşağıdaki proje dosyası örneği, içerik öğelerinin nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="5b2a9-120">Uygulamanın çalışma zamanında yazı tiplerini kullanabilmesini sağlamak için, yazı tiplerine uygulamanın dağıtım dizininde erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="5b2a9-121">Uygulamanın proje dosyasındaki öğe, `<CopyToOutputDirectory>` yapı işlemi sırasında yazı tiplerini otomatik olarak uygulama dağıtım dizinine kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="5b2a9-122">Aşağıdaki proje dosyası örneği, yazı tiplerinin dağıtım dizinine nasıl kopyalanış yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="5b2a9-123">Aşağıdaki kod örneği, uygulamanın yazı tipine içerik öğesi olarak nasıl başvuruleceğini gösterir- başvurulan içerik öğesi, uygulamanın derleme dosyalarıyla aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="5b2a9-124">Kaynak Öğesi Olarak Yazı Tipleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="5b2a9-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="5b2a9-125">Uygulamanıza, uygulamanın derleme dosyalarına katıştırılmış proje kaynağı öğeleri olarak yazı tipleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="5b2a9-126">Kaynaklar için ayrı bir alt dizini kullanmak, uygulamanın proje dosyalarını düzenlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="5b2a9-127">Aşağıdaki proje dosyası örneği, yazı tiplerinin ayrı bir alt dizinde kaynak öğeleri olarak nasıl tanımlanır gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="5b2a9-128">Uygulamanıza kaynak olarak yazı tipleri eklediğinizde, uygulamanızın `<Resource>` proje dosyasındaki `<EmbeddedResource>` öğeyi değil, öğeyi ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="5b2a9-129">Yapı `<EmbeddedResource>` eylemi öğesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="5b2a9-130">Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklarına nasıl başvurulup başvurulmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="5b2a9-131">Koddan Yazı Tipi Kaynak Öğelerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="5b2a9-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="5b2a9-132">Koddan yazı tipi kaynak öğelerine başvurmak için iki parçalı yazı tipi kaynak başvurusu sağlamanız gerekir: temel tekdüzen kaynak tanımlayıcısı (URI); ve yazı tipi konumu başvurusu.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="5b2a9-133">Bu değerler <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntem için parametre olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="5b2a9-134">Aşağıdaki kod örneği, uygulamanın yazı tipi kaynaklarına proje alt `resources`dizininde nasıl başvuruldu:</span><span class="sxs-lookup"><span data-stu-id="5b2a9-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="5b2a9-135">Temel tekdüzen kaynak tanımlayıcısı (URI), yazı tipi kaynağının bulunduğu uygulama alt dizinini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-135">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="5b2a9-136">Bu durumda, yazı tipi konumu başvurusu bir dizin belirtmek gerekmez, ancak`./`yazı tipi kaynağı temel tekdüzen kaynak tanımlayıcı (URI) tarafından belirtilen aynı dizinde olduğunu gösteren bir satır aralığı " ", eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="5b2a9-137">Aşağıdaki kod örneği, yazı tipi kaynak öğesine başvurmanın alternatif bir yolunu gösterir ve önceki kod örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="5b2a9-138">Aynı Uygulama Alt Dizini'nden Yazı Tiplerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="5b2a9-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="5b2a9-139">Hem uygulama içeriğini hem de kaynak dosyalarını uygulama projenizin aynı kullanıcı tanımlı alt dizinine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="5b2a9-140">Aşağıdaki proje dosyası örneği, aynı alt dizinde tanımlanan bir içerik sayfası ve yazı tipi kaynaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="5b2a9-141">Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu uygulama içeriğine göredir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="5b2a9-142">Aşağıdaki örnekler, yazı tipi uygulamayla aynı dizinde olduğunda uygulamanın yazı tipi kaynağına nasıl başvurulsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="5b2a9-143">Uygulamada Yazı Tiplerini Sayısallandırma</span><span class="sxs-lookup"><span data-stu-id="5b2a9-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="5b2a9-144">Uygulamanızda yazı tiplerini kaynak öğesi olarak sıralamak <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> için, ya yöntemi kullanın. <xref:System.Windows.Media.Fonts.GetTypefaces%2A></span><span class="sxs-lookup"><span data-stu-id="5b2a9-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="5b2a9-145">Aşağıdaki örnek, uygulama fontu konumundan <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> <xref:System.Windows.Media.FontFamily> nesnelerin koleksiyonunu döndürmek için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="5b2a9-146">Bu durumda, uygulama "kaynaklar" adlı bir alt dizini içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="5b2a9-147">Aşağıdaki örnek, uygulama fontu konumundan <xref:System.Windows.Media.Fonts.GetTypefaces%2A> <xref:System.Windows.Media.Typeface> nesnelerin koleksiyonunu döndürmek için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="5b2a9-148">Bu durumda, uygulama "kaynaklar" adlı bir alt dizini içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="5b2a9-149">Yazı Tipi Kaynak Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b2a9-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="5b2a9-150">Yalnızca yazı tipleri içeren yalnızca kaynak kitaplığı oluşturabilirsiniz—hiçbir kod bu tür kitaplık projesinin bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="5b2a9-151">Yalnızca kaynak kitaplığı oluşturmak, kaynakları bunları kullanan uygulama kodundan ayırmak için yaygın bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="5b2a9-152">Bu, kitaplık derlemesinin birden çok uygulama projesine dahil edilmesine de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="5b2a9-153">Aşağıdaki proje dosyası örneği, yalnızca kaynak kitaplığı projesinin önemli bölümlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="5b2a9-154">Kaynak Kitaplığında Yazı Tipine Başvurma</span><span class="sxs-lookup"><span data-stu-id="5b2a9-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="5b2a9-155">Uygulamanızdan kaynak kitaplığındaki bir yazı tipine başvurmak için yazı tipi başvurusunu kitaplık derlemesinin adıyla önetürmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="5b2a9-156">Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="5b2a9-157">Derleme adını derleme içindeki başvurudan ayırmak için bir ';' karakter kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="5b2a9-158">Yazı tipi adına başvurunun ardından "Bileşen" anahtar sözcüğünün eklenmesi, yazı tipi kitaplığı kaynağına yapılan başvurunun tamamını tamamlar.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="5b2a9-159">Aşağıdaki kod örneği, kaynak kitaplığı derlemesinde bir yazı tipine nasıl başvurulyur gösteriş yapar.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="5b2a9-160">Bu SDK, uygulamalarla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birlikte kullanabileceğiniz bir örnek OpenType yazı tipleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-160">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="5b2a9-161">Yazı tipleri yalnızca kaynak kitaplığında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="5b2a9-162">Daha fazla bilgi için [Örnek OpenType Yazı Tipi Paketi'ne](sample-opentype-font-pack.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="5b2a9-163">Font Kullanımındaki Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="5b2a9-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="5b2a9-164">Aşağıdaki liste, uygulamalarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tiplerinin paketlenmesi ve kullanımıyla ilgili çeşitli sınırlamaları açıklamaktadır:</span><span class="sxs-lookup"><span data-stu-id="5b2a9-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="5b2a9-165">**Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar herhangi bir yazı tipi katıştırma izin bitlerini denetlemez veya zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="5b2a9-166">Daha fazla bilgi için [Introduction_to_Packing Fontları](#introduction_to_packaging_fonts) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="5b2a9-167">**Kaynak yazı tipleri sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar bir http veya ftp üniforma kaynak tanımlayıcısına (URI) yazı tipi başvurusuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="5b2a9-168">**Paketi kullanarak Mutlak URI: gösterim:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar bir yazı <xref:System.Windows.Media.FontFamily> tipi için mutlak tekdüzen kaynak tanımlayıcısı (URI) referans parçası olarak "pack:" kullanarak programlı bir nesne oluşturmak için izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="5b2a9-169">Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="5b2a9-170">**Otomatik yazı tipi katıştırma:** Tasarım süresi boyunca, bir uygulamanın yazı tiplerini kullanımını aramak ve yazı tiplerini uygulamanın kaynaklarına otomatik olarak katıştırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="5b2a9-171">**Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar sabit olmayan belgeler için yazı tipi alt kümelerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="5b2a9-172">Yanlış başvuru nun olduğu durumlarda, uygulama kullanılabilir bir yazı tipini kullanmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2a9-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b2a9-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="5b2a9-174">Microsoft Tipografisi: Bağlantılar, Haberler ve Kişiler</span><span class="sxs-lookup"><span data-stu-id="5b2a9-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="5b2a9-175">OpenType Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5b2a9-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="5b2a9-176">OpenType Yazı Tipi Özellikleri</span><span class="sxs-lookup"><span data-stu-id="5b2a9-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="5b2a9-177">Örnek OpenType Yazı Tipi Paketi</span><span class="sxs-lookup"><span data-stu-id="5b2a9-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
