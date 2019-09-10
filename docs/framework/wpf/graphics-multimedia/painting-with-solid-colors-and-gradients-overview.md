---
title: Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: fb6b7da4be46f361b263c573339b1a6b73ef24bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855892"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış

Bu konuda <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, ve <xref:System.Windows.Media.RadialGradientBrush> nesnelerinin, düz renkler, doğrusal degradeler ve radyal gradyanlar ile boyamak için nasıl kullanılacağı açıklanmaktadır.

<a name="solidcolor"></a>

## <a name="painting-an-area-with-a-solid-color"></a>Düz renk ile bir alanı boyama

Herhangi bir platformda en yaygın işlemlerden biri, bir alanı Solid <xref:System.Windows.Media.Color>ile boyamak. Bu görevi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] gerçekleştirmek için <xref:System.Windows.Media.SolidColorBrush> sınıfını sağlar. Aşağıdaki bölümlerde, ile <xref:System.Windows.Media.SolidColorBrush>boyamak için farklı yollar açıklanır.

<a name="solidcolorinxaml"></a>

### <a name="using-a-solidcolorbrush-in-xaml"></a>"XAML" içinde bir SolidColorBrush kullanma

İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]düz bir renkle bir alanı boyamak için, aşağıdaki seçeneklerden birini kullanın.

- Ada göre önceden tanımlanmış bir düz renk fırçası seçin.  Örneğin, bir düğmeyi <xref:System.Windows.Controls.Control.Background%2A> "Red" veya "düz mavi" olarak ayarlayabilirsiniz.  Önceden tanımlanmış diğer düz renk fırçalarının bir listesi için, <xref:System.Windows.Media.Brushes> sınıfının statik özelliklerine bakın. Bir örnek verilmiştir.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]

- Tek bir düz renk halinde birleştirilecek kırmızı, yeşil ve mavi miktarlarını belirterek 32 bitlik renk paletinden bir renk seçin.  32-bit paletten bir renk belirtme biçimi " *#rrggbb*", burada *RR* , göreli miktarı belirten iki basamaklı bir onaltılık sayıdır, *gg* ise yeşil miktarını belirtir ve *BB* miktarı mavi olarak belirtir.  Ayrıca, renk "#*aarrggbb*" olarak belirtilebilir, burada *AA* rengin *Alfa* değerini ya da saydamlığını belirtir. Bu yaklaşım, kısmen saydam renkler oluşturmanıza olanak sağlar.  Aşağıdaki örnekte, bir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> , onaltılık gösterim kullanılarak tamamen opak kırmızı olarak ayarlanmıştır.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]

- Bir <xref:System.Windows.Media.SolidColorBrush>açıklaması için özellik etiketi sözdizimini kullanın. Bu sözdizimi daha ayrıntılıdır, ancak fırçanın geçirgenliği gibi ek ayarlar belirtmenize olanak sağlar. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> iki <xref:System.Windows.Controls.Button> öğenin özellikleri tam opak kırmızı olarak ayarlanmıştır. İlk fırçanın rengi önceden tanımlanmış bir renk adı kullanılarak açıklanmıştır. İkinci fırçanın rengi onaltılık gösterim kullanılarak açıklanmıştır.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]

<a name="solidcolorsincode"></a>

### <a name="painting-with-a-solidcolorbrush-in-code"></a>Koddaki SolidColorBrush ile boyama

Kodda bir düz renk ile bir alanı boyamak için, aşağıdaki seçeneklerden birini kullanın.

- <xref:System.Windows.Media.Brushes> Sınıfı tarafından sunulan önceden tanımlanmış fırçalardan birini kullanın. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> öğesinin ' i olarak <xref:System.Windows.Media.Brushes.Red%2A>ayarlanır.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]

- Bir <xref:System.Windows.Media.SolidColorBrush> Yapı<xref:System.Windows.Media.Color> kullanarak bir oluşturun <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve özelliğini ayarlayın. <xref:System.Windows.Media.Colors> Sınıfından önceden tanımlanmış bir renk kullanabilir veya statik <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi <xref:System.Windows.Media.Color> kullanarak oluşturabilirsiniz.

  Aşağıdaki örnek, bir <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> öğesinin özelliğinin önceden tanımlanmış bir renk kullanılarak nasıl ayarlanacağını gösterir.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]

