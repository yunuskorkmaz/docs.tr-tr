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
# <a name="packaging-fonts-with-applications"></a>Uygulamalarla Yazı Tiplerini Paketleme
Bu konu, uygulamanızla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tiplerini nasıl paketleeceğine genel bir bakış sağlar.  
  
> [!NOTE]
> Çoğu yazılım türünde olduğu gibi, yazı tipi dosyaları satılmak yerine lisanslanır. Yazı tiplerinin kullanımını yöneten lisanslar satıcıdan satıcıya değişir, ancak Microsoft'un uygulamaları ve Windows ile sağladığı yazı tiplerini kapsayanlar da dahil olmak üzere genel olarak çoğu lisans, yazı tiplerinin uygulamalara katıştırılmasına veya başka bir şekilde yeniden dağıtılmasına izin vermez. Bu nedenle, bir geliştirici olarak, bir uygulamanın içine katıştırdığınız veya başka bir şekilde yeniden dağıttığınız herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Ambalaj Yazı Tiplerine Giriş  
 Kullanıcı arabirimi metnini ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer metin tabanlı içerik türlerini görüntülemek için yazı tiplerini uygulamalarınızda kaynak olarak kolayca paketleyebilirsiniz. Yazı tipleri, uygulamanın derleme dosyalarından ayrılabilir veya içine katışabilir. Ayrıca, uygulamanızın başvuruedebileceği yalnızca kaynak yazı tipi kitaplığı da oluşturabilirsiniz.  
  
 OpenType ve TrueType® yazı tipleri, yazı tipi için yazı tipi katıştırma lisanslama haklarını gösteren bir tür bayrağı, fsType içerir. Ancak, bu tür bayrağı yalnızca bir belgede depolanan katışılmış yazı tiplerini ifade eder-bir uygulamaya katışılmış yazı tiplerine atıfta bulunmaz. Bir <xref:System.Windows.Media.GlyphTypeface> nesne oluşturup <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> özelliğine başvurarak yazı tipi nin yazı tipi katıştırma haklarını alabilirsiniz. fsType bayrağı hakkında daha fazla bilgi için [OpenType Belirtimi'nin](https://www.microsoft.com/typography/otspec/os2.htm) "OS/2 ve Windows Ölçümleri" bölümüne bakın.  
  
 [Microsoft Tipografi](https://docs.microsoft.com/typography/) Web sitesi, belirli bir yazı tipi satıcısını bulmanıza veya özel çalışma için bir yazı tipi satıcısı bulmanıza yardımcı olabilecek kişi bilgileri içerir.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>İçerik Öğesi Olarak Yazı Tipleri Ekleme  
 Uygulamanıza, uygulamanın derleme dosyalarından ayrı proje içerik öğeleri olarak yazı tipleri ekleyebilirsiniz. Bu, içerik öğelerinin derleme içinde kaynak olarak katıştırılmış olmadığı anlamına gelir. Aşağıdaki proje dosyası örneği, içerik öğelerinin nasıl tanımlandığını gösterir.  
  
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
  
 Uygulamanın çalışma zamanında yazı tiplerini kullanabilmesini sağlamak için, yazı tiplerine uygulamanın dağıtım dizininde erişilebilir olması gerekir. Uygulamanın proje dosyasındaki öğe, `<CopyToOutputDirectory>` yapı işlemi sırasında yazı tiplerini otomatik olarak uygulama dağıtım dizinine kopyalamanızı sağlar. Aşağıdaki proje dosyası örneği, yazı tiplerinin dağıtım dizinine nasıl kopyalanış yapılacağını gösterir.  
  
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
  
 Aşağıdaki kod örneği, uygulamanın yazı tipine içerik öğesi olarak nasıl başvuruleceğini gösterir- başvurulan içerik öğesi, uygulamanın derleme dosyalarıyla aynı dizinde olmalıdır.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>Kaynak Öğesi Olarak Yazı Tipleri Ekleme  
 Uygulamanıza, uygulamanın derleme dosyalarına katıştırılmış proje kaynağı öğeleri olarak yazı tipleri ekleyebilirsiniz. Kaynaklar için ayrı bir alt dizini kullanmak, uygulamanın proje dosyalarını düzenlemeye yardımcı olur. Aşağıdaki proje dosyası örneği, yazı tiplerinin ayrı bir alt dizinde kaynak öğeleri olarak nasıl tanımlanır gösteriş olduğunu gösterir.  
  
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
> Uygulamanıza kaynak olarak yazı tipleri eklediğinizde, uygulamanızın `<Resource>` proje dosyasındaki `<EmbeddedResource>` öğeyi değil, öğeyi ayarladığınızdan emin olun. Yapı `<EmbeddedResource>` eylemi öğesi desteklenmez.  
  
 Aşağıdaki biçimlendirme örneği, uygulamanın yazı tipi kaynaklarına nasıl başvurulup başvurulmayı gösterir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Koddan Yazı Tipi Kaynak Öğelerine Başvurma  
 Koddan yazı tipi kaynak öğelerine başvurmak için iki parçalı yazı tipi kaynak başvurusu sağlamanız gerekir: temel tekdüzen kaynak tanımlayıcısı (URI); ve yazı tipi konumu başvurusu. Bu değerler <xref:System.Windows.Media.FontFamily.%23ctor%2A> yöntem için parametre olarak kullanılır. Aşağıdaki kod örneği, uygulamanın yazı tipi kaynaklarına proje alt `resources`dizininde nasıl başvuruldu:  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Temel tekdüzen kaynak tanımlayıcısı (URI), yazı tipi kaynağının bulunduğu uygulama alt dizinini içerebilir. Bu durumda, yazı tipi konumu başvurusu bir dizin belirtmek gerekmez, ancak`./`yazı tipi kaynağı temel tekdüzen kaynak tanımlayıcı (URI) tarafından belirtilen aynı dizinde olduğunu gösteren bir satır aralığı " ", eklemek gerekir. Aşağıdaki kod örneği, yazı tipi kaynak öğesine başvurmanın alternatif bir yolunu gösterir ve önceki kod örneğine eşdeğerdir.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Aynı Uygulama Alt Dizini'nden Yazı Tiplerine Başvurma  
 Hem uygulama içeriğini hem de kaynak dosyalarını uygulama projenizin aynı kullanıcı tanımlı alt dizinine yerleştirebilirsiniz. Aşağıdaki proje dosyası örneği, aynı alt dizinde tanımlanan bir içerik sayfası ve yazı tipi kaynaklarını gösterir.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Uygulama içeriği ve yazı tipi aynı alt dizinde olduğundan, yazı tipi başvurusu uygulama içeriğine göredir. Aşağıdaki örnekler, yazı tipi uygulamayla aynı dizinde olduğunda uygulamanın yazı tipi kaynağına nasıl başvurulsüreceğini gösterir.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Uygulamada Yazı Tiplerini Sayısallandırma  
 Uygulamanızda yazı tiplerini kaynak öğesi olarak sıralamak <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> için, ya yöntemi kullanın. <xref:System.Windows.Media.Fonts.GetTypefaces%2A> Aşağıdaki örnek, uygulama fontu konumundan <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> <xref:System.Windows.Media.FontFamily> nesnelerin koleksiyonunu döndürmek için yöntemin nasıl kullanılacağını gösterir. Bu durumda, uygulama "kaynaklar" adlı bir alt dizini içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Aşağıdaki örnek, uygulama fontu konumundan <xref:System.Windows.Media.Fonts.GetTypefaces%2A> <xref:System.Windows.Media.Typeface> nesnelerin koleksiyonunu döndürmek için yöntemin nasıl kullanılacağını gösterir. Bu durumda, uygulama "kaynaklar" adlı bir alt dizini içerir.  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Yazı Tipi Kaynak Kitaplığı Oluşturma  
 Yalnızca yazı tipleri içeren yalnızca kaynak kitaplığı oluşturabilirsiniz—hiçbir kod bu tür kitaplık projesinin bir parçası değildir. Yalnızca kaynak kitaplığı oluşturmak, kaynakları bunları kullanan uygulama kodundan ayırmak için yaygın bir tekniktir. Bu, kitaplık derlemesinin birden çok uygulama projesine dahil edilmesine de olanak tanır. Aşağıdaki proje dosyası örneği, yalnızca kaynak kitaplığı projesinin önemli bölümlerini gösterir.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Kaynak Kitaplığında Yazı Tipine Başvurma  
 Uygulamanızdan kaynak kitaplığındaki bir yazı tipine başvurmak için yazı tipi başvurusunu kitaplık derlemesinin adıyla önetürmelisiniz. Bu durumda, yazı tipi kaynak derlemesi "FontLibrary" dir. Derleme adını derleme içindeki başvurudan ayırmak için bir ';' karakter kullanın. Yazı tipi adına başvurunun ardından "Bileşen" anahtar sözcüğünün eklenmesi, yazı tipi kitaplığı kaynağına yapılan başvurunun tamamını tamamlar. Aşağıdaki kod örneği, kaynak kitaplığı derlemesinde bir yazı tipine nasıl başvurulyur gösteriş yapar.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Bu SDK, uygulamalarla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birlikte kullanabileceğiniz bir örnek OpenType yazı tipleri kümesi içerir. Yazı tipleri yalnızca kaynak kitaplığında tanımlanır. Daha fazla bilgi için [Örnek OpenType Yazı Tipi Paketi'ne](sample-opentype-font-pack.md)bakın.  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Font Kullanımındaki Sınırlamalar  
 Aşağıdaki liste, uygulamalarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tiplerinin paketlenmesi ve kullanımıyla ilgili çeşitli sınırlamaları açıklamaktadır:  
  
- **Yazı tipi katıştırma izin bitleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar herhangi bir yazı tipi katıştırma izin bitlerini denetlemez veya zorlamaz. Daha fazla bilgi için [Introduction_to_Packing Fontları](#introduction_to_packaging_fonts) bölümüne bakın.  
  
- **Kaynak yazı tipleri sitesi:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar bir http veya ftp üniforma kaynak tanımlayıcısına (URI) yazı tipi başvurusuna izin vermez.  
  
- **Paketi kullanarak Mutlak URI: gösterim:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar bir yazı <xref:System.Windows.Media.FontFamily> tipi için mutlak tekdüzen kaynak tanımlayıcısı (URI) referans parçası olarak "pack:" kullanarak programlı bir nesne oluşturmak için izin vermez. Örneğin, `"pack://application:,,,/resources/#Pericles Light"` geçersiz bir yazı tipi başvurusudur.  
  
- **Otomatik yazı tipi katıştırma:** Tasarım süresi boyunca, bir uygulamanın yazı tiplerini kullanımını aramak ve yazı tiplerini uygulamanın kaynaklarına otomatik olarak katıştırma desteği yoktur.  
  
- **Yazı tipi alt kümeleri:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar sabit olmayan belgeler için yazı tipi alt kümelerinin oluşturulmasını desteklemez.  
  
- Yanlış başvuru nun olduğu durumlarda, uygulama kullanılabilir bir yazı tipini kullanmaya geri döner.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Tipografisi: Bağlantılar, Haberler ve Kişiler](https://docs.microsoft.com/typography/)
- [OpenType Belirtimi](https://www.microsoft.com/typography/otspec/)
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Örnek OpenType Yazı Tipi Paketi](sample-opentype-font-pack.md)
