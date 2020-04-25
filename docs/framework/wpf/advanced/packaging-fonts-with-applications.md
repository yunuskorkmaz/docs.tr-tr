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
ms.openlocfilehash: 7bdf3b11557d94ab39c93a21ac53b917e3a1767d
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141114"
---
# <a name="packaging-fonts-with-applications"></a>Uygulamalarla Yazı Tiplerini Paketleme
Bu konu, yazı tiplerinin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamanıza nasıl paketlenecek hakkında genel bakış sağlar.  
  
> [!NOTE]
> Çoğu yazılım türünde olduğu gibi, satılan değil, yazı tipi dosyaları lisanslanır. Yazı tiplerinin kullanımını yöneten lisanslar satıcıdan satıcıya farklılık gösterir, ancak Microsoft 'un uygulamalar ve Windows ile birlikte bulunan yazı tiplerini kapsaanlar da dahil olmak üzere çoğu lisans, yazı tiplerinin uygulamalara katıştırılması veya yeniden dağıtılması için izin vermez. Bu nedenle, bir geliştirici olarak, bir uygulama içine eklediğiniz veya başka bir şekilde yeniden dağıtırabilmeniz gereken herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Paketleme yazı tiplerine giriş  
 Kullanıcı arabirimi metnini ve diğer metin tabanlı içerik türlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyecek şekilde, yazı tiplerini uygulamalarınızdaki kaynaklar olarak kolayca paketleyebilirsiniz. Yazı tipleri, uygulamanın derleme dosyalarından ayrı veya katıştırılmış olabilir. Ayrıca, uygulamanızın başvurbileceği yalnızca kaynak yazı tipi kitaplığı da oluşturabilirsiniz.  
  
 OpenType ve TrueType® yazı tiplerinde yazı tipi için, yazı tipi ekleme lisanslama haklarını belirten bir tür bayrağı vardır. Ancak, bu tür bayrağı yalnızca bir belgede depolanan katıştırılmış yazı tiplerine başvurur. bir uygulamaya katıştırılmış olan yazı tiplerine başvurmaz. Bir <xref:System.Windows.Media.GlyphTypeface> nesne oluşturarak ve <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliğine başvurarak bir yazı tipi için yazı tipi ekleme haklarını alabilirsiniz. FsType bayrağı hakkında daha fazla bilgi için [OpenType belirtiminin](https://www.microsoft.com/typography/otspec/os2.htm) "OS/2 ve Windows ölçümleri" bölümüne bakın.  
  
 [Microsoft Tipografi](https://docs.microsoft.com/typography/) Web sitesi, belirli bir yazı tipi satıcısının yerini bulmanıza veya özel iş için bir yazı tipi satıcısı bulmanıza yardımcı olabilecek iletişim bilgilerini içerir.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>Yazı tiplerini Içerik öğeleri olarak ekleme  
 Uygulamanıza, uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak yazı tipi ekleyebilirsiniz. Bu, içerik öğelerinin bir bütünleştirilmiş kod içinde kaynak olarak katıştırılmayacağı anlamına gelir. Aşağıdaki proje dosyası örneği, içerik öğelerinin nasıl tanımlanacağını gösterir.  
  
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
  
 Uygulamanın çalışma zamanında yazı tiplerini kullanabilmesi için, yazı tiplerinin uygulamanın dağıtım dizininde erişilebilir olması gerekir. Uygulamanın `<CopyToOutputDirectory>` proje dosyasındaki öğesi, derleme işlemi sırasında yazı tiplerini uygulama dağıtım dizinine otomatik olarak kopyalamanızı sağlar. Aşağıdaki proje dosyası örneği, yazı tiplerinin dağıtım dizinine nasıl kopyalanacağını gösterir.  
  
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
  
 Aşağıdaki kod örneği, uygulamanın yazı tipine içerik öğesi olarak nasıl başvurulacağını gösterir — başvurulan içerik öğesi, uygulamanın derleme dosyalarıyla aynı dizinde olmalıdır.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>Yazı tiplerini kaynak öğe olarak ekleme  
 Uygulamanıza, uygulamanın derleme dosyaları içine katıştırılmış proje kaynak öğeleri olarak yazı tipi ekleyebilirsiniz. Kaynaklar için ayrı bir alt dizin kullanılması, uygulamanın proje dosyalarını düzenlemenize yardımcı olur. Aşağıdaki proje dosyası örneği, yazı tiplerinin ayrı bir alt dizinde kaynak öğe olarak nasıl tanımlanacağını gösterir.  
  
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
> Uygulamanıza kaynak olarak yazı tipi eklediğinizde, uygulamanızın proje dosyasındaki öğesini değil `<Resource>` `<EmbeddedResource>` , öğesini ayarladığınızdan emin olun. Derleme `<EmbeddedResource>` eyleminin öğesi desteklenmiyor.  
  
 Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Koddan yazı tipi kaynak öğelerine başvurma  
 Koddan yazı tipi kaynak öğelerine başvurmak için, iki bölümlü bir yazı tipi kaynak başvurusu sağlamanız gerekir: Temel Tekdüzen Kaynak tanımlayıcısı (URI); ve yazı tipi konumu başvurusu. Bu değerler, <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntemi için parametreler olarak kullanılır. Aşağıdaki kod örneği, adlı `resources`proje alt dizinindeki uygulamanın yazı tipi kaynaklarına nasıl başvurulacağını gösterir.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Temel Tekdüzen Kaynak tanımlayıcısı (URI), yazı tipi kaynağının bulunduğu uygulama alt dizinini içerebilir. Bu durumda, yazı tipi konumu başvurusunun bir dizin belirtmesi gerekmez, ancak yazı tipi kaynağının Temel Tekdüzen Kaynak tanımlayıcısı (URI) tarafından`./`belirtilen dizinde olduğunu belirten önünde bir "" içermesi gerekir. Aşağıdaki kod örneği, yazı tipi kaynak öğesine başvurmak için alternatif bir yol gösterir; önceki kod örneğine eşdeğerdir.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Aynı uygulama alt dizininden yazı tiplerine başvurma  
 Hem uygulama içeriğini hem de kaynak dosyalarını uygulama projenizin Kullanıcı tanımlı aynı alt dizinine yerleştirebilirsiniz. Aşağıdaki proje dosyası örneği, aynı alt dizinde tanımlanan bir içerik sayfası ve yazı tipi kaynaklarını gösterir.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu uygulama içeriğine göre değişir. Aşağıdaki örneklerde, yazı tipi uygulamayla aynı dizinde olduğunda uygulamanın yazı tipi kaynağına nasıl başvurulacağını gösterilmektedir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Bir uygulamadaki yazı tiplerini numaralandırma  
 Yazı tiplerini uygulamanızdaki kaynak öğeleri olarak numaralandırmak için <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> ya <xref:System.Windows.Media.Fonts.GetTypefaces%2A> da yöntemini kullanın. Aşağıdaki örnek, uygulama yazı tipi konumundan <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> <xref:System.Windows.Media.FontFamily> nesne koleksiyonunu döndürmek için yönteminin nasıl kullanılacağını gösterir. Bu durumda, uygulama "resources" adlı bir alt dizin içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Aşağıdaki örnek, uygulama yazı tipi konumundan <xref:System.Windows.Media.Fonts.GetTypefaces%2A> <xref:System.Windows.Media.Typeface> nesne koleksiyonunu döndürmek için yönteminin nasıl kullanılacağını gösterir. Bu durumda, uygulama "resources" adlı bir alt dizin içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Yazı tipi kaynak kitaplığı oluşturma  
 Yalnızca yazı tiplerini içeren yalnızca kaynak kitaplığı oluşturabilirsiniz — kod, bu tür kitaplık projesi parçası değildir. Yalnızca kaynak kitaplığı oluşturma, kaynakları kullanan uygulama kodundan ayrılmış kaynaklar için ortak bir tekniktir. Bu Ayrıca, kitaplık derlemesinin birden çok uygulama projesine dahil edilmesini sağlar. Aşağıdaki proje dosyası örneği, kaynak kitaplığı projesinin önemli kısımlarını gösterir.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Kaynak kitaplığındaki bir yazı tipine başvurma  
 Uygulamanızdan bir kaynak kitaplığındaki bir yazı tipine başvurmak için, yazı tipi başvurusunu kitaplık derlemesinin adı ile önekle uygulamanız gerekir. Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir. Derleme adını derleme içindeki başvurudan ayırmak için '; ' karakterini kullanın. "Component" anahtar sözcüğünü ve ardından yazı tipi adının başvurusunu eklemek, yazı tipi kitaplığının kaynağına tam başvuruyu tamamlar. Aşağıdaki kod örneği, bir kaynak kitaplığı derlemesinde bir yazı tipine nasıl başvurulacağını gösterir.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Bu SDK, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarla kullanabileceğiniz örnek bir OpenType yazı tipi kümesi içerir. Yazı tipleri yalnızca kaynak kitaplığında tanımlanmıştır. Daha fazla bilgi için bkz. [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Yazı tipi kullanımı sınırlamaları  
 Aşağıdaki listede, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda yazı tiplerinin paketlenmesi ve kullanımıyla ilgili çeşitli sınırlamalar açıklanmaktadır:  
  
- **Yazı tipi ekleme izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar herhangi bir yazı tipi katıştırma izin bitlerini denetlemez veya zorlamaz. Daha fazla bilgi için [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) bölümüne bakın.  
  
- **Kaynak yazı tiplerinin sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, http veya FTP Tekdüzen Kaynak tanımlayıcısı (URI) için yazı tipi başvurusuna izin vermez.  
  
- **Paketi kullanarak mutlak URI: Gösterim:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, bir yazı tipine mutlak Tekdüzen Kaynak tanımlayıcısı <xref:System.Windows.Media.FontFamily> (URI) başvurusunun bir parçası olarak "Pack:" kullanarak bir nesne oluşturmanıza izin vermez. Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.  
  
- **Otomatik yazı tipi ekleme:** Tasarım zamanı sırasında uygulamanın yazı tipi kullanımını arama ve yazı tiplerini uygulamanın kaynaklarına otomatik olarak katıştırma desteği yoktur.  
  
- **Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, sabit olmayan belgeler için yazı tipi alt kümelerinin oluşturulmasını desteklemez.  
  
- Yanlış bir başvuru olduğu durumlarda, uygulama kullanılabilir bir yazı tipi kullanmaya geri döner.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Tipografi: bağlantılar, Haberler ve kişiler](https://docs.microsoft.com/typography/)
- [OpenType belirtimi](https://www.microsoft.com/typography/otspec/)
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Örnek OpenType Yazı Tipi Paketi](sample-opentype-font-pack.md)