Statik <xref:System.Windows.Media.Color.FromArgb%2A> , rengin alfa, kırmızı, yeşil ve mavi değerlerini belirtmenize olanak sağlar. Bu değerlerin her biri için tipik Aralık 0-255 ' dir. Örneğin, bir alfa değeri bir rengin tamamen saydam olduğunu, 255 değeri ise rengin tamamen opak olduğunu gösterir. Benzer şekilde, kırmızı değeri 0 değerinde bir rengin kırmızı olmadığını gösterir. 255 değeri, bir rengin olası en yüksek miktarda kırmızı olduğunu gösterir.  Aşağıdaki örnekte, bir fırçanın rengi alfa, kırmızı, yeşil ve mavi değerler belirtilerek açıklanmıştır.

[!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]

Renk belirtmek için ek yollar için <xref:System.Windows.Media.Color> başvuru konusuna bakın.

<a name="gradient"></a>

## <a name="painting-an-area-with-a-gradient"></a>Gradyan ile bir alanı boyama

Gradyan fırçası, bir eksen üzerinde birbirine karışan birden çok renge sahip bir alanı boyar. Bunları, denetimlerinizi üç boyutlu bir fikir vererek ışığın ve gölgenin etkili bir şekilde oluşturulmasını sağlamak için kullanabilirsiniz. Bunları cam, Chrome, su ve diğer kesintisiz yüzeylerin benzetimini yapmak için de kullanabilirsiniz.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]iki tür gradyan fırçaları sağlar: <xref:System.Windows.Media.LinearGradientBrush> ve. <xref:System.Windows.Media.RadialGradientBrush>

<a name="lineargradientbrush"></a>

## <a name="linear-gradients"></a>Doğrusal degradeler

Bir <xref:System.Windows.Media.LinearGradientBrush> çizgi, *gradyan ekseni*ve çizgi üzerinde tanımlanan degradeyle bir alanı boyar.  Degradenin renklerini ve konumlarını nesneleri kullanarak <xref:System.Windows.Media.GradientStop> gradyan ekseni üzerinde belirtirsiniz.  Ayrıca, yatay ve dikey degradeler oluşturmanızı ve Gradyan yönünü ters çevirmeyi sağlayan gradyan eksenini de değiştirebilirsiniz. Gradyan ekseni sonraki bölümde açıklanmaktadır. Varsayılan olarak, köşegen bir gradyan oluşturulur.

Aşağıdaki örnek dört renkle doğrusal bir gradyan oluşturan kodu gösterir.

[!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]

Bu kod aşağıdaki degradeyi üretir:

