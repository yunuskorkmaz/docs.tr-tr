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
ms.openlocfilehash: 52ed421ee92eed29bf16815d22e3ec7a8b718a84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632354"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="46673-102">Uygulamalarla Yazı Tiplerini Paketleme</span><span class="sxs-lookup"><span data-stu-id="46673-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="46673-103">Bu konuda paket yazı tipleri ile nasıl genel bir bakış sağlar, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="46673-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46673-104">Çoğu yazılım türleri gibi yazı tipi dosyalarını lisanslı satılan yerine.</span><span class="sxs-lookup"><span data-stu-id="46673-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="46673-105">Yazı tipleri yöneten lisansları satıcı satıcı ancak genel olarak yazı tiplerini dahil olmak üzere çoğu lisansları farklılık [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] uygulamalarla sağlar ve [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], yazı tiplerini uygulamalar içinde gömülü veya aksi izin verme yeniden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="46673-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="46673-106">İçinde bir uygulama veya başka türlü redıstrıbute ekleme herhangi bir yazı tipi için gerekli lisans haklarına sahip olmak sizin sorumluluğunuzdadır olduğundan bu nedenle, bir geliştirici olarak.</span><span class="sxs-lookup"><span data-stu-id="46673-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="46673-107">Giriş yazı tiplerini paketleme</span><span class="sxs-lookup"><span data-stu-id="46673-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="46673-108">İçinde kaynaklar olarak yazı tiplerini kolayca paketleyebilir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik tabanlı uygulamaları kullanıcı arabirimi metinlerini ve diğer türde metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="46673-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="46673-109">Yazı tiplerinin ayrı veya eklenen uygulamanın derleme dosyaları içinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="46673-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="46673-110">Ayrıca, uygulamanızın başvurabileceği bir yalnızca kaynak yazı tipi kitaplığı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46673-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="46673-111">ve [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı tiplerinin bir tür bayrak, yazı tipi katıştırma lisans hakları yazı tipini gösteren fsType içerir.</span><span class="sxs-lookup"><span data-stu-id="46673-111">and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="46673-112">Ancak, yalnızca bir belge – içinde depolanan katıştırılmış yazı tiplerini başvurduğu bu tür bir uygulamada katıştırılmış yazı tipi başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="46673-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="46673-113">Bir yazı tipi için haklar oluşturarak yazı tipi alabilirsiniz bir <xref:System.Windows.Media.GlyphTypeface> nesne ve bunlara başvurma kendi <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="46673-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="46673-114">"İşletim sistemi/2 ve Windows ölçümlerini" bölümüne bakın [OpenType Belirtimi](https://www.microsoft.com/typography/otspec/os2.htm) fsType bayrağı hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="46673-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="46673-115">[Microsoft Typography](https://www.microsoft.com/typography/links/) Web sitesi belirli yazı tipleriyle veya özel bir çalışma için yazı tipi sağlayıcısı bulun yardımcı olabilecek ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="46673-115">The [Microsoft Typography](https://www.microsoft.com/typography/links/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="46673-116">İçerik öğeleri olarak yazı tipi ekleme</span><span class="sxs-lookup"><span data-stu-id="46673-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="46673-117">Yazı tiplerini uygulamanıza uygulamanın derleme dosyalarından ayrı proje içerik öğeler olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46673-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="46673-118">Bu içerik öğeleri bir derleme içindeki kaynakları olarak gömülü olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46673-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="46673-119">Aşağıdaki proje dosyası örneği içerik öğelerinin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46673-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="46673-120">Uygulama çalışma zamanında yazı tiplerinin kullanmasını sağlamak için yazı tiplerini uygulamanın dağıtım dizinine erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46673-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="46673-121">`<CopyToOutputDirectory>` Uygulamanın proje dosyasında öğe yazı tiplerinin uygulama dağıtım dizinine derleme işlemi sırasında otomatik olarak kopyalanıp olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="46673-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="46673-122">Aşağıdaki proje dosyası örneği, yazı tiplerini dağıtım dizinine kopyalanacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46673-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="46673-123">Aşağıdaki kod örneği, uygulamanın yazı tipi içerik öğesi olarak başvurmak gösterilmektedir: başvurulan içerik öğesi, uygulamanın bütünleştirilmiş kod dosyaları ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46673-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="46673-124">Kaynak öğeleri olarak yazı tipi ekleme</span><span class="sxs-lookup"><span data-stu-id="46673-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="46673-125">Yazı tiplerini uygulamanıza uygulamanın derleme dosyaları içinde gömülü proje kaynak öğeler olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46673-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="46673-126">Kaynaklar için ayrı bir alt dizin kullanarak uygulamanın proje dosyalarını düzenlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="46673-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="46673-127">Aşağıdaki proje dosyası örneği ayrı bir alt dizinde kaynak öğeleri olarak yazı tiplerini tanımlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="46673-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="46673-128">Yazı tipleri kaynak olarak uygulamanıza eklediğinizde, ayarladığınızdan emin olun `<Resource>` öğesi değil `<EmbeddedResource>` uygulamanızın proje dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="46673-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="46673-129">`<EmbeddedResource>` Öğe oluşturma eylemi için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="46673-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="46673-130">Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklara başvuran gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46673-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="46673-131">Yazı tipi kaynak öğelerini koddan başvurma</span><span class="sxs-lookup"><span data-stu-id="46673-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="46673-132">Yazı tipi kaynak öğelerini koddan başvurmak için iki parçalı yazı tipi kaynak başvuru sağlamanız gerekir: temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; ve yazı tipi konumu başvurusu.</span><span class="sxs-lookup"><span data-stu-id="46673-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="46673-133">Bu değerler için parametre olarak kullanılan <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46673-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="46673-134">Aşağıdaki kod örneği başvuru adlı proje alt yazı tipi kaynaklarında uygulamanın nasıl gösterir `resources`.</span><span class="sxs-lookup"><span data-stu-id="46673-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="46673-135">Temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] yazı tipi kaynak yer aldığı uygulama alt içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46673-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="46673-136">Bu durumda, yazı tipi konumu başvurusu bir dizin belirtmek ihtiyaç duymaz ancak içermesi gerekir "`./`", yazı tipi kaynak gösteren temel tarafından belirtilen ile aynı dizinde olduğu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46673-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="46673-137">Yazı tipi kaynak öğesi başvuru alternatif bir yolu aşağıdaki kod örneği gösterir; önceki örnek kod eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="46673-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="46673-138">Aynı uygulama alt dizinden başvuru yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="46673-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="46673-139">Her iki uygulama içerik ve kaynak dosyaları aynı kullanıcı tarafından tanımlanan alt uygulama projenizin içinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46673-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="46673-140">İçerik sayfası ve yazı tipi kaynakları aynı alt dizinde tanımlanan aşağıdaki proje dosyası örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="46673-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="46673-141">Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvuru uygulama içeriğine göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="46673-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="46673-142">Aşağıdaki örnekler, yazı tipi uygulama ile aynı dizinde olduğunda uygulamanın yazı tipi kaynağa başvuran gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46673-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="46673-143">Bir uygulamada yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="46673-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="46673-144">Uygulamanızdaki kaynak öğeleri olarak yazı tiplerini numaralandırma için ya da kullanın <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> veya <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46673-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="46673-145">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.FontFamily> uygulama yazı tipi konumdan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="46673-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="46673-146">Bu durumda, uygulamanın "Kaynaklar" adlı bir alt dizin içeriyor.</span><span class="sxs-lookup"><span data-stu-id="46673-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="46673-147">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetTypefaces%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.Typeface> uygulama yazı tipi konumdan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="46673-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="46673-148">Bu durumda, uygulamanın "Kaynaklar" adlı bir alt dizin içeriyor.</span><span class="sxs-lookup"><span data-stu-id="46673-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="46673-149">Bir yazı tipi kaynak kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="46673-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="46673-150">Yalnızca yazı tiplerini içeren yalnızca kaynak kitaplığı oluşturabilirsiniz — kod kitaplığı projesi bu tür bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="46673-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="46673-151">Yalnızca kaynak kitaplığı oluşturmak, bunları kullanan uygulama kodu kaynaklardan ayırma için yaygın bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="46673-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="46673-152">Bu, birden çok uygulama projeleriyle dahil edilecek kitaplık derlemesine de sağlar.</span><span class="sxs-lookup"><span data-stu-id="46673-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="46673-153">Aşağıdaki proje dosyası örneği yalnızca kaynak kitaplık projesi anahtar kısımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46673-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="46673-154">Bir yazı tipi Kaynak Kitaplığı'nda başvurma</span><span class="sxs-lookup"><span data-stu-id="46673-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="46673-155">Uygulamanızdan bir yazı tipi Kaynak Kitaplığı'nda başvurmak için kitaplık derlemenin adı ile yazı tipi başvurusu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46673-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="46673-156">Bu durumda, yazı tipi kaynak derleme "FontLibrary" dir.</span><span class="sxs-lookup"><span data-stu-id="46673-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="46673-157">Başvuru bütünleştirilmiş kod içinde derleme adını ayırmak için bir ';' karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="46673-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="46673-158">Başvuru yazı tipi adı olarak "Component" anahtar sözcüğünü ekleme tam yazı tipi kitaplık kaynağına başvuru tamamlar.</span><span class="sxs-lookup"><span data-stu-id="46673-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="46673-159">Aşağıdaki kod örneği, bir yazı tipi kaynak kitaplığı derlemede başvuru gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46673-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="46673-160">Bu SDK örnek kümesini içeren [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile kullanabileceğiniz yazı tipleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="46673-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="46673-161">Yazı tiplerinin yalnızca kaynak kitaplığında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="46673-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="46673-162">Daha fazla bilgi için [örnek OpenType yazı tipi paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="46673-162">For more information, see [Sample OpenType Font Pack](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="46673-163">Yazı tipi kullanımı sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="46673-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="46673-164">Aşağıdaki listede, paketleme ve yazı tiplerinin kullanımı bazı sınırlamaları açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar:</span><span class="sxs-lookup"><span data-stu-id="46673-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="46673-165">**Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları denetlemez veya izin bitlerini herhangi bir yazı tipi zorla.</span><span class="sxs-lookup"><span data-stu-id="46673-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="46673-166">Bkz: [Introduction_to_Packing yazı tipleri](#introduction_to_packaging_fonts) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="46673-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="46673-167">**Site kaynak yazı tipi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların http veya ftp yazı tipi başvuru izin vermiyor [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46673-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="46673-168">**Paketi kullanarak bir mutlak URI: gösterimi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar oluşturmanızı verme bir <xref:System.Windows.Media.FontFamily> program aracılığıyla kullanarak nesne "paketi:" mutlak bir parçası olarak [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] bir yazı tipi başvuru.</span><span class="sxs-lookup"><span data-stu-id="46673-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="46673-169">Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz yazı tipi başvurudur.</span><span class="sxs-lookup"><span data-stu-id="46673-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="46673-170">**Otomatik yazı tipi ekleme:** Tasarım sırasında uygulama kullanımını yazı tipleri aramak ve yazı tipleri uygulamanın kaynakları otomatik olarak ekleme desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="46673-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="46673-171">**Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları sabit olmayan belgeler için yazı tipi alt kümeleri oluşturmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="46673-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="46673-172">Durumlarda hatalı bir başvuru olduğunda, uygulama yeniden kullanılabilir bir yazı tipi kullanarak döner.</span><span class="sxs-lookup"><span data-stu-id="46673-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46673-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46673-173">See also</span></span>
- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="46673-174">Microsoft tipografi: Bağlantılar, haber ve kişiler</span><span class="sxs-lookup"><span data-stu-id="46673-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://www.microsoft.com/typography/links/)
- [<span data-ttu-id="46673-175">OpenType Belirtimi</span><span class="sxs-lookup"><span data-stu-id="46673-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="46673-176">OpenType Yazı Tipi Özellikleri</span><span class="sxs-lookup"><span data-stu-id="46673-176">OpenType Font Features</span></span>](../../../../docs/framework/wpf/advanced/opentype-font-features.md)
- [<span data-ttu-id="46673-177">Örnek OpenType Yazı Tipi Paketi</span><span class="sxs-lookup"><span data-stu-id="46673-177">Sample OpenType Font Pack</span></span>](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
