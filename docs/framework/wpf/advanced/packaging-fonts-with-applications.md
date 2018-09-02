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
ms.openlocfilehash: 0ad8d071a91edaef184c4cc1fa28298f8ec3d71a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391772"
---
# <a name="packaging-fonts-with-applications"></a>Uygulamalarla Yazı Tiplerini Paketleme
Bu konuda paket yazı tipleri ile nasıl genel bir bakış sağlar, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama.  
  
> [!NOTE]
>  Çoğu yazılım türleri gibi yazı tipi dosyalarını lisanslı satılan yerine. Yazı tipleri yöneten lisansları satıcı satıcı ancak genel olarak yazı tiplerini dahil olmak üzere çoğu lisansları farklılık [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] uygulamalarla sağlar ve [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], yazı tiplerini uygulamalar içinde gömülü veya aksi izin verme yeniden dağıtılabilir. İçinde bir uygulama veya başka türlü redıstrıbute ekleme herhangi bir yazı tipi için gerekli lisans haklarına sahip olmak sizin sorumluluğunuzdadır olduğundan bu nedenle, bir geliştirici olarak.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Giriş yazı tiplerini paketleme  
 İçinde kaynaklar olarak yazı tiplerini kolayca paketleyebilir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik tabanlı uygulamaları kullanıcı arabirimi metinlerini ve diğer türde metin görüntüler. Yazı tiplerinin ayrı veya eklenen uygulamanın derleme dosyaları içinde olabilir. Ayrıca, uygulamanızın başvurabileceği bir yalnızca kaynak yazı tipi kitaplığı oluşturabilirsiniz.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ve [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı tiplerinin bir tür bayrak, yazı tipi katıştırma lisans hakları yazı tipini gösteren fsType içerir. Ancak, yalnızca bir belge – içinde depolanan katıştırılmış yazı tiplerini başvurduğu bu tür bir uygulamada katıştırılmış yazı tipi başvurmuyor. Bir yazı tipi için haklar oluşturarak yazı tipi alabilirsiniz bir <xref:System.Windows.Media.GlyphTypeface> nesne ve bunlara başvurma kendi <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliği. "İşletim sistemi/2 ve Windows ölçümlerini" bölümüne bakın [OpenType Belirtimi](https://www.microsoft.com/typography/otspec/os2.htm) fsType bayrağı hakkında daha fazla bilgi için.  
  
 [Microsoft Typography](https://www.microsoft.com/typography/links/) Web sitesi belirli yazı tipleriyle veya özel bir çalışma için yazı tipi sağlayıcısı bulun yardımcı olabilecek ilgili bilgiler içerir.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>İçerik öğeleri olarak yazı tipi ekleme  
 Yazı tiplerini uygulamanıza uygulamanın derleme dosyalarından ayrı proje içerik öğeler olarak ekleyebilirsiniz. Bu içerik öğeleri bir derleme içindeki kaynakları olarak gömülü olmayan anlamına gelir. Aşağıdaki proje dosyası örneği içerik öğelerinin nasıl tanımlanacağını gösterir.  
  
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
  
 Uygulama çalışma zamanında yazı tiplerinin kullanmasını sağlamak için yazı tiplerini uygulamanın dağıtım dizinine erişilebilir olması gerekir. `<CopyToOutputDirectory>` Uygulamanın proje dosyasında öğe yazı tiplerinin uygulama dağıtım dizinine derleme işlemi sırasında otomatik olarak kopyalanıp olanak tanır. Aşağıdaki proje dosyası örneği, yazı tiplerini dağıtım dizinine kopyalanacak gösterilmektedir.  
  
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
  
 Aşağıdaki kod örneği, uygulamanın yazı tipi içerik öğesi olarak başvurmak gösterilmektedir: başvurulan içerik öğesi, uygulamanın bütünleştirilmiş kod dosyaları ile aynı dizinde olmalıdır.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Kaynak öğeleri olarak yazı tipi ekleme  
 Yazı tiplerini uygulamanıza uygulamanın derleme dosyaları içinde gömülü proje kaynak öğeler olarak ekleyebilirsiniz. Kaynaklar için ayrı bir alt dizin kullanarak uygulamanın proje dosyalarını düzenlemenize yardımcı olur. Aşağıdaki proje dosyası örneği ayrı bir alt dizinde kaynak öğeleri olarak yazı tiplerini tanımlamak nasıl gösterir.  
  
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
>  Yazı tipleri kaynak olarak uygulamanıza eklediğinizde, ayarladığınızdan emin olun `<Resource>` öğesi değil `<EmbeddedResource>` uygulamanızın proje dosyasında öğesi. `<EmbeddedResource>` Öğe oluşturma eylemi için desteklenmiyor.  
  
 Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklara başvuran gösterilmektedir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Yazı tipi kaynak öğelerini koddan başvurma  
 Yazı tipi kaynak öğelerini koddan başvurmak için iki parçalı yazı tipi kaynak başvuru sağlamanız gerekir: temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; ve yazı tipi konumu başvurusu. Bu değerler için parametre olarak kullanılan <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntemi. Aşağıdaki kod örneği başvuru adlı proje alt yazı tipi kaynaklarında uygulamanın nasıl gösterir `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Temel [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] yazı tipi kaynak yer aldığı uygulama alt içerebilir. Bu durumda, yazı tipi konumu başvurusu bir dizin belirtmek ihtiyaç duymaz ancak içermesi gerekir "`./`", yazı tipi kaynak gösteren temel tarafından belirtilen ile aynı dizinde olduğu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Yazı tipi kaynak öğesi başvuru alternatif bir yolu aşağıdaki kod örneği gösterir; önceki örnek kod eşdeğerdir.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Aynı uygulama alt dizinden başvuru yazı tipleri  
 Her iki uygulama içerik ve kaynak dosyaları aynı kullanıcı tarafından tanımlanan alt uygulama projenizin içinde yerleştirebilirsiniz. İçerik sayfası ve yazı tipi kaynakları aynı alt dizinde tanımlanan aşağıdaki proje dosyası örneği gösterir.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvuru uygulama içeriğine göre yapılır. Aşağıdaki örnekler, yazı tipi uygulama ile aynı dizinde olduğunda uygulamanın yazı tipi kaynağa başvuran gösterilmektedir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Bir uygulamada yazı tiplerini numaralandırma  
 Uygulamanızdaki kaynak öğeleri olarak yazı tiplerini numaralandırma için ya da kullanın <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> veya <xref:System.Windows.Media.Fonts.GetTypefaces%2A> yöntemi. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.FontFamily> uygulama yazı tipi konumdan nesneleri. Bu durumda, uygulamanın "Kaynaklar" adlı bir alt dizin içeriyor.  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Fonts.GetTypefaces%2A> koleksiyonunu döndürülecek yöntemi <xref:System.Windows.Media.Typeface> uygulama yazı tipi konumdan nesneleri. Bu durumda, uygulamanın "Kaynaklar" adlı bir alt dizin içeriyor.  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Bir yazı tipi kaynak kitaplığı oluşturma  
 Yalnızca yazı tiplerini içeren yalnızca kaynak kitaplığı oluşturabilirsiniz — kod kitaplığı projesi bu tür bir parçasıdır. Yalnızca kaynak kitaplığı oluşturmak, bunları kullanan uygulama kodu kaynaklardan ayırma için yaygın bir tekniktir. Bu, birden çok uygulama projeleriyle dahil edilecek kitaplık derlemesine de sağlar. Aşağıdaki proje dosyası örneği yalnızca kaynak kitaplık projesi anahtar kısımlarını gösterir.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Bir yazı tipi Kaynak Kitaplığı'nda başvurma  
 Uygulamanızdan bir yazı tipi Kaynak Kitaplığı'nda başvurmak için kitaplık derlemenin adı ile yazı tipi başvurusu eklemeniz gerekir. Bu durumda, yazı tipi kaynak derleme "FontLibrary" dir. Başvuru bütünleştirilmiş kod içinde derleme adını ayırmak için bir ';' karakterini kullanın. Başvuru yazı tipi adı olarak "Component" anahtar sözcüğünü ekleme tam yazı tipi kitaplık kaynağına başvuru tamamlar. Aşağıdaki kod örneği, bir yazı tipi kaynak kitaplığı derlemede başvuru gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Bu SDK örnek kümesini içeren [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile kullanabileceğiniz yazı tipleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar. Yazı tiplerinin yalnızca kaynak kitaplığında tanımlanır. Daha fazla bilgi için [örnek OpenType yazı tipi paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Yazı tipi kullanımı sınırlamaları  
 Aşağıdaki listede, paketleme ve yazı tiplerinin kullanımı bazı sınırlamaları açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar:  
  
-   **Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları denetlemez veya izin bitlerini herhangi bir yazı tipi zorla. Bkz: [Introduction_to_Packing yazı tipleri](#introduction_to_packaging_fonts) bölümünde daha fazla bilgi için.  
  
-   **Site kaynak yazı tipi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların http veya ftp yazı tipi başvuru izin vermiyor [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Paketi kullanarak bir mutlak URI: gösterimi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar oluşturmanızı verme bir <xref:System.Windows.Media.FontFamily> program aracılığıyla kullanarak nesne "paketi:" mutlak bir parçası olarak [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] bir yazı tipi başvuru. Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz yazı tipi başvurudur.  
  
-   **Otomatik yazı tipi katıştırma:** tasarım sırasında uygulama kullanımını yazı tipleri aramak ve yazı tipleri uygulamanın kaynakları otomatik olarak ekleme desteği yoktur.  
  
-   **Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları sabit olmayan belgeler için yazı tipi alt kümeleri oluşturmayı desteklemez.  
  
-   Durumlarda hatalı bir başvuru olduğunda, uygulama yeniden kullanılabilir bir yazı tipi kullanarak döner.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Microsoft tipografi: Bağlantılar, haber ve kişiler](https://www.microsoft.com/typography/links/)  
 [OpenType Belirtimi](https://www.microsoft.com/typography/otspec/)  
 [OpenType Yazı Tipi Özellikleri](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Örnek OpenType Yazı Tipi Paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
