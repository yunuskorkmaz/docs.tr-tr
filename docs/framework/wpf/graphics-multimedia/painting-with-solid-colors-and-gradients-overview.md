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
ms.openlocfilehash: 7945660f40e44596fe36a6b9d53223a0e264a064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009467"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış
Bu konu nasıl kullanılacağını açıklar <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, ve <xref:System.Windows.Media.RadialGradientBrush> düz renkler, doğrusal gradyanlar ve radyal gradyanlar ile Boyama nesneleri.  

<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Düz renk ile bir alanı boyama  
 En yaygın işlemlerden herhangi bir platformda bir düz ile bir alanı boyama etmektir <xref:System.Windows.Media.Color>. Bu görevi gerçekleştirmek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Media.SolidColorBrush> sınıfı. Aşağıdaki bölümlerde farklı yolları ile Boyama bir <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>SolidColorBrush "XAML" kullanma  
 İçinde bir düz renk ile bir alanı boyama için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki seçeneklerden birini kullanın.  
  
- Ada göre bir önceden tanımlanmış tek renk Fırçası seçin.  Örneğin, bir düğmenin ayarlayabilirsiniz <xref:System.Windows.Controls.Control.Background%2A> "Red" veya "MediumBlue şeklinde".  Diğer listesini düz renk fırçaları önceden tanımlanmış statik özelliklerini görmek <xref:System.Windows.Media.Brushes> sınıfı. Bir örnek verilmiştir.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
- Bir renk, 32 bit renk paletinden kırmızı, yeşil ve mavi tek bir düz renk birleştirilecek miktarda belirterek seçin.  32-bit paletinden bir renk belirtmeye yönelik biçimi "*#rrggbb*" burada *rr* kırmızı, göreli miktarını belirten iki basamaklı bir onaltılık sayı olduğu *gg* Yeşil, belirtir ve *bb* mavi miktarını belirtir.  Ayrıca, rengi olarak belirtilebilir "#*geçirgenliğini belirttiği*" nerede *aa* belirtir *alfa* değeri veya saydamlığını rengi. Bu yaklaşım, kısmen saydam olan renkleri oluşturmanıza olanak sağlar.  Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button> onaltılık gösterim kullanılarak tamamen opak kırmızı olarak ayarlayın.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
- Özellik etiketi sözdizimi tanımlamak için kullanmak bir <xref:System.Windows.Media.SolidColorBrush>. Bu sözdizimi, daha ayrıntılı ancak fırça opaklığını gibi ek ayarları belirtmenize olanak sağlar. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> iki özelliklerini <xref:System.Windows.Controls.Button> öğeleri tamamen opak kırmızı ayarlanır. İlk fırçanın rengi, önceden tanımlı renk adı kullanılarak tanımlanır. İkinci fırçanın rengi, onaltılık gösterim kullanılarak tanımlanır.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Kod içinde SolidColorBrush ile Boyama  
 Kodda düz renk ile bir alanı boyama için aşağıdaki seçeneklerden birini kullanın.  
  
