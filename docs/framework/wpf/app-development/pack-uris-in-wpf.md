---
title: Paket URI 'Leri
description: Windows Presentation Foundation (WPF) içindeki dosyaları tanımlamak ve yüklemek için Tekdüzen Kaynak tanımlayıcılarını (URI) kullanmanın birçok yolu hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 1d19dec0d846659f8de6ed518a7f98d224354a82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621697"
---
# <a name="pack-uris-in-wpf"></a>WPF İçinde URI'leri Paketleme

Windows Presentation Foundation (WPF) içinde, aşağıdaki gibi çeşitli yollarla dosya tanımlamak ve yüklemek için Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanılır:

- [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]Uygulamanın ilk başladığı zaman göstermek için öğesini belirtme.

- Görüntüler yükleniyor.

- Sayfalara gitme.

- Yürütülebilir olmayan veri dosyaları yükleniyor.

Ayrıca, URI 'Ler aşağıdakiler de dahil olmak üzere çeşitli konumlardan dosyaları tanımlamak ve yüklemek için kullanılabilir:

- Geçerli derleme.

- Başvurulan bir derleme.

- Bir derlemeye göre bir konum.

- Uygulamanın kaynak sitesi.

Bu konumlardan bu dosya türlerini tanımlamaya ve yüklemeye yönelik tutarlı bir mekanizma sağlamak için WPF, *paket URI düzeninin*genişletilebilirliği kullanır. Bu konu, şemaya genel bir bakış sağlar ve çeşitli senaryolar için paket URI 'Lerinin nasıl kullanılacağını ele alır. her iki biçimlendirme ve koddan paket URI 'Lerinin nasıl kullanılacağını göstermeden önce mutlak ve göreli URI 'Ler ve URI çözümlemesini açıklar.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Paket URI şeması