![Köşegen doğrusal gradyan](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")

> [!NOTE]
> Bu konudaki gradyan örnekleri, başlangıç noktalarını ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemini kullanır. Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' unu gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir. <xref:System.Windows.Media.GradientBrush.MappingMode%2A> Özelliği değerine<xref:System.Windows.Media.BrushMappingMode.Absolute>ayarlayarak bu koordinat sistemini değiştirebilirsiniz. Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir. Değerler doğrudan yerel alanda yorumlanır.

, <xref:System.Windows.Media.GradientStop> Bir gradyan fırçasının temel yapı taşıdır.  Gradyan durağı, gradyan ekseni <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.GradientStop.Offset%2A> üzerinde bir olarak belirtir.

- Gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> özelliği gradyan durağının rengini belirtir. Rengi önceden tanımlanmış bir renk ( <xref:System.Windows.Media.Colors> sınıf tarafından sağlanmış) kullanarak veya ScRGB veya argb değerlerini belirterek ayarlayabilirsiniz. ' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]De, bir rengi anlatmak için onaltılık Gösterim de kullanabilirsiniz. Daha fazla bilgi için, <xref:System.Windows.Media.Color> yapısına bakın.

- Gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> özelliği gradyan ekseninin gradyan durağının renginin konumunu belirtir. <xref:System.Double> Bu Aralık 0 ile 1 arasındadır. Gradyan durağının fark değeri 0 ' dır, daha yakın renk de degradenin başlangıcına yakındır. Gradyanın fark değeri 1 ' e yaklaşacak ve rengin, degradenin sonuna yakın olması gerekir.

Gradyan duraklarının her bir noktasının rengi, iki sınırlayıcı gradyan durdurulduğunda belirtilen rengin bir birleşimi olarak doğrusal bir şekilde enterpoladır. Aşağıdaki çizimde, önceki örnekteki gradyan duraklarının vurgulanmıştır. Daireler gradyan duraklarının konumunu ve kesik çizgili bir çizgiyi işaret eden gradyan eksenini gösterir.

![Doğrusal bir degradede gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")

İlk gradyan durağı, bir uzaklığında `0.0`sarı rengi belirtir.  İkinci gradyan durağı, bir uzaklığında `0.25`kırmızı rengi belirtir.  Bu iki durak arasındaki noktalara, soldan sağa doğru hareket eden bir şekilde, soldan sağa geçiş yaparken, yavaş olarak sarıdan kırmızıya geçiş yapılır.  Üçüncü gradyan durağı, bir uzaklığında `0.75`mavi rengi belirtir.  İkinci ve üçüncü gradyan arasındaki noktaları aşamalı olarak kırmızı ve mavi arasında değişir. Dördüncü gradyan durağı, bir uzaklığında `1.0`açık yeşil rengi belirtir. Üçüncü ve dördüncü gradyan arasındaki noktaları, aşamalı olarak mavi ve açık yeşil arasında değişir.

<a name="gradientaxis"></a>

### <a name="the-gradient-axis"></a>Gradyan ekseni

Daha önce belirtildiği gibi, doğrusal gradyan fırçasının gradyan duraklarının bir çizgi, gradyan ekseni ve bir satır üzerinde konumlandırıldı. Fırçanın <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> özelliklerini kullanarak çizginin yönünü ve boyutunu değiştirebilirsiniz. Fırçanın <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>' i düzenleyerek yatay ve dikey degradeler oluşturabilir, Gradyan yönünü ters çevirin, gradyan formayı daraltabilir ve daha fazlasını yapabilirsiniz.

Varsayılan olarak, doğrusal gradyan fırçası <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> boyanmış olan alana göre değişir. (0, 0) noktası, boyanmış alanın sol üst köşesini temsil eder ve (1, 1) boyanmış alanın sağ alt köşesini temsil eder. Varsayılan <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> değer (0, 0) ve varsayılan değer (1, 1) olduğundan, sol üst köşeden başlayan ve boyanmış alanın sağ alt köşesine genişleyen köşegen bir gradyan oluşturur. <xref:System.Windows.Media.LinearGradientBrush> Aşağıdaki çizimde, varsayılan <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>ile doğrusal bir gradyan fırçasının gradyan ekseni gösterilmektedir.

![Köşegen doğrusal gradyan Için gradyan ekseni](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")

Aşağıdaki örnek, fırçasının <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve ' i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>belirterek yatay degradenin nasıl oluşturulacağını gösterir. Gradyanın durduğuna önceki örneklerde olduğu gibi dikkat edin; yalnızca <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>öğesini değiştirerek gradyan köşegenden yataya değiştirilmiştir.

[!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]

Aşağıdaki çizimde oluşturulan gradyan gösterilmektedir. Gradyan ekseni kesik çizgili bir çizgiyle işaretlenir ve gradyan duraklarının çevrelerle işaretlenmiş olması gerekir.

![Yatay doğrusal gradyan Için gradyan ekseni](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")

Sonraki örnekte, dikey degradenin nasıl oluşturulacağı gösterilmektedir.

[!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]

Aşağıdaki çizimde oluşturulan gradyan gösterilmektedir. Gradyan ekseni kesik çizgili bir çizgiyle işaretlenir ve gradyan duraklarının çevrelerle işaretlenmiş olması gerekir.

![Dikey gradyan Için gradyan ekseni](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")

<a name="radialgradients"></a>

## <a name="radial-gradients"></a>Radyal degradeler

A <xref:System.Windows.Media.LinearGradientBrush>gibi, bir <xref:System.Windows.Media.RadialGradientBrush> eksen üzerinde birlikte karışan renklerle bir alanı boyar. Önceki örneklerde, doğrusal gradyan fırçası ekseninin nasıl düz bir çizgi olduğunu gösterildi. Radyal gradyan fırçasının ekseni bir daire tarafından tanımlanır; renkleri "yarıçapın" kendi kaynağından dışarı doğru.

Aşağıdaki örnekte, bir dikdörtgen iç kısmını boyamak için radyal gradyan fırçası kullanılır.

[!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]

Aşağıdaki çizimde, önceki örnekte oluşturulan gradyan gösterilmektedir. Fırçanın gradyan durması vurgulandı. Sonuçlar farklı olsa da, bu örnekteki gradyan duraklarının önceki doğrusal gradyan fırçası örneklerinde gradyan duraklarına özdeş olduğuna dikkat edin.

![Radyal degradede gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")

, <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Radyal gradyan fırçasının gradyan ekseninin başlangıç noktasını belirtir. Gradyan ekseni gradyan başlangıcının gradyan çemberinden yayılır. Fırçanın gradyan çemberi <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> özellikleri tarafından tanımlanır.

<xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>Aşağıdaki çizimde, farklı <xref:System.Windows.Media.RadialGradientBrush.Center%2A> <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>,, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> ayarlarına sahip çeşitli radyal degradeler gösterilmektedir.

![RadialGradientBrush ayarları](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii") Farklı GradientOrigin, Center, RadiusX ve RadiusY ayarları ile RadialGradientBrushes.

<a name="specifyinggradientcolors"></a>

## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Saydam veya kısmen saydam gradyan duraklarının belirlenmesi

Gradyan duraklarının bir opaklık özelliği sağlamadığı için, İşaretlemede argb onaltılı gösterimi kullanarak renklerin alfa kanalını belirtmeniz veya saydam veya kısmen saydam olan gradyan <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> duraklarının oluşturulması için yöntemi kullanmanız gerekir. Aşağıdaki bölümlerde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kodunda kısmen saydam gradyan duraklarının nasıl oluşturulduğu açıklanmaktadır.

<a name="argbsyntax"></a>

### <a name="specifying-color-opacity-in-xaml"></a>"XAML" içinde renk geçirgenliği belirtme

İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tek tek renklerin saydamlığını belirtmek için ARGB onaltılık gösterimini kullanırsınız. ARGB onaltılık gösterimi aşağıdaki sözdizimini kullanır:

`#`**AA** *RRGGBB*

Önceki satırdaki *AA* , rengin opaklığını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. *RR*, *gg*ve *BB* her biri, rengin kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. Her onaltılık basamak 0-9 veya A-F arasında bir değere sahip olabilir. 0 en küçük değerdir ve F en büyük değerdir. 00 ' ın alfa değeri tamamen saydam bir rengi belirtir, bu da bir FF Alpha değeri tamamen opak bir renk oluşturur.  Aşağıdaki örnekte, iki renk belirtmek için onaltılı ARGB gösterimi kullanılır. İlki kısmen saydamdır (x20 Alpha değeri vardır), ikincisi tamamen opak hale gelir.

[!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]

<a name="fromscrgbsyntax"></a>

### <a name="specifying-color-opacity-in-code"></a>Kodda renk geçirgenliği belirtme

Kodu kullanırken, statik <xref:System.Windows.Media.Color.FromArgb%2A> Yöntem bir renk oluştururken alfa değeri belirtmenize olanak sağlar. Yöntemi türünde <xref:System.Byte>dört parametre alır. İlk parametre rengin alfa kanalını belirtir; diğer üç parametre rengin kırmızı, yeşil ve mavi değerlerini belirtir. Her değer 0 ile 255 (dahil) arasında olmalıdır. 0 ' ın bir alfa değeri, rengin tamamen saydam olduğunu belirtir, ancak 255 Alpha değeri rengin tamamen opak olduğunu belirtir. Aşağıdaki örnekte, <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi iki renk oluşturmak için kullanılır. İlk renk kısmen saydamdır (alfa değeri 32 ' dir), ikincisi tamamen opak hale gelir.

[!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]

Alternatif olarak, bir renk oluşturmak <xref:System.Windows.Media.Color.FromScRgb%2A> için ScRGB değerlerini kullanmanızı sağlayan yöntemini kullanabilirsiniz.

<a name="otherbrushes"></a>

## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Görüntüler, çizimler, görseller ve desenlerle boyama

<xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> ve<xref:System.Windows.Media.VisualBrush> sınıfları görüntüleri, çizimleri veya görselleri olan bir alanı boyamanıza imkan tanır. Görüntüler, çizimler ve desenlerle boyama hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Fırça Dönüşümüne Genel Bakış](brush-transformation-overview.md)
- [Grafik İşleme Katmanları](../advanced/graphics-rendering-tiers.md)