- Tarafından sağlanan önceden tanımlanmış Fırçalar birini <xref:System.Windows.Media.Brushes> sınıfı. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button> ayarlanır <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
- Oluşturma bir <xref:System.Windows.Media.SolidColorBrush> ve kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliğini kullanarak bir <xref:System.Windows.Media.Color> yapısı. Önceden tanımlanmış bir rengi kullanabileceğiniz <xref:System.Windows.Media.Colors> sınıfı veya oluşturabilir bir <xref:System.Windows.Media.Color> 'using static <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi.  
  
     Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği bir <xref:System.Windows.Media.SolidColorBrush> kullanarak önceden tanımlanmış bir rengi.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statik <xref:System.Windows.Media.Color.FromArgb%2A> kırmızı, yeşil ve mavi renk, alfa değerleri belirtmenize olanak sağlar. Bu değerlerin her birini tipik aralığının 0-255'tir. Örneğin, alfa değeri 0, 255 değerini rengi tamamen opak çağrılırken bir renk tamamen saydam olduğunu gösterir. Benzer şekilde, 255 değerini bir rengin kırmızı olası en uzun süreyi sahip çağrılırken bir renk içinde hiç kırmızı sahip kırmızı 0 değerini gösterir.  Aşağıdaki örnekte, bir fırçanın rengi, alfa, kırmızı, yeşil ve mavi değerleri belirtilerek tanımlanır.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Renk belirtmek ek yollar için bkz. <xref:System.Windows.Media.Color> başvuru konusu.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Gradyan ile bir alanı boyama  
 Gradyan fırçası diğer bir eksen boyunca blend çok sayıda renk ile bir alanı boyar. Üç boyutlu bir genel görünüm denetimlerinizi vererek izlenimler açık ve gölge oluşturmak için kullanabilirsiniz. Ayrıca bunları cam, chrome, su ve diğer kesintisiz yüzeyleri benzetimini yapmak için kullanabilirsiniz.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Gradyan Fırçalar iki tür sağlar: <xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Doğrusal gradyanlar  
 A <xref:System.Windows.Media.LinearGradientBrush> bir satır tanımlanan gradyan ile bir alanı boyar *gradyan eksen*.  Gradyan renklerini ve konumlarını kullanarak gradyan ekseni boyunca belirttiğiniz <xref:System.Windows.Media.GradientStop> nesneleri.  Ayrıca, yatay ve dikey gradyan oluşturmak ve gradyan yönünü tersine çevirmek için sayesinde gradyan eksen değiştirebilir. Gradyan eksen, sonraki bölümde açıklanmıştır. Varsayılan olarak, çapraz gradyan oluşturulur.  
  
 Aşağıdaki örnekte, dört renklerle doğrusal gradyan oluşturan kodu gösterir.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Bu kod, aşağıdaki gradyanı üretir:  
  
 ![Çapraz doğrusal gradyan](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Not:** Bu konuda gradyan örnekleri varsayılan koordinat sistemi, başlangıç ve bitiş noktalarını ayarlamak için kullanın. Varsayılan koordinat sistemi göreli bir sınırlayıcı kutu şöyledir: 0 sınırlayıcı kutu ve 1 yüzde 0 sınırlayıcı kutunun yüzde 100 demektir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özellik değerine <xref:System.Windows.Media.BrushMappingMode.Absolute>. Mutlak koordinat sistemi bir sınırlayıcı kutu göreli değil. Değerleri, doğrudan yerel alan yorumlanır.  
  
 <xref:System.Windows.Media.GradientStop> Gradyan fırçası temel yapı bloğudur.  Gradyan durak belirtir bir <xref:System.Windows.Media.GradientStop.Color%2A> konumundaki bir <xref:System.Windows.Media.GradientStop.Offset%2A> gradyan ekseni.  
  
- Gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> özellik gradyan rengini belirtir. Önceden tanımlanmış bir rengi kullanarak rengini ayarlayabilir (tarafından sağlanan <xref:System.Windows.Media.Colors> sınıfı) veya ScRGB veya ARGB değerlerini belirterek. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir renk tanımlamak için onaltılık gösterim de kullanabilir. Daha fazla bilgi için <xref:System.Windows.Media.Color> yapısı.  
  
- Gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> özellik gradyan eksende gradyan durağının renk konumunu belirtir. Uzaklık bir <xref:System.Double> 1-0'dan aralıkları. Daha yakın bir gradyan durağının uzaklık değeri 0'a daha yakın renk geçişin başlangıca yaklaşır. Daha yakın gradyan uzaklık değeri 1'e yakın renk gradyanı sonuna kadar olan olan.  
  
 Gradyan durakları arasındaki her noktasının rengini, doğrusal gradyan duraklarının sınırlayıcı iki tarafından belirtilen renk birleşimi olarak ilişkilendirilir. Aşağıdaki resimde, önceki örnekte gradyan duraklarının vurgular. Gradyan duraklarının konumuna daireler işaretlemek ve gradyan eksen kesikli çizgiye gösterir.  
  
 ![Doğrusal gradyan gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 İlk gradyan durağı uzaklığı sarı renk belirtir `0.0`.  İkinci gradyan durağı uzaklığı kırmızı rengini belirtir `0.25`.  Soldan sağa gradyan ekseni boyunca hareket ettikçe bu iki durakları arasındaki noktalar sarı kademeli olarak kırmızı olarak değiştirin.  Üçüncü gradyan durağı uzaklığı mavi rengini belirtir `0.75`.  İkinci ve üçüncü gradyan duraklarının arasındaki noktalar, mavi ve kırmızı kademeli olarak değiştirin. Dördüncü gradyan durağı uzaklığı yeşil renk Küf belirtir `1.0`. Üçüncü ve dördüncü gradyan duraklarının arasındaki noktalar yeşile maviye kademeli olarak değiştirin.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Gradyan ekseni  
 Doğrusal gradyan fırçası gradyan duraklarının daha önce belirtildiği gibi bir çizgi, gradyan ekseni boyunca yerleştirilir. Fırça kullanarak satır boyutunu ve yönünü değişebilir <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> özellikleri. Fırçanın düzenleme tarafından <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, oluşturabileceğiniz yatay ve dikey gradyan gradyan yönünü tersine çevir, daraltabilir gradyan yayılmasını ve daha fazlasını yapabilirsiniz.  
  
 Varsayılan olarak, doğrusal gradyan fırçası 's <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> boyanan alanına göre. Noktası (0,0) üst sol löşede boyanan alanının sağ alt köşedeki boyanan ve (1,1) temsil edilen alanının temsil eder. Varsayılan <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> , bir <xref:System.Windows.Media.LinearGradientBrush> (0,0) ' dır ve varsayılan <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> (1,1) olan sol üst köşesinde'ı başlatıp boyanan alana sağ alt köşesindeki genişletme Çapraz Gradyan oluşturur. Doğrusal gradyan fırçası varsayılan gradyan eksenini aşağıdaki çizimde <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Gradyan eksen için alt kenar köşegeni doğrusal gradyan](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 Aşağıdaki örnek bir yatay oluşturulacağını fırçanın belirterek gradyan gösterir <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Gradyan duraklarının önceki örneklerde olduğu gibi aynı olduğuna dikkat edin; yalnızca değiştirerek <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, geçişin çaprazdan yataya değiştirildi.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Oluşturulan gradyan aşağıda gösterilmiştir. Gradyan eksen kesik çizgi ile işaretlenir ve gradyan duraklarının daire ile işaretlenir.  
  
 ![Gradyan eksen için Yatay doğrusal gradyan](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Sonraki örnek, dikey gradyan oluşturma işlemi gösterilmektedir.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Oluşturulan gradyan aşağıda gösterilmiştir. Gradyan eksen kesik çizgi ile işaretlenir ve gradyan duraklarının daire ile işaretlenir.  
  
 ![Dikey Gradyan gradyan eksen](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Radyal gradyanlar  
 Gibi bir <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> bir eksen boyunca karıştırarak renk ile bir alanı boyar. Önceki örneklerde, doğrusal gradyan fırçası eksenine düz bir çizgi nasıl olduğunu göstermiştir. Radyal gradyan fırçası eksen bir daire tarafından tanımlanır; renklerini "dışa kendi merkezinden yayılır".  
  
 Aşağıdaki örnekte, bir radyal gradyan fırçasına iç bir dikdörtgen kısmını boyamak için kullanılır.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Önceki örnekte oluşturulan gradyanı aşağıda gösterilmiştir. Fırçanın gradyan duraklarının vurgulanır. Sonuçları farklı olmasına karşın, bu örnekte gradyan duraklarının önceki doğrusal gradyan fırçası örneklerde gradyan duraklarının aynı olan, dikkat edin.  
  
 ![Radyal gradyan gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Radyal gradyan fırçası gradyan ekseninin başlangıç noktasını belirtir. Gradyan eksen gradyan dairenin gradyan merkezinden yayılır. Gradyan fırça daire tarafından tanımlanan kendi <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> özellikleri.  
  
 Aşağıdaki çizimde birkaç radyal gradyanlar ile farklı <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> ayarları.  
  
 ![RadialGradientBrush ayarları](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
Farklı ayarlarla GradientOrigin, merkezi RadiusX ve RadiusY RadialGradientBrushes.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Saydam veya kısmen saydam gradyan durakları belirtme  
 Gradyan duraklarının donukluk özelliği sağlamadığından, alfa kanalı renkler kullanarak belirtmelisiniz [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] biçimlendirme veya onaltılık gösterimde <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> saydam veya saydam kısmen gradyan durakları oluşturmak için yöntemi. Aşağıdaki bölümlerde, kısmen saydam gradyan duraklarının oluşturma işlemleri açıklanmaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" renk opaklığı belirtme  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] tek tek renkler opaklığını belirtmek için onaltılık gösterim. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] onaltılık gösterim aşağıdaki sözdizimini kullanır:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* önceki satıra rengin geçirgenliğini belirtmek için kullanılan iki basamaklı bir onaltılık değer temsil eder. *Rr*, *gg*, ve *bb* her rengin kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. Her bir onaltılık basamak 0-9 veya A-f arasında bir değer olabilir. en küçük değer 0 ise ve F en büyük değerdir. Alfa değeri 00 ila tamamen opak FF alfa değeri olan bir renk oluştururken tamamen şeffaf olduğundan bir renk belirtir.  Aşağıdaki örnekte, onaltılık [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] gösterim iki renkleri belirtmek için kullanılır. İlk (sahip x20 alfa değeri) kısmen saydamdır ikinci tamamen opak ederken.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Renk Geçirgenliği kodda belirtme  
 Kod, statik kullanırken <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi, bir renk oluşturduğunuzda bir alfa değeri belirtmenize imkan tanır. Yöntemi dört parametre türü alır <xref:System.Byte>. İlk parametre rengi alfa kanalı belirtir; diğer üç parametre rengin kırmızı, yeşil ve mavi değerlerini belirtin. Her değer, 0 ile 255 arasında kapsamlı olmalıdır. Alfa değeri 0, 255 alfa değeri rengi tamamen opak belirtirken rengi tamamen saydam olduğunu belirtir. Aşağıdaki örnekte, <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi iki renk üretmek için kullanılır. İlk renk (bir alfa değeri 32 erişiminizde), kısmen saydamdır saniye ila tamamen opak ederken.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternatif olarak, kullanabilir <xref:System.Windows.Media.Color.FromScRgb%2A> yöntemi, bir renk oluşturmak için ScRGB değerlerini kullanmanıza olanak sağlar.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Görüntüler, çizimler, görselleri ve düzenleri ile Boyama  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> sınıfları görüntüler, çizimler veya görsel ile bir alanı boyama olanak tanır. Boyama görüntüler, çizimler ve desenleri hakkında daha fazla bilgi için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Fırça Dönüşümüne Genel Bakış](brush-transformation-overview.md)
- [Grafik İşleme Katmanları](../advanced/graphics-rendering-tiers.md)
