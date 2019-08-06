---
title: WPF İçinde URI'leri Paketleme
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796747"
---
# <a name="pack-uris-in-wpf"></a>WPF İçinde URI'leri Paketleme

Windows Presentation Foundation (WPF) ' [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] de, aşağıdaki gibi çeşitli yollarla dosya tanımlamak ve yüklemek için kullanılır:

- Uygulamanın ilk başladığı zaman göstermek içinöğesinibelirtme.[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]

- Görüntüler yükleniyor.

- Sayfalara gitme.

- Yürütülebilir olmayan veri dosyaları yükleniyor.

Ayrıca, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aşağıdakiler de dahil olmak üzere çeşitli konumlardan dosyaları tanımlamak ve yüklemek için de kullanılabilir:

- Geçerli derleme.

- Başvurulan bir derleme.

- Bir derlemeye göre bir konum.

- Uygulamanın kaynak sitesi.

Bu konumlardan bu dosya türlerini tanımlamaya ve yüklemeye yönelik tutarlı bir mekanizma sağlamak için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] *paket URI düzeninin*genişletilebilirliği kullanır. Bu konu, şemaya genel bir bakış sunar, çeşitli senaryolar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] için paketin nasıl oluşturulacağını ele alır, her iki biçimlendirmeden da Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 'in [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] nasıl [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kullanılacağını göstermeden önce mutlak ve göreli ve çözünürlüğe sahiptir ve kod.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Paket URI şeması

Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması, içeriği düzenlemek ve tanımlamak için bir model tanımlayan [Açık paketleme kuralları](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) belirtimi tarafından kullanılır. Bu modelin anahtar öğeleri, bir *paketin* bir veya daha fazla mantıksal *bölüm*için mantıksal bir kapsayıcı olduğu paket ve parçalardır. Aşağıdaki şekil bu kavramı gösterir.

![Paket ve parçalar diyagramı](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Bileşenleri tanımlamak için OPC belirtimi, RFC 2396 ' in genişletilebilirliği kullanır (Tekdüzen Kaynak tanımlayıcıları (URI): Genel sözdizimi), paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzenini tanımlar.

Tarafından [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] belirtilen düzen ön eki tarafından tanımlanır; http, FTP ve File iyi bilinen örneklerdir. Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması, düzeni olarak "Pack" kullanır ve iki bileşen içerir: yetkili ve yol. Bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]biçimi aşağıda verilmiştir.

Pack://*yetkilisi*/*yolu*

*Yetkili* , bir bölümün içerdiği paketin türünü belirtir. *yol* , bir paket içindeki bir bölümün konumunu belirtir.

Bu kavram aşağıdaki şekilde gösterilmiştir:

![Paket, yetkili ve yol arasındaki ilişki](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Paketler ve parçalar, uygulamalar ve dosyalarla benzerdir; burada bir uygulama (paket) bir veya daha fazla dosya (parça) içerebilir:

- Yerel derlemeye derlenen kaynak dosyaları.

- Başvurulan bir derlemeye derlenen kaynak dosyaları.

- Başvurulan bir derlemeye derlenen kaynak dosyaları.

- İçerik dosyaları.

- Kaynak dosyalarının sitesi.

Bu dosya [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] türlerine erişmek için iki kaynakçayı destekler: Application:///ve siteoforigin:///. Application:///yetkilisi, kaynak ve içerik dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyalarını tanımlar. Siteoforigin:///yetkilisi, kaynak dosyalarının sitesini tanımlar. Her bir yetkilinin kapsamı aşağıdaki şekilde gösterilmiştir.

![Paket URI diyagramı](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketin yetkili bileşeni, bir pakete işaret eden [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ve RFC 2396 ile uyumlu olması gereken bir katıştırılır. Ek olarak, "/" karakteri "," karakteriyle değiştirilmelidir ve "%" ve "?" gibi ayrılmış karakterlerle kaçışlı olmalıdır. Ayrıntılar için bkz. OPC.

Aşağıdaki bölümlerde, bu iki yetkilinin kaynak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , içerik ve kaynak dosyalarının sitesini tanımlamaya yönelik uygun yollarla birlikte nasıl kullanılacağı açıklanmaktadır.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Kaynak dosya paketi URI 'Leri

Kaynak dosyaları öğeler olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` yapılandırılır ve derlemelere derlenir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]yerel derlemeye derlenen ya da [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel derlemeden başvurulan bir derlemeye derlenen kaynak dosyalarını tanımlamak için kullanılabilen paketin oluşturulmasını destekler.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Yerel derleme kaynak dosyası

Yerel derlemeye [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derlenen bir kaynak dosyası paketi şu yetkiyi ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: Kaynak dosyasının, yolu da dahil olmak üzere, yerel derleme proje klasörü köküne göreli adı.

Aşağıdaki örnek, yerel derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün kökünde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir kaynak dosyası paketini gösterir.

`pack://application:,,,/ResourceFile.xaml`

Aşağıdaki örnek, yerel derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasöründe bulunan bir kaynak dosyası paketini gösterir.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Başvurulan derleme kaynak dosyası

Başvurulan bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derlemeye derlenen bir kaynak dosyası paketi şu yetkiyi ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: Başvurulan bir derlemeye derlenen kaynak dosyasının adı. Yolun aşağıdaki biçime uyması gerekir:

  *AssemblyShortName* { *; Sürüm*] { *; PublicKey*]; bileşen/*yol*

  - **AssemblyShortName**: başvurulan derlemenin kısa adı.

  - **; Sürüm** [isteğe bağlı]: kaynak dosyasını içeren başvurulan derlemenin sürümü. Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.

  - **; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar. Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.

  - **; bileşen**: başvurulan derlemenin yerel derlemeden başvurulduğunu belirtir.

  - **/Path**: kaynak dosyasının, yolu da dahil olmak üzere, başvurulan derlemenin proje klasörünün köküne göre adı.

Aşağıdaki örnek, başvurulan derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün kökünde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir kaynak dosyası paketini gösterir.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Aşağıdaki örnek, başvurulan derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasöründe bulunan bir kaynak dosyası paketini gösterir.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

Aşağıdaki örnek, başvurulan, sürüme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] özgü derlemenin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] proje klasörünün kök klasöründe bulunan bir kaynak dosyası paketini gösterir.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Başvurulan derleme kaynak dosyalarının [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paket sözdiziminin yalnızca Application:///yetkilisi ile kullanılabileceğini unutmayın. Örneğin, aşağıdaki ' de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]desteklenmez.

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>İçerik dosyası paketi URI 'Leri

Bir içerik [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dosyası paketi aşağıdaki yetkili ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: Uygulamanın ana yürütülebilir dosyasının dosya sistemi konumuna göreli yolu da dahil olmak üzere içerik dosyasının adı.

Aşağıdaki örnek, çalıştırılabilir derleme ile [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aynı klasörde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir içerik dosyası paketini gösterir.

`pack://application:,,,/ContentFile.xaml`

Aşağıdaki örnek, uygulamanın yürütülebilir derlemesine [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] göre bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasörde bulunan bir içerik dosyası paketini gösterir.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> HTML içerik dosyalarına gidilemez. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Düzen yalnızca kaynak sitesinde bulunan HTML dosyalarına gezinmeyi destekler.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Kaynak Paketi URI 'Leri sitesi

Kaynak dosyanın [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir sitesi paketi aşağıdaki yetkili ve yolu kullanır:

- **Yetkili**: siteoforigin:///.

- **Yol**: Yürütülebilir dosyanın başlatıldığı konuma göre yolu da dahil olmak üzere, kaynak dosya sitesinin adı.

Aşağıdaki örnek, çalıştırılabilir derlemenin başlatıldığı [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] konumda depolanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir kaynak dosyası sitesinin paketini gösterir.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

Aşağıdaki örnek, uygulamanın yürütülebilir dosyasının [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başlatıldığı konuma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] göre alt klasörde depolanan bir kaynak dosyası sitesinin paketini gösterir.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Sayfa dosyaları

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]öğeler olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` yapılandırılan dosyalar, kaynak dosyalarla aynı şekilde derlemeler halinde derlenir. Sonuç olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] , `Page` öğeler kaynak dosyaları paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kullanılarak tanımlanabilir.

Genellikle öğe olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]yapılandırılandosyatürleri kököğesiolarakaşağıdakilerdenbirinesahiptir`Page` :

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Mutlak vs. Göreli paket URI 'Leri

Tam nitelikli paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , düzeni, yetkiyi ve yolu içerir ve mutlak bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]olarak kabul edilir. Geliştiriciler için bir basitleştirme olarak, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler genellikle yalnızca yolu içeren göreli bir paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]birlikte uygun öznitelikleri ayarlamanıza olanak sağlar.

Örneğin, yerel derlemedeki bir kaynak dosyası için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki mutlak paketi göz önünde bulundurun.

`pack://application:,,,/ResourceFile.xaml`

Bu kaynak dosyasına [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran göreli paket aşağıdaki gibi olacaktır.

`/ResourceFile.xaml`

> [!NOTE]
> Kaynak dosyalarının sitesi Derlemelerle ilişkili olmadığından, yalnızca mutlak paketle [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]başvurulabilir.

Varsayılan olarak, göreli bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , başvuruyu içeren biçimlendirmenin veya kodun konumuna göre değerlendirilir. Bununla birlikte, önde gelen ters eğik çizgi kullanılırsa, göreli paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurusu uygulamanın köküne göre değerlendirilir. Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Sayfa1. xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] *kök*\SubFolder\Page2.xaml 'e başvuran bir içeriyorsa, başvuru aşağıdaki göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanabilir.

`Page2.xaml`

Sayfa1. xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] *kök*\ Page2.xaml 'e başvuran bir içeriyorsa, başvuru aşağıdaki göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanabilir.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Paket URI 'SI çözümlemesi

Paketin [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] biçimi, farklı dosya türleri için paketin [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aynı görünmesine olanak tanır. Örneğin, aşağıdaki mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]göz önünde bulundurun.

`pack://application:,,,/ResourceOrContentFile.xaml`

Bu mutlak paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , yerel derlemedeki veya bir içerik dosyasındaki bir kaynak dosyasına başvurabilir. Aynı, aşağıdaki göreli [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]için de geçerlidir.

`/ResourceOrContentFile.xaml`

Bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurduğu dosya türünü tespit etmek için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki buluşsal yöntemleri kullanarak yerel derlemelerde [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ve içerik dosyalarında kaynak dosyaları için çözümler:

1. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Paketle[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]eşleşen bir özniteliğin derleme meta verilerini araştırma.

2. Öznitelik bulunursa, paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yolu bir içerik dosyasına başvurur. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>

3. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Özniteliği bulunamazsa, yerel derlemeye derlenen küme kaynak dosyalarını araştırın.

4. Paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yoluyla eşleşen bir kaynak dosyası bulunursa, paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yolu bir kaynak dosyasına başvurur.

5. Kaynak bulunamazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz olur.

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]Aşağıdaki öğesine başvuran için [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] çözümleme uygulanmaz:

- Başvurulan derlemelerdeki içerik dosyaları: Bu dosya türleri tarafından [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]desteklenmez.

- Başvurulan derlemelerdeki gömülü dosyalar: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] bu değerler, başvurulan derlemenin `;component` ve sonekin her ikisi de dahil olduklarından benzersiz olduğunu belirler.

- Kaynak dosyalarının sitesi: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] siteoforigin:///yetkilisini içeren paket [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] tarafından tanımlanabilecek tek dosya olduklarından bunların benzersiz olduğunu belirler.

Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çözümlemenin izin verdiği bir basitleştirme, kodun kaynak ve içerik dosyalarının konumlarından çok bağımsız olmasına yöneliktir. Örneğin, yerel derlemede bir içerik dosyası olarak yeniden yapılandırılmış bir kaynak dosyanız varsa, paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanan kodla aynı şekilde kaynak paketi aynı kalır.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Paket URI 'Leri ile programlama

Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıf, paketiyle [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]birlikte ayarlanabilir özellikleri uygular, örneğin:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Bu özellikler, hem biçimlendirmeden hem de koddan ayarlanabilir. Bu bölümde her ikisi için temel kurulumlarını ve ardından yaygın senaryolar örnekleri gösterilmektedir.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Biçimlendirmede paket URI 'Leri kullanma

Bir özniteliğin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] öğesi paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ayarlanarak biçimlendirme içinde bir paket belirtilir. Örneğin:

`<element attribute="pack://application:,,,/File.xaml" />`

Tablo 1, biçimlendirmede belirtebileceğiniz çeşitli mutlak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] paketi gösterir.

Tablo 1: Işaretlemede mutlak paket URI 'Leri

|Dosya|Mutlak paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Kaynak dosya-yerel derleme|`"pack://application:,,,/ResourceFile.xaml"`|
|Alt klasör-yerel derlemede kaynak dosyası|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|Kaynak dosyası ile başvurulan derleme|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|Başvurulan derlemenin alt klasöründeki kaynak dosyası|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Sürümlü başvurulan derlemede kaynak dosyası|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|İçerik dosyası|`"pack://application:,,,/ContentFile.xaml"`|
|Alt klasördeki içerik dosyası|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|Kaynak dosyanın sitesi|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|Alt klasördeki kaynak dosyanın sitesi|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

Tablo 2 ' de, İşaretlemede [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] belirtebileceğiniz çeşitli göreli paket gösterilmektedir.

Tablo 2: Işaretlemede göreli paket URI 'Leri

|Dosya|Göreli paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Yerel derlemede kaynak dosyası|`"/ResourceFile.xaml"`|
|Yerel derlemenin alt klasöründeki kaynak dosyası|`"/Subfolder/ResourceFile.xaml"`|
|Başvurulan derlemedeki kaynak dosyası|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Başvurulan derlemenin alt klasöründeki kaynak dosyası|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|İçerik dosyası|`"/ContentFile.xaml"`|
|Alt klasördeki içerik dosyası|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Kodda paket URI 'Leri kullanma