Paket URI şeması, içeriği düzenlemek ve tanımlamak için bir model tanımlayan [Açık paketleme kuralları](https://www.ecma-international.org/publications/standards/Ecma-376.htm) (OPC) belirtimi tarafından kullanılır. Bu modelin anahtar öğeleri, bir *paketin* bir veya daha fazla mantıksal *bölüm*için mantıksal bir kapsayıcı olduğu paket ve parçalardır. Aşağıdaki şekil bu kavramı gösterir.

![Paket ve parçalar diyagramı](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

OPC belirtimi, parçaları belirlemek için, paket URI düzenini tanımlamak üzere RFC 2396 (Tekdüzen Kaynak tanımlayıcıları (URI): genel sözdizimi) genişletilebilirliği kullanır.

Bir URI tarafından belirtilen düzen ön eki tarafından tanımlanır; http, FTP ve dosya iyi bilinen örneklerdir. Paket URI şeması, düzeni olarak "Pack" kullanır ve iki bileşen içerir: yetkili ve yol. Paket URI 'sinin biçimi aşağıda verilmiştir.

Pack://*yetkilisi* / *yolu*

*Yetkili* , bir bölümün içerdiği paketin türünü belirtir. *yol* , bir paket içindeki bir bölümün konumunu belirtir.

Bu kavram aşağıdaki şekilde gösterilmiştir:

![Paket, yetkili ve yol arasındaki ilişki](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Paketler ve parçalar, uygulamalar ve dosyalarla benzerdir; burada bir uygulama (paket) bir veya daha fazla dosya (parça) içerebilir:

- Yerel derlemeye derlenen kaynak dosyaları.

- Başvurulan bir derlemeye derlenen kaynak dosyaları.

- Başvurulan bir derlemeye derlenen kaynak dosyaları.

- İçerik dosyaları.

- Kaynak dosyalarının sitesi.

Bu dosya türlerine erişmek için WPF iki kaynakçayı destekler: application:///ve siteoforigin:///. Application:///yetkilisi, kaynak ve içerik dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyalarını tanımlar. Siteoforigin:///yetkilisi, kaynak dosyalarının sitesini tanımlar. Her bir yetkilinin kapsamı aşağıdaki şekilde gösterilmiştir.

![Paket URI diyagramı](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Bir paket URI 'sinin yetkili bileşeni, bir paketi işaret eden ve RFC 2396 ' e uyması gereken gömülü bir URI 'dir. Ek olarak, "/" karakteri "," karakteriyle değiştirilmelidir ve "%" ve "?" gibi ayrılmış karakterlerle kaçışlı olmalıdır. Ayrıntılar için bkz. OPC.

Aşağıdaki bölümlerde, bu iki yetkilinin kaynağını, içeriğini ve kaynak dosyalarının sitesini tanımlamaya yönelik uygun yollarla birlikte kullanarak paket URI 'Lerinin nasıl oluşturulduğu açıklanmaktadır.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Kaynak dosya paketi URI 'Leri

Kaynak dosyaları MSBuild öğeleri olarak yapılandırılır `Resource` ve derlemelere derlenir. WPF, yerel derlemeye derlenen ya da yerel derlemeden başvurulan bir derlemeye derlenen kaynak dosyalarını tanımlamak için kullanılabilen paket URI 'lerinin oluşturulmasını destekler.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Yerel derleme kaynak dosyası

Yerel derlemeye derlenen bir kaynak dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: kaynak dosyanın, yolu da dahil olmak üzere yerel derleme proje klasörü köküne göreli adı.

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Yerel derlemenin proje klasörünün kökünde bulunan bir kaynak dosyası için paket URI 'sini gösterir.

`pack://application:,,,/ResourceFile.xaml`

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Yerel derlemenin proje klasörünün bir alt klasöründe bulunan bir kaynak dosyası için paket URI 'sini gösterir.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Başvurulan derleme kaynak dosyası

Başvurulan bir derlemeye derlenen bir kaynak dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: başvurulan bir derlemeye derlenen kaynak dosyasının adı. Yolun aşağıdaki biçime uyması gerekir:

  *AssemblyShortName*{*; Sürüm*] {*; PublicKey*]; bileşen/*yol*

  - **AssemblyShortName**: başvurulan derlemenin kısa adı.

  - **; Sürüm** [isteğe bağlı]: kaynak dosyasını içeren başvurulan derlemenin sürümü. Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.

  - **; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar. Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.

  - **; bileşen**: başvurulan derlemenin yerel derlemeden başvurulduğunu belirtir.

  - **/Path**: kaynak dosyasının, yolu da dahil olmak üzere, başvurulan derlemenin proje klasörünün köküne göre adı.

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün kökünde bulunan bir kaynak dosyası için paket URI 'sini gösterir.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün bir alt klasöründe bulunan bir kaynak dosyası için paket URI 'sini gösterir.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan, sürüme özgü derlemenin proje klasörünün kök klasöründe bulunan bir kaynak dosyası için paket URI 'sini gösterir.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Başvurulan derleme kaynak dosyalarının paket URI sözdiziminin yalnızca application:///yetkilisi ile kullanılabileceğini unutmayın. Örneğin, WPF 'de aşağıdakiler desteklenmez.

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>İçerik dosyası paketi URI 'Leri

Bir içerik dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:

- **Yetkili**: Application:///.

- **Yol**: uygulamanın ana yürütülebilir dosyasının dosya sistemi konumuna göreli yolu da dahil olmak üzere içerik dosyasının adı.

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalıştırılabilir derleme ile aynı klasörde bulunan bir içerik dosyası için paket URI 'sini gösterir.

`pack://application:,,,/ContentFile.xaml`

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın yürütülebilir derlemesine göre bir alt klasörde bulunan bir içerik dosyası için paket URI 'sini gösterir.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> HTML içerik dosyalarına gidilemez. URI şeması yalnızca kaynak sitesinde bulunan HTML dosyalarına gezinmeyi destekler.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Kaynak Paketi URI 'Leri sitesi

Kaynak dosyanın bir sitesi için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:

- **Yetkili**: siteoforigin:///.

- **Yol**: kaynak dosyanın, yürütülebilir derlemenin başlatıldığı konuma göre yolu da dahil olmak üzere adı.

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalıştırılabilir derlemenin başlatıldığı konumda depolanan bir kaynak dosyası sitesinin paket URI 'sini gösterir.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın yürütülebilir dosyasının başlatıldığı konuma göre alt klasörde depolanan bir kaynak dosyası sitesinin paket URI 'sini gösterir.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Sayfa dosyaları

MSBuild öğeleri olarak yapılandırılmış XAML dosyaları `Page` , kaynak dosyalarla aynı şekilde derlemeler halinde derlenir. Sonuç olarak, MSBuild `Page` öğeleri, kaynak dosyaları için Pack URI 'leri kullanılarak tanımlanabilir.

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Genellikle MSBuild öğeleri olarak yapılandırılan dosya türleri, `Page` kök öğesi olarak aşağıdakilerden birine sahiptir:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Mutlak ve göreli paket URI 'Leri

Tam bir paket URI şeması, yetkiyi ve yolu içerir ve mutlak paket URI 'SI olarak kabul edilir. Geliştiriciler için bir basitleştirme olarak, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler genellikle yalnızca yolu içeren göreli bir paket URI 'si ile uygun öznitelikleri ayarlamanıza olanak sağlar.

Örneğin, yerel derlemedeki bir kaynak dosyası için aşağıdaki mutlak paket URI 'sini göz önünde bulundurun.

`pack://application:,,,/ResourceFile.xaml`

Bu kaynak dosyasına başvuran göreli paket URI 'SI aşağıdaki gibi olacaktır.

`/ResourceFile.xaml`

> [!NOTE]
> Kaynak dosyalarının sitesi Derlemelerle ilişkili olmadığından, yalnızca mutlak paket URI 'Leri ile başvurulabilirler.

Varsayılan olarak, göreli bir paket URI 'SI, başvuruyu içeren biçimlendirmenin veya kodun konumuna göre değerlendirilir. Bununla birlikte, önde gelen ters eğik çizgi kullanılırsa, göreli paket URI başvurusu daha sonra uygulamanın köküne göre değerlendirilir. Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Sayfa1. xaml *kök*\Subfolder\page2.xaml 'e başvuran bir URI içeriyorsa, başvuru aşağıdaki GÖRELI paket URI 'sini kullanabilir.

`Page2.xaml`

Sayfa1. xaml, *kök*\ Page2.xaml 'e başvuran bir URI içeriyorsa, başvuru aşağıdaki GÖRELI paket URI 'sini kullanabilir.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Paket URI 'SI çözümlemesi

Paket URI 'Leri biçimi, farklı dosya türleri için paket URI 'Lerinin aynı görünmesine olanak tanır. Örneğin, aşağıdaki mutlak paket URI 'sini göz önünde bulundurun.

`pack://application:,,,/ResourceOrContentFile.xaml`

Bu mutlak paket URI 'SI, yerel derlemedeki veya bir içerik dosyasındaki bir kaynak dosyasına başvurabilir. Aynı, aşağıdaki göreli URI için de geçerlidir.

`/ResourceOrContentFile.xaml`

Bir paket URI 'sinin başvurduğu dosya türünü belirleyebilmek için WPF, aşağıdaki buluşsal yöntemleri kullanarak yerel derlemelerdeki ve içerik dosyalarındaki kaynak dosyaları için URI 'Leri çözümler:

1. Paket URI 'siyle eşleşen bir özniteliğin derleme meta verilerini araştırma <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .

2. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>Öznitelik bulunursa, paket URI 'si yolu bir içerik dosyası anlamına gelir.

3. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>Özniteliği bulunamazsa, yerel derlemeye derlenen küme kaynak dosyalarını araştırın.

4. Paket URI 'SI yoluyla eşleşen bir kaynak dosyası bulunursa, paket URI 'sinin yolu bir kaynak dosyasına başvurur.

5. Kaynak bulunamazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz olur.

URI çözümlemesi, aşağıdakilere başvuran URI 'Ler için uygulanmaz:

- Başvurulan derlemelerdeki içerik dosyaları: Bu dosya türleri WPF tarafından desteklenmez.

- Başvurulan derlemelerdeki gömülü dosyalar: başvurulan derlemenin ve sonekin her ikisi de dahil olduklarından, bunları tanımlayan URI 'Ler benzersizdir `;component` .

- Kaynak dosyalarının sitesi: siteoforigin:///yetkilisini içeren paket URI 'Leri tarafından tanımlanabilecek tek dosya olduklarından, bunları tanımlayan URI 'Ler benzersizdir.

Paket URI 'SI çözümlemenin izin verdiği bir basitleştirmeli, kodun kaynak ve içerik dosyalarının konumlarından bağımsız olması için kod içindir. Örneğin, yerel derlemede bir içerik dosyası olarak yeniden yapılandırılmış bir kaynak dosyanız varsa, paket URI 'sini kullanan kod gibi, kaynağın paket URI 'SI aynı kalır.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Paket URI 'Leri ile programlama

Birçok WPF sınıfı, aşağıdakiler dahil olmak üzere paket URI 'Leri ile ayarlanabilir özellikleri uygular:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Bu özellikler, hem biçimlendirmeden hem de koddan ayarlanabilir. Bu bölümde her ikisi için temel kurulumlarını ve ardından yaygın senaryolar örnekleri gösterilmektedir.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Biçimlendirmede paket URI 'Leri kullanma

Paket URI 'si olan bir özniteliğin öğesi ayarlanarak, biçimlendirmede bir paket URI 'SI belirtilir. Örneğin:

`<element attribute="pack://application:,,,/File.xaml" />`

Tablo 1 ' de, İşaretlemede belirtebileceğiniz çeşitli mutlak paket URI 'Leri gösterilmektedir.

Tablo 1: biçimlendirmede mutlak paket URI 'Leri

|Dosya|Mutlak paket URI 'SI|
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

Tablo 2 ' de, biçimlendirmede belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir.

Tablo 2: biçimlendirmede göreli paket URI 'Leri

|Dosya|Göreli paket URI 'SI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Yerel derlemede kaynak dosyası|`"/ResourceFile.xaml"`|
|Yerel derlemenin alt klasöründeki kaynak dosyası|`"/Subfolder/ResourceFile.xaml"`|
|Başvurulan derlemedeki kaynak dosyası|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Başvurulan derlemenin alt klasöründeki kaynak dosyası|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|İçerik dosyası|`"/ContentFile.xaml"`|
|Alt klasördeki içerik dosyası|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Kodda paket URI 'Leri kullanma

Sınıfın örneğini oluşturarak <xref:System.Uri> ve PAKETI URI 'sini oluşturucuya bir parametre olarak geçirerek kodda bir paket URI 'si belirtirsiniz. Bu, aşağıdaki örnekte gösterilmiştir.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Varsayılan olarak, <xref:System.Uri> sınıfı paket URI 'lerinin mutlak olduğunu varsayar. Sonuç olarak, bir sınıf örneği bir <xref:System.Uri> göreli paket URI 'si ile oluşturulduğunda bir özel durum tetiklenir.

```csharp
Uri uri = new Uri("/File.xaml");
```

Neyse ki <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> sınıf oluşturucusunun aşırı yüklemesi, <xref:System.Uri> <xref:System.UriKind> bir paket URI 'sinin mutlak veya göreli olduğunu belirtmenize izin vermek için türünde bir parametre kabul eder.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Yalnızca <xref:System.UriKind.Absolute> veya <xref:System.UriKind.Relative> diğer bir paket URI 'sinin bir veya diğeri olduğundan emin olmanız gerekir. Kullanıcı çalışma zamanında bir paket URI 'SI girdiğinde olduğu gibi, kullanılan paket URI türünü bilmiyorsanız, <xref:System.UriKind.RelativeOrAbsolute> bunun yerine kullanın.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tablo 3 ' de kullanarak kodda belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir <xref:System.Uri?displayProperty=nameWithType> .

Tablo 3: koddaki mutlak paket URI 'Leri

|Dosya|Mutlak paket URI 'SI|
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

Tablo 4 ' te, kullanarak kod içinde belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir <xref:System.Uri?displayProperty=nameWithType> .

Tablo 4: koddaki göreli paket URI 'Leri

|Dosya|Göreli paket URI 'SI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Kaynak dosya-yerel derleme|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Alt klasör-yerel derlemede kaynak dosyası|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Kaynak dosyası ile başvurulan derleme|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Alt klasör ile başvurulan derlemede kaynak dosyası|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|İçerik dosyası|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Alt klasördeki içerik dosyası|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Ortak paket URI senaryoları

Önceki bölümlerde kaynak, içerik ve kaynak dosyalarının kaynağını tanımlamak için paket URI 'Leri oluşturma konusu ele alınmıştır. WPF 'de, bu kurulumlarını çeşitli yollarla kullanılır ve aşağıdaki bölümlerde birçok yaygın kullanım kullanımı ele alınmaktadır.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Uygulamanın başladığı zaman gösterilecek Kullanıcı arabirimini belirtme

<xref:System.Windows.Application.StartupUri%2A>[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]WPF uygulaması başlatıldığında ilk gösterilecek olan öğesini belirtir. Tek başına uygulamalar için, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Aşağıdaki örnekte gösterildiği gibi bir pencere olabilir.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Tek başına uygulamalar ve XAML tarayıcı uygulamaları (XBAP 'ler), aşağıdaki örnekte gösterildiği gibi ilk kullanıcı arabirimi olarak bir sayfa da belirtebilir.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Uygulama bağımsız bir uygulamadır ve ile bir sayfa belirtilirse <xref:System.Windows.Application.StartupUri%2A> , WPF <xref:System.Windows.Navigation.NavigationWindow> sayfayı barındırmak için bir açar. XBAP 'ler için, sayfa konak tarayıcısında gösterilir.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Bir sayfaya gitme

Aşağıdaki örnek, bir sayfaya nasıl gidebileceğiniz gösterilmektedir.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

WPF 'de gezinmek için çeşitli yollar hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Pencere simgesi belirtme

Aşağıdaki örnek, bir pencerenin simgesini belirtmek için bir URI 'yi nasıl kullanacağınızı gösterir.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Görüntü, ses ve video dosyaları yükleniyor

WPF, uygulamaların, her biri aşağıdaki örneklerde gösterildiği gibi, paket URI 'leriyle tanımlanabilecek ve yüklenebilecek çok çeşitli medya türlerini kullanmasına olanak sağlar.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Medya içeriğiyle çalışma hakkında daha fazla bilgi için bkz. [grafik ve multimedya](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Kaynak sitesinden kaynak sözlüğü yükleme

Kaynak sözlükleri ( <xref:System.Windows.ResourceDictionary> ), uygulama temalarını desteklemek için kullanılabilir. Temaları oluşturmanın ve yönetmenin bir yolu, uygulamanın kaynak sitesinde bulunan kaynak sözlükleri olarak birden çok tema oluşturmaktır. Bu, bir uygulamayı yeniden derleme ve yeniden dağıtmaya gerek kalmadan temaların eklenmesini ve güncelleştirilmesini sağlar. Bu kaynak sözlükleri, aşağıdaki örnekte gösterilen Pack URI 'Leri kullanılarak tanımlanabilir ve yüklenebilir.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

WPF 'deki temalara genel bakış için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
