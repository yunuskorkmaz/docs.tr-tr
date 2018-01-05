---
title: "Uygulamalarla Yazı Tiplerini Paketleme"
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
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3860aff69b0e4e7a3dc624898cc6b1daa0dd092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-fonts-with-applications"></a>Uygulamalarla Yazı Tiplerini Paketleme
Bu konuda paket yazı tipleriyle hakkında genel bakış sağlar, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama.  
  
> [!NOTE]
>  Çoğu yazılım türleri gibi yazı tipi dosyaları lisanslı satılan yerine. Yazı tipleri kullanımını yöneten lisanslar yazı tiplerini kapsayan dahil olmak üzere çoğu lisans satıcı satıcı ancak genel farklılık [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] uygulamalarla sağlar ve [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], uygulama içinden katıştırılmış veya aksi yazı tiplerini izin verme yeniden dağıtılması gerekir. Bir uygulama veya aksi Dağıt içinde katıştırmak herhangi bir yazı tipi için gerekli lisans haklarına sahip olmak sizin sorumluluğunuzdadır olduğundan bu nedenle, geliştirici olarak.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Yazı tiplerini paketlemeye giriş  
 Yazı tipleri içindeki kaynaklar olarak kolayca paketleyebilirsiniz, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik tabanlı kullanıcı arabirimi metni ve diğer türleri metin görüntülemek için uygulamaları. Yazı tipleri ayrı veya uygulamanın derleme dosyaları içinde katıştırılmış olabilir. Ayrıca, uygulamanızın başvurabilir bir yalnızca kaynak yazı tipi kitaplığı oluşturabilirsiniz.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]ve [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı tiplerini bir tür bayrak, yazı tipi gömülmüş lisanslama hakları yazı tipini fsType, içerir. Ancak, yalnızca bir belge – içinde depolanan katıştırılmış yazı tiplerini başvurduğu bu tür bir uygulamada katıştırılmış yazı tipi başvurmuyor. Yazı tipi için haklar oluşturarak katıştırma yazı tipi alabilir bir <xref:System.Windows.Media.GlyphTypeface> nesne ve başvuran kendi <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliği. "OS/2 ve Windows ölçütleri" bölümüne bakın [OpenType Belirtimi](http://www.microsoft.com/typography/otspec/os2.htm) fsType bayrağı hakkında daha fazla bilgi için.  
  
 [Microsoft Typography](http://www.microsoft.com/typography/links/) Web sitesi belirli yazı tipi satıcı bulun veya özel iş için bir yazı tipi satıcı Bul yardımcı olabilecek kişi bilgilerini içerir.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Yazı tipleri içerik öğeleri olarak ekleme  
 Yazı tipleri uygulamanızı uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak ekleyebilirsiniz. Başka bir deyişle, içerik öğeleri derleme içindeki kaynaklar olarak ekli değil. Aşağıdaki proje dosyası örneği içerik öğelerinin nasıl tanımlanacağı gösterilmektedir.  
  
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
  
 Uygulamanın çalışma zamanında yazı tiplerini kullanmasını sağlamak için yazı tiplerini uygulamanın dağıtım dizininde erişilebilir olması gerekir. `<CopyToOutputDirectory>` Öğesi uygulamanın proje dosyasında yazı tiplerini uygulama dağıtım dizinine oluşturma işlemi sırasında otomatik olarak kopyalamanıza olanak sağlar. Aşağıdaki proje dosyası örneği yazı dağıtım dizinine Kopyala gösterilmektedir.  
  
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
  
 Aşağıdaki kod örneği uygulamanın yazı tipi içerik öğesi olarak başvuru gösterilmektedir — başvurulan içerik öğe uygulamanın derleme dosyaları ile aynı dizinde olması gerekir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Yazı tipleri kaynak öğeler olarak ekleme  
 Yazı tipleri uygulamanızı uygulamanın derleme dosyaları içinde katıştırılmış proje kaynak öğeler olarak ekleyebilirsiniz. Kaynaklar için ayrı bir alt dizin kullanarak uygulamanın proje dosyalarını düzenlemenize yardımcı olur. Aşağıdaki proje dosyası örneği ayrı bir alt dizin kaynak öğeler olarak yazı tiplerini tanımlamak nasıl gösterir.  
  
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
>  Uygulamanız için kaynak olarak yazı tipleri eklediğinizde, ayarladığınızdan emin olun `<Resource>` öğesi ve `<EmbeddedResource>` uygulamanızın proje dosyasında öğesi. `<EmbeddedResource>` Öğesi derleme eylemi için desteklenmiyor.  
  
 Aşağıdaki biçimlendirme örneği uygulamanın yazı tipi kaynaklara başvuran gösterilmektedir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Yazı tipi kaynak öğelerine koddan başvurma  
 Yazı tipi kaynak öğelerine koddan başvurmak için iki parçalı yazı tipi kaynak başvurusu sağlamalısınız: temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; ve yazı tipi konumu başvurusu. Bu değerler için parametre olarak kullanılan <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntemi. Aşağıdaki kod örneğinde adlı proje alt dizinindeki uygulamanın yazı tipi kaynaklarına başvuru gösterilmektedir `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] yazı tipi kaynağının bulunduğu uygulama alt içerebilir. Bu durumda, yazı tipi konumu başvurusu bir dizin belirtmek zorunda değildir, ancak içermesi gerekir "`./`", yazı tipi kaynak belirten temel tarafından belirtilen aynı dizinde yer [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Yazı tipi kaynağı öğesine başvuru alternatif bir yolu aşağıdaki kod örneği gösterir; önceki kod örneğinde eşdeğerdir.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Aynı uygulama alt dizininden yazı tipleri başvurma  
 Her iki uygulama içeriği ve kaynak dosyaları aynı kullanıcı tarafından tanımlanan alt uygulama projenizin içinde yerleştirebilirsiniz. Aşağıdaki proje dosyası örneği bir içerik sayfasını ve aynı alt dizinde tanımlı yazı tipi kaynakları gösterir.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu göre uygulama içeriktir. Aşağıdaki örnekler, yazı tipi uygulama ile aynı dizinde olduğunda uygulamanın yazı tipi kaynağa başvuran gösterilmektedir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Bir uygulamada yazı tiplerini numaralandırma  
 Uygulamanızda kaynak öğeler olarak yazı tiplerini numaralandırma için kullanın ya da <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> veya <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yöntemi. Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.FontFamily> uygulama yazı tipi konumdan nesneleri. Bu durumda, "Kaynaklar" adlı bir alt uygulama içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetTypefaces%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.Typeface> uygulama yazı tipi konumdan nesneleri. Bu durumda, "Kaynaklar" adlı bir alt uygulama içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Yazı tipi kaynak kitaplığı oluşturma  
 Yalnızca yazı tiplerini içeren bir yalnızca kaynak kitaplık oluşturabilirsiniz — herhangi bir kodu bu tür kitaplık projesinin bir parçasıdır. Yalnızca kaynak kitaplığı oluşturmak, bunları kullanan uygulama kodu kaynaklardan kesilmesi için ortak bir tekniktir. Bu aynı zamanda birden çok uygulama projeleri ile dahil edilecek Kitaplık derlemesi sağlar. Aşağıdaki proje dosyası örneği yalnızca kaynak kitaplığı projesi anahtar kısımlarını gösterir.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Bir kaynak kitaplığında bir yazı tipi başvurma  
 Uygulamanızdan kaynak kitaplığındaki bir yazı tipi başvurmak için yazı tipi başvurusuna kitaplık derlemesinin adıyla önek gerekir. Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir. Derleme adı derlemedeki başvuru ayırmak üzere ';' karakterini kullanın. Yazı tipi adı başvurusunu ve ardından "Component" anahtar sözcüğü ekleyerek yazı tipi kitaplık kaynağı tam referansı tamamlar. Aşağıdaki kod örneği, bir kaynak kitaplığının derlemedeki bir yazı tipi başvuru gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Bu SDK örnek kümesini içeren [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile birlikte kullanabileceğiniz yazı tipleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar. Yazı tipleri yalnızca kaynak kitaplığa tanımlanır. Daha fazla bilgi için bkz: [örnek OpenType yazıtipi paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Yazı tipi kullanımı sınırlamaları  
 Aşağıdaki listede paketleme ve yazı tipleri kullanımını ilgili bazı sınırlamaları açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar:  
  
-   **Yazı tipi izin bitleri katıştırma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları denetlemez veya izin bitleri katıştırma herhangi bir yazı tipi zorlamaz. Bkz: [Introduction_to_Packing yazı tipleri](#introduction_to_packaging_fonts) daha fazla bilgi için bölüm.  
  
-   **Kaynak yazı tipleri sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları bir http veya ftp için yazı tipi başvurusuna izin vermez [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Paketi kullanarak mutlak URI: gösterimi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları izin vermez oluşturmak bir <xref:System.Windows.Media.FontFamily> program aracılığıyla kullanarak nesne "paketi:" mutlak bir parçası olarak [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] bir yazı tipi referansı. Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.  
  
-   **Otomatik yazı tipi katıştırma:** tasarım sırasında yazı tipleri uygulamanın kullanımını aramak ve otomatik olarak uygulamanın kaynaklarında yazı tiplerini katıştırma desteği yoktur.  
  
-   **Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları sabit olmayan belgeler için yazı tipi alt kümeleri oluşturulmasını desteklemez.  
  
-   Durumlarda yanlış başvuru olduğunda, uygulama kullanılabilir bir yazıtipi kullanmaya geri döner.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Microsoft tipografi: Bağlantılar, haber ve kişiler](http://www.microsoft.com/typography/links/)  
 [OpenType Belirtimi](http://www.microsoft.com/typography/otspec/)  
 [OpenType Yazı Tipi Özellikleri](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Örnek OpenType Yazı Tipi Paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