Sınıfı örnekleyerek ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oluşturucuya bir parametre olarak geçirerek kodda bir paket belirtirsiniz. <xref:System.Uri> Bu, aşağıdaki örnekte gösterilmiştir.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Varsayılan olarak, <xref:System.Uri> sınıfı paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak kabul eder. Sonuç olarak, bir <xref:System.Uri> sınıf örneği bir göreli paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]oluşturulduğunda bir özel durum tetiklenir.

```csharp
Uri uri = new Uri("/File.xaml");
```

Neyse ki, <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> <xref:System.Uri> sınıf oluşturucusunun aşırı yüklemesi, bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mutlak ya da <xref:System.UriKind> göreli olduğunu belirtmenize izin vermek için türünde bir parametre kabul eder.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Yalnızca <xref:System.UriKind.Absolute> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ya <xref:System.UriKind.Relative> da belirtilen paketin bir veya diğeri olduğunu belirtmeniz gerekir. Kullanıcı çalışma zamanında bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] girdiğinde olduğu gibi kullanılan paketin türünü bilmiyorsanız, bunun yerine kullanın <xref:System.UriKind.RelativeOrAbsolute> .

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tablo 3 ' de kullanarak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] <xref:System.Uri?displayProperty=nameWithType>kodda belirtebileceğiniz çeşitli göreli paket gösterilmektedir.

