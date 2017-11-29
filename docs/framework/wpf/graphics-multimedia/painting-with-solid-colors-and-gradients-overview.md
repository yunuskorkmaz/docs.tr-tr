---
title: "Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f26ab394ea94b27257b6d0b662f3a78f3e68ca99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış
Bu konuda nasıl kullanılacağını açıklar <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, ve <xref:System.Windows.Media.RadialGradientBrush> düz renkler, doğrusal gradyanlar ve radyal gradyanlar ile boyamak için nesneleri.  
  

  
<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Düz renk ile alanı boyama  
 Herhangi bir platformda en yaygın işlemlerden biri olan bir kesintisiz bir alanı boyamak için <xref:System.Windows.Media.Color>. Bu görevi gerçekleştirmek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Media.SolidColorBrush> sınıfı. Aşağıdaki bölümlerde ile boyamak için farklı yollar açıklanmaktadır bir <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>"XAML" içinde SolidColorBrush kullanma  
 İçinde bir düz renk ile alanı boyamak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki seçeneklerden birini kullanın.  
  
-   Önceden tanımlanmış düz renk fırça ada göre seçin.  Örneğin, bir düğmenin ayarlayabilirsiniz <xref:System.Windows.Controls.Control.Background%2A> "Red" veya "MediumBlue şeklinde".  Düz renk fırçaları diğer listesini önceden tanımlanmış statik özelliklerini görmek <xref:System.Windows.Media.Brushes> sınıfı. Bir örnek verilmiştir.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
-   Kırmızı, yeşil ve tek bir düz renk birleştirmek için mavi miktarda belirterek 32-bit renk paletinden bir renk seçin.  32-bit paletinden bir renk belirtmek için biçim "*#rrggbb*", burada *rr* kırmızı, göreli miktarını belirten iki basamaklı bir onaltılık sayı *gg* Yeşil, miktarını belirtir ve *bb* mavi miktarını belirtir.  Ayrıca, renk olarak belirtilebilir "#*geçirgenliğini belirttiği*" nerede *aa* belirtir *alfa* değeri veya saydamlığını rengi. Bu yaklaşım, kısmen saydam renkleri oluşturmanıza olanak sağlar.  Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button> onaltılık gösterim kullanılarak tamamen opak kırmızı olarak ayarlayın.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
-   Açıklamak için özellik etiketi sözdizimini kullanın bir <xref:System.Windows.Media.SolidColorBrush>. Bu sözdizimi daha ayrıntılı ancak fırça opaklık gibi ek ayarları belirtmenize olanak sağlar. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> iki özelliklerini <xref:System.Windows.Controls.Button> öğeleri tamamıyla opak kırmızı şeklinde ayarlanır. İlk fırça rengi önceden tanımlanmış renk adı kullanılarak açıklanmıştır. İkinci fırça rengi, onaltılık gösterim kullanılarak tanımlanır.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Kod içinde SolidColorBrush boyama  
 Kod içinde bir düz renk ile alanı boyamak için aşağıdaki seçeneklerden birini kullanın.  
  
-   Tarafından sağlanan önceden tanımlanmış Fırçalar birini kullanın <xref:System.Windows.Media.Brushes> sınıfı. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button> ayarlanır <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
-   Oluşturma bir <xref:System.Windows.Media.SolidColorBrush> ve kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliğini kullanarak bir <xref:System.Windows.Media.Color> yapısı. Önceden tanımlanmış bir renk kullanabilirsiniz <xref:System.Windows.Media.Colors> sınıfı veya oluşturabilir bir <xref:System.Windows.Media.Color> statik kullanarak <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi.  
  
     Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği bir <xref:System.Windows.Media.SolidColorBrush> önceden tanımlanmış bir renk kullanarak.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statik <xref:System.Windows.Media.Color.FromArgb%2A> rengin alfa, kırmızı, yeşil ve mavi değerlerini belirtmenizi sağlar. Bu değerlerin her birini tipik aralığının 0-255'tir. Örneğin, bir alfa değeri 0 255 değerini rengi tamamen opak göstergesidir renk tamamen saydam olduğunu gösterir. Benzer şekilde, kırmızı bir değer 0 255 değerini rengi kırmızı olası en büyük miktarına sahip göstergesidir renk hiç kırmızı içinde sahip olduğunu gösterir.  Aşağıdaki örnekte, fırça rengi alfa, kırmızı, yeşil ve mavi değerleri belirtilerek tanımlanır.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Renk belirtmek üzere ek yöntemler için bkz: <xref:System.Windows.Media.Color> başvuru konusu.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Gradyan ile bir alanı boyama  
 Gradyan fırçası bir alanı başka bir eksen boyunca blend birden çok renkleri boyar. Üç boyutlu hissini denetimlerinizi vermiş izlenim ışık ve gölge oluşturmak için kullanabilirsiniz. Ayrıca bunları cam, chrome, su ve diğer kesintisiz yüzeyleri benzetimini yapmak için kullanabilirsiniz.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]iki tür gradyan fırçası sağlar: <xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Doğrusal gradyanlar  
 A <xref:System.Windows.Media.LinearGradientBrush> bir satır tanımlanan bir gradyan ile bir alanı boyar *gradyan ekseni*.  Gradyan renklerini ve konumlarını kullanarak gradyan ekseni boyunca belirttiğiniz <xref:System.Windows.Media.GradientStop> nesneleri.  Ayrıca, yatay ve dikey gradyanları oluşturmanıza ve gradyan yönünü tersine çevirmek için sağlar gradyan ekseni değiştirebilir. Gradyan ekseni sonraki bölümde açıklanmıştır. Varsayılan olarak, çapraz gradyan oluşturulur.  
  
 Aşağıdaki örnek, dört renklerle doğrusal gradyan oluşturan kodu gösterir.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Bu kod aşağıdaki gradyanı üretir:  
  
 ![Çapraz doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Not:** başlangıç ve bitiş noktalarını ayarlamak için bu konudaki gradyan örnekleri varsayılan koordinat sistemi kullanın. Varsayılan koordinat sistemi göreli bir sınırlama kutusudur: 0, 0 yüzdesi sınırlama kutusu ve 1 gösterir sınırlama kutusunun yüzde 100 gösterir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğinin değeri <xref:System.Windows.Media.BrushMappingMode.Absolute>. Mutlak koordinat sistemi sınırlayıcı kutu göre değil. Değerleri, doğrudan yerel uzayda yorumlanır.  
  
 <xref:System.Windows.Media.GradientStop> Gradyan fırçası temel yapı bloğu olduğu.  Gradyan durağının belirten bir <xref:System.Windows.Media.GradientStop.Color%2A> adresindeki bir <xref:System.Windows.Media.GradientStop.Offset%2A> gradyan ekseni boyunca.  
  
-   Gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> özelliği gradyan rengini belirtir. Önceden tanımlanmış bir renk kullanarak rengi ayarlayabilir (tarafından sağlanan <xref:System.Windows.Media.Colors> sınıfı) veya ScRGB veya ARGB değerlerini belirterek. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], onaltılık gösterimi bir renk tanımlamak için de kullanabilirsiniz. Daha fazla bilgi için bkz: <xref:System.Windows.Media.Color> yapısı.  
  