Tablo 3: Koddaki mutlak paket URI 'Leri

|Dosya|Mutlak paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Kaynak dosya-yerel derleme|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|Alt klasör-yerel derlemede kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Kaynak dosyası ile başvurulan derleme|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|Başvurulan derlemenin alt klasöründeki kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Sürümlü başvurulan derlemede kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|İçerik dosyası|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|Alt klasördeki içerik dosyası|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|Kaynak dosyanın sitesi|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|Alt klasördeki kaynak dosyanın sitesi|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

Tablo 4 ' te, kullanarak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] <xref:System.Uri?displayProperty=nameWithType>kod içinde belirtebileceğiniz çeşitli göreli paket gösterilmektedir.

Tablo 4: Koddaki göreli paket URI 'Leri

|Dosya|Göreli paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Kaynak dosya-yerel derleme|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Alt klasör-yerel derlemede kaynak dosyası|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Kaynak dosyası ile başvurulan derleme|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Alt klasör ile başvurulan derlemede kaynak dosyası|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|İçerik dosyası|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Alt klasördeki içerik dosyası|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Ortak paket URI senaryoları

Yukarıdaki bölümlerde kaynak, içerik ve kaynak dosyalarının kaynağını [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] tanımlamak üzere paket oluşturma konusu ele alınmıştır. ' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]De, bu kurulumlarını çeşitli yollarla kullanılır ve aşağıdaki bölümlerde birçok yaygın kullanımlar ele alınmaktadır.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Uygulamanın başladığı zaman gösterilecek Kullanıcı arabirimini belirtme

<xref:System.Windows.Application.StartupUri%2A>[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında görüntülenecek olan ilkini belirtir. Tek başına uygulamalar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için, aşağıdaki örnekte gösterildiği gibi bir pencere olabilir.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Ayrıca, aşağıdaki [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] örnekte gösterildiği gibi, tek başına uygulamalar ve ilk kullanıcı arabirimi olarak bir sayfa da belirtebilir.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Uygulama tek başına bir uygulama ve bir sayfa ile <xref:System.Windows.Application.StartupUri%2A>belirtilirse, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfayı barındırmak için bir <xref:System.Windows.Navigation.NavigationWindow> açar. İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], sayfa konak tarayıcısında gösterilir.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Bir sayfaya gitme

Aşağıdaki örnek, bir sayfaya nasıl gidebileceğiniz gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]gezinmek için çeşitli yollar hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Pencere simgesi belirtme

Aşağıdaki örnek, bir pencerenin simgesini belirtmek için bir URI 'yi nasıl kullanacağınızı gösterir.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Görüntü, ses ve video dosyaları yükleniyor

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]uygulamaların, aşağıdaki örneklerde gösterildiği gibi, hepsi tarafından [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]tanımlanabilecek ve yüklenebilecek çok çeşitli medya türlerini kullanmasına olanak sağlar.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Medya içeriğiyle çalışma hakkında daha fazla bilgi için bkz. [grafik ve multimedya](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Kaynak sitesinden kaynak sözlüğü yükleme

Kaynak sözlükleri (<xref:System.Windows.ResourceDictionary>), uygulama temalarını desteklemek için kullanılabilir. Temaları oluşturmanın ve yönetmenin bir yolu, uygulamanın kaynak sitesinde bulunan kaynak sözlükleri olarak birden çok tema oluşturmaktır. Bu, bir uygulamayı yeniden derleme ve yeniden dağıtmaya gerek kalmadan temaların eklenmesini ve güncelleştirilmesini sağlar. Bu kaynak sözlükleri, aşağıdaki örnekte gösterilen Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]kullanılarak tanımlanabilir ve yüklenebilir.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

İçindeki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temalara genel bakış için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