-   Gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> özelliği gradyan ekseni üzerinde gradyan durağının renginin konumunu belirtir. Uzaklığı bir <xref:System.Double> 1 0'dan aralıkları. Yakınsa gradyan durağının uzaklık değeri 0'a yakınsa renk gradyan başlangıcına yaklaşır. Yakınsa gradyan uzaklık değeri 1'e yakınsa renk gradyan sonuna yaklaşır.  
  
 Gradyan durakları arasındaki her noktanın rengi doğrusal gradyan durakları sınırlayıcı iki tarafından belirtilen renk birleşimi olarak ilişkilendirilir. Aşağıdaki çizimde, önceki örnekte gradyan durakları vurgular. Gradyan duraklarının konumunu daireleri işaretleyin ve gradyan ekseni kesikli çizgi gösterir.  
  
 ![Doğrusal gradyan gradyan duraklarının](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 İlk gradyan durağının uzaklığı sarı renkli belirtir `0.0`.  İkinci gradyan durağının uzaklığı kırmızı rengini belirtir `0.25`.  Soldan sağa gradyan ekseni boyunca taşımak gibi bu iki durak arasındaki noktalar sarı kırmızı kademeli olarak değiştirin.  Üçüncü gradyan durağının uzaklığı mavi rengini belirtir `0.75`.  İkinci ve üçüncü gradyan durakları arasındaki noktalar, mavi ve kırmızı kademeli olarak değiştirin. Dördüncü gradyan durağının açık bir uzaklıkta yeşil rengini belirtir `1.0`. Üçüncü ve dördüncü gradyan durakları arasındaki noktalar yeşile mavi kademeli olarak değiştirin.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Gradyan ekseni  
 Daha önce belirtildiği gibi doğrusal gradyan fırçası gradyan durakları bir çizgi, gradyan ekseni boyunca yerleştirilir. Yönlendirme ve fırça kullanma satır boyutu değişebilir <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> özellikleri. Fırça düzenleme tarafından <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, oluşturabileceğiniz yatay ve dikey gradyanlar gradyan yönünü tersine çevir, daraltabilir gradyan yayılmasını ve daha fazlasını yapabilirsiniz.  
  
 Varsayılan olarak, doğrusal gradyan fırçası 's <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> boyandığında alana göre. (0,0) noktası boyandığında alanının sağ alt köşedeki boyanmış ve (1,1) temsil edilen alanının sol üst köşesinde temsil eder. Varsayılan <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> , bir <xref:System.Windows.Media.LinearGradientBrush> (0,0) ' dır ve varsayılan <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> (1,1) ' dir sol üst köşede başlatma ve boyanan alanın sağ alt köşesindeki genişletme Çapraz Gradyan oluşturur. Varsayılan bir doğrusal gradyan fırçası gradyan eksenini aşağıda gösterilmiştir <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Çapraz doğrusal gradyan için gradyan ekseni](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 Aşağıdaki örnek yatay nasıl oluşturulacağını fırça belirterek gradyan gösterir <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Gradyan durakları önceki örneklerde olduğu gibi aynı olduğuna dikkat edin; yalnızca değiştirerek <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, gradyan çaprazdan yataya değişti.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Aşağıdaki çizimde oluşturulan gradyanı gösterir. Gradyan ekseni kesikli çizgi ile işaretlenir ve gradyan durakları daireler ile işaretlenir.  
  
 ![Yatay doğrusal gradyan için gradyan ekseni](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Sonraki örnek dikey gradyan oluşturulacağını gösterir.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Aşağıdaki çizimde oluşturulan gradyanı gösterir. Gradyan ekseni kesikli çizgi ile işaretlenir ve gradyan durakları daireler ile işaretlenir.  
  
 ![Dikey Gradyan için gradyan ekseni](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Radyal gradyanlar  
 Gibi bir <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> bir alanı birlikte bir eksen boyunca blend renkleri boyar. Önceki örneklerde, nasıl bir çizgide doğrusal gradyan fırçası ekseninin olduğunu gösterdi. Radyal gradyan fırçası ekseninin bir daire tarafından tanımlanan; renklerini "dışa kendi merkezinden yayılır".  
  
 Aşağıdaki örnekte, Radyal gradyan fırçası bir dikdörtgenin iç kısmını boyamak için kullanılır.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Aşağıdaki çizimde önceki örnekte oluşturulan gradyanı gösterir. Vurgulanan fırça gradyan durdurur. Sonuçlar farklı olmasına rağmen bu örnekteki gradyan durakları aynı önceki doğrusal gradyan fırçası örneklerindeki gradyan duraklarının olduğunu, dikkat edin.  
  
 ![Radyal gradyan gradyan duraklarının](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Radyal gradyan fırçası gradyan ekseninin başlangıç noktasını belirtir. Gradyan ekseni gradyan merkezinden gradyan daire yayılır. Fırça gradyan daire tarafından tanımlanan kendi <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> özellikleri.  
  
 Farklı ile bazı radyal gradyanları aşağıda gösterilmiştir <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, ve <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> ayarlar.  
  
 ![RadialGradientBrush ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes farklı GradientOrigin, merkezi, RadiusX ve RadiusY ayarlara sahip.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Saydam veya kısmen saydam gradyan durakları belirtme  
 Gradyan durakları opacity özelliği sağlamadığından kullanarak renklerin alfa kanal belirtmelisiniz [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] işaretleme veya kullanım onaltılık gösterimde <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> saydam veya kısmen saydam gradyan durakları oluşturmak için yöntem. Aşağıdaki bölümlerde, kısmen saydam gradyan duraklarının oluşturmak açıklamaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" içinde Renk Geçirgenliği Belirtme  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] tek tek renkleri geçirgenliğini belirtmek için onaltılık gösterimi. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)]onaltılık gösterimi aşağıdaki söz dizimini kullanır:  
  
 `#`**aa** *rrggbb*  
  
 *Aa* önceki satırda rengin geçirgenliğini belirtmek için kullanılan iki basamaklı onaltılık değeri temsil eder. *Rr*, *gg*, ve *bb* her rengi kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı onaltılık değeri temsil eder. Her bir onaltılık değerinin 0-9 veya A-f arasında olabilir 0 en küçük değerdir ve F en büyük değerdir. 00 alfa değeri FF alfa değeri bir renk oluştururken, tamamen saydam olacak bir renk tamamıyla opak belirtir.  Aşağıdaki örnekte, onaltılık [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] gösterimi iki rengi belirtmek için kullanılır. İlk (bunu sahip x20 alfa değeri), kısmen saydamdır ikinci tamamen opak olsa.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Kod içinde Renk Geçirgenliği Belirtme  
 Kod, statik kullanırken <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi bir renk oluşturduğunuzda alfa değeri belirtmenize olanak sağlar. Yöntem türü dört parametre alır <xref:System.Byte>. İlk parametre rengin alfa kanal belirtir; diğer üç parametre rengi kırmızı, yeşil ve mavi değerlerini belirtin. Her değer 0 ile 255 arasında (bunlar dahil) olmalıdır. Alfa değeri 0 255 alfa değeri rengi tamamen opak olduğunu belirtir sırada rengi tamamen saydam olduğunu belirtir. Aşağıdaki örnekte, <xref:System.Windows.Media.Color.FromArgb%2A> yöntemi iki renk üretmek için kullanılır. İlk rengi (bunu alfa değerine sahiptir, 32), kısmen saydamdır ikinci tamamıyla opak olsa.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternatif olarak, kullanabilir <xref:System.Windows.Media.Color.FromScRgb%2A> yöntemi, bir renk oluşturmak için ScRGB değerlerini kullanmanızı sağlar.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Görüntüleri, çizimler, görseller ve desenler ile Boyama  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> sınıfların resimler, çizimler veya görsel bir alanı boyamak olanak tanır. Resimler, çizimler ve desenler ile boyama hakkında daha fazla bilgi için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 [Görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Fırça dönüşümüne genel bakış](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)
