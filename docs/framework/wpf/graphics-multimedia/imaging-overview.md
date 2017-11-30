---
title: "Görüntülemeye Genel Bakış"
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
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6821b724e45ea90a5b22c6efe6c36ee3b99e39ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imaging-overview"></a>Görüntülemeye Genel Bakış
Bu konuda tanıtılmaktadır [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]geliştiricilerin görüntülemek, dönüştürme ve görüntüleri format sağlar.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF görüntüleme bileşeni  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]içinde görüntüleme özelliğinde önemli iyileştirmeler sağlar [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Bir bit eşlem görüntüleme veya ortak bir denetimde bir resim kullanma gibi özellikleri Imaging önceden bağımlıdır [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] veya [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] kitaplıkları. Bunlar [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] taban çizgisi görüntüleme işlevselliği sağlar, ancak eksik codec genişletilebilirliği ve yüksek doğruluk görüntü desteği için desteği gibi özellikleri. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]eksikliklerini aşmak için tasarlanmış [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ve [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] ve yeni bir dizi sağlamak [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] görüntülemek ve uygulamalarınızdaki resimleri kullanmak için.  
  
 Erişim için iki yolla [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], yönetilen bileşen ve yönetilmeyen bir bileşen. Yönetilmeyen bileşen aşağıdaki özellikleri sağlar.  
  
-   Yeni veya özel resim biçimleri için genişletilebilirlik modeli.  
  
-   Geliştirilmiş performans ve güvenlik dahil olmak üzere yerel görüntü biçimleri [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]ve simge (.ico).  
  
-   Yüksek bit derinliği görüntü verilerinin korunması kanal (32 bit / piksel) başına 8 bit.  
  
-   Bozucu olmayan resmi ölçekleme, kırpma ve döndürme.  
  
-   Basitleştirilmiş renk yönetimi.  
  
-   Dosya içinde özel meta verileri desteği.  
  
-   Yönetilen bileşen diğer ile sorunsuz bütünleştirme görüntülerinin sağlamak için yönetilmeyen altyapısını kullanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi özellikleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animasyon ve grafik. Yönetilen bileşen de faydalanır [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] yeni görüntüyü otomatik olarak tanınmasını sağlayan görüntü codec genişletilebilirlik modeli biçimleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Çoğu yönetilen [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] bulunan <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> ad alanı, birkaç önemli tür rağmen gibi <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.ImageDrawing> bulunan <xref:System.Windows.Media?displayProperty=nameWithType> ad alanı ve <xref:System.Windows.Controls.Image> bulunuyor<xref:System.Windows.Controls?displayProperty=nameWithType> ad alanı.  
  
 Bu konu yönetilen bileşen hakkında ek bilgi sağlar. Yönetilmeyen hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] bkz [Yönetilmeyen WPF görüntüleme bileşeni](https://msdn.microsoft.com/library/ee719902.aspx) belgeleri.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF resim biçimleri  
 Codec kod çözme veya belirli bir medya biçiminin kodlamak için kullanılır. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]için bir codec içerir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]ve Icon resim biçimleri. Her codec simgesi hariç olmak üzere, bunların ilgili resim biçimleri kodlanacağını ve, uygulamaların etkinleştirin.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>önemli bir sınıftır kod çözme ve görüntülerini kodlamada kullanılır. Temel yapı bloğu olduğu [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] kanal ve belirli bir boyut ve çözümleme piksel tek, sabit bir kümesini temsil eder. A <xref:System.Windows.Media.Imaging.BitmapSource> birden çok çerçeve resminin tek bir çerçevesi olabilir veya üzerinde gerçekleştirilen bir dönüşümün sonucu olabilir bir <xref:System.Windows.Media.Imaging.BitmapSource>. Kullanılan birincil sınıfların çoğu üst olduğu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi Imaging <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> bir resim biçimi gerçek bitmap verileri depolamak için kullanılır. Çoğu resim biçimleri yalnızca tek bir destek <xref:System.Windows.Media.Imaging.BitmapFrame>, ancak gibi biçimler [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] ve [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] resim başına birden çok çerçeveyi destekler. Çerçeveler kod çözücüleri tarafından girdi verisi olarak kullanılır ve resim dosyaları oluşturmak için kodlayıcıya geçirilir.  
  
 Aşağıdaki örnekte gösterilmiştir nasıl bir <xref:System.Windows.Media.Imaging.BitmapFrame> oluşturulur bir <xref:System.Windows.Media.Imaging.BitmapSource> ve daha sonra eklenen bir [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] görüntü.  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Görüntü biçimi kod çözme  
 Görüntü kod çözme sistem tarafından kullanılan resim verileri bir resim biçimine çevrilmesidir. Görüntü verileri işleme, görüntüleme ya da farklı bir biçimde kodlamak için sonra kullanılabilir. Kod çözücü seçimi resim biçimine dayanır. Belirli bir kod çözücü belirtilmedikçe codec seçimi otomatik olarak yapılır. Örneklerde [WPF resimlerini görüntüleme](#_displayingimages) bölüm göstermek otomatik kod çözme. Yönetilmeyen kullanılarak geliştirilen özel biçim kod çözücüleri [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] arabirimleri ve sistemle otomatik olarak kayıtlı kod çözücü seçimine katılır. Bu otomatik olarak görüntülenecek özel biçimler sağlar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Aşağıdaki örnek kodunu çözmek için bir bit eşlem kod çözücü kullanımını gösteren bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] biçimi görüntü.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Görüntü biçimi kodlama  
 Görüntü kodlama resim verilerinin belirli bir resim biçimine çevrilmesidir. Kodlanmış resim verileri daha sonra yeni resim dosyaları oluşturmak için kullanılabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]Yukarıda açıklanan resim biçimleri için kodlayıcılar sağlar.  
  
 Aşağıdaki örnek, yeni oluşturulan bit eşlem resim kaydetmek için bir kodlayıcı kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>WPF'de görüntüleri görüntüleme  
 Görüntüyü görüntülemek için çeşitli yollar vardır bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulama. Görüntüleri kullanılarak görüntülenebilir bir <xref:System.Windows.Controls.Image> denetimi, bir görsel kullanarak boyandığında bir <xref:System.Windows.Media.ImageBrush>, veya kullanılarak çizilen bir <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Resim denetimini kullanma  
 <xref:System.Windows.Controls.Image>Çerçeve öğesidir ve uygulamalarda görüntüleri göstermek için birincil yol olur. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> iki yolla; öznitelik sözdizimi veya özellik sözdizimi kullanılabilir. Aşağıdaki örnek, bir resmin 200 piksel genişliğinde öznitelik sözdizimi ve özellik etiketi sözdizimi kullanılarak nasıl işleneceğini gösterir. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Birçok örnek kullanmak bir <xref:System.Windows.Media.Imaging.BitmapImage> resim dosyası başvurmak için nesne. <xref:System.Windows.Media.Imaging.BitmapImage>özelleştirilmiş <xref:System.Windows.Media.Imaging.BitmapSource> için iyileştirilmiş [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yükleme ve görüntü olarak görüntülemek için kolay bir yoludur <xref:System.Windows.Controls.Image.Source%2A> , bir <xref:System.Windows.Controls.Image> denetim.  
  
 Aşağıdaki örnek bir resmin 200 piksel genişliğinde kod kullanarak nasıl işleneceğini gösterir.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>uygulayan <xref:System.ComponentModel.ISupportInitialize> başlatma birden çok özellikleri en iyi duruma getirme arabirimi. Özellik değişiklikleri yalnızca nesne başlatma sırasında ortaya çıkabilir. Çağrı <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> başlatmanın başladı sinyal ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> başlatmanın tamamlandı sinyal. Başlatıldıktan sonra özellik değişikliklerini göz ardı edilir.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Döndürme, dönüştürme ve görüntüleri kırpma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Kullanıcıların özelliklerini kullanarak görüntüleri dönüştürme olanak sağlayan <xref:System.Windows.Media.Imaging.BitmapImage> veya ek kullanarak <xref:System.Windows.Media.Imaging.BitmapSource> gibi nesneleri <xref:System.Windows.Media.Imaging.CroppedBitmap> veya <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Bu görüntü dönüşümleri ölçeklemek veya görüntüyü döndürmek, görüntünün piksel biçimini değiştirme veya görüntü kırpma.  
  
 Resim döndürme kullanılarak gerçekleştirilir <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> özelliği <xref:System.Windows.Media.Imaging.BitmapImage>. Döndürme yalnızca 90 derece artışlarla yapılabilir. Aşağıdaki örnekte, bir görüntü 90 derece döndürülür.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Gri tonlamalı gerçekleştirilir gibi görüntüyü farklı piksel biçimine dönüştürme kullanarak <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Bir görüntü dönüştürülür aşağıdaki örneklerde, <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Bir görüntü ya da kırpma için <xref:System.Windows.UIElement.Clip%2A> özelliği <xref:System.Windows.Controls.Image> veya <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanılabilir. Yeni genel olarak, görüntünün bir kısmını görüntülemek istiyorsanız <xref:System.Windows.UIElement.Clip%2A> kullanılmalıdır. Kodlamak ve kırpılan resim kaydetmeye gerekiyorsa <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanılmalıdır. Aşağıdaki örnekte, küçük özelliğini kullanarak bir resim kırpılmış bir <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Görüntüleri uzatma  
 <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği denetler nasıl görüntü kapsayıcısı dolduracak şekilde genişletilir. <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.Stretch> numaralandırma:  
  
-   <xref:System.Windows.Media.Stretch.None>: Görüntü çıkış alanı dolduracak şekilde genişletilir değil. Görüntü çıkış alandan daha büyük olduğunda, görüntü ne uymayan kırpma çıktı alanına çizilir.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Resim çıktı alanına uyacak şekilde ölçeklendirilir. Görüntü yüksekliğini ve genişliğini bağımsız olarak ölçeklenir olduğundan, görüntü özgün en boy oranı korunmayabilir. Diğer bir deyişle, görüntü tamamen çıkış kapsayıcıyı doldurmak için karışmış olabilir.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Resim çıktı alanına tamamen sığacak şekilde ölçeklendirilir. Resmin en boy oranı korunur.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Resim, resmin özgün en boy oranını korurken tamamen çıkış alanı dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki örnekte, her geçerli uygulanır <xref:System.Windows.Media.Stretch> numaralandırmalar için bir <xref:System.Windows.Controls.Image>.  
  
 Aşağıdaki resimde örnek çıktısını gösterir ve farklı etkileyen gösterir <xref:System.Windows.Controls.Image.Stretch%2A> ayarlara sahip bir görüntüye uygulanır.  
  
 ![Farklı TileBrush Stretch ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Farklı Uzatma Ayarları  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>İle görüntüleri boyama  
 Görüntüleri görüntülenebilir bir uygulamada boyama tarafından bir <xref:System.Windows.Media.Brush>. Fırçalar boyamak etkinleştirme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nesneler herhangi bir şeyin desenleri ve görüntüleri karmaşık kümesi için basit, düz renk ile. İle görüntüleri boyamak için kullanmak bir <xref:System.Windows.Media.ImageBrush>. Bir <xref:System.Windows.Media.ImageBrush> bir tür <xref:System.Windows.Media.TileBrush> , içeriği bir bit eşlem resim olarak tanımlar. Bir <xref:System.Windows.Media.ImageBrush> tarafından belirtilen tek bir resmi görüntüler kendi <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği. Bozulmayı önlemek ve desenleri ve diğer efektler üretmek etkinleştirme nasıl görüntü, hizalanmış ve döşendiğini genişletilir denetleyebilirsiniz. Aşağıdaki çizimde ile elde bazı efektleri gösterir bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıktı örnekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Şekiller, denetimler, metin ve resim fırçaları doldurabilirsiniz  
  
 Aşağıdaki örneği kullanarak bir görüntü ile düğmesinin arka plan boyama yapmayı gösteren bir <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Hakkında ek bilgi için <xref:System.Windows.Media.ImageBrush> ve resimleri boyama [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Görüntü meta verilerini  
 Bazı görüntü dosyaları içerik veya dosya özelliklerini açıklayan meta veriler içeriyor. Örneğin, çoğu dijital kamera marka ve model görüntüsünü yakalamak için kullanılan kamera hakkındaki meta verileri içeren görüntüleri oluşturun. Her resim biçimi meta verileri farklı işler ancak [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] depolama ve her desteklenen resim biçimi için meta veri alma Tekdüzen bir yol sağlar.  
  
 Meta verilerine erişim aracılığıyla sağlanır <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapSource> nesnesi. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>döndüren bir <xref:System.Windows.Media.Imaging.BitmapMetadata> görüntü tarafından bulunan tüm meta veriler içeren nesne. Bu veriler bir meta veri şema veya farklı şemaların birleşimi olabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]Aşağıdaki resim meta veri şemalarını destekler: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], metin (PNG metinsel veriler), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], ve [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Meta verileri okuma işlemini basitleştirmek için <xref:System.Windows.Media.Imaging.BitmapMetadata> gibi kolay erişilebilen adlandırılmış özellikleri sağlar <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, ve <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Bu özelliklerin çoğunu da meta veri yazmak için kullanılabilir. Meta veri okumak için ek destek meta veri sorgu okuyucusu tarafından sağlanır. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> Yöntemi gibi bir dize sorgu sağlayarak bir meta veri sorgu okuyucusunu almak için kullanılır *"/ app1/exif /"*. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> depolanan metni elde etmek için kullanılan *"/ metin/açıklama"* konumu.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Meta veri yazmak için bir meta veri sorgu yazıcısı kullanılır. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Sorgu yazıcısını alır ve istenilen değeri ayarlar. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> depolanan metin yazmak için kullanılan *"/ metin/açıklama"* konumu.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Codec genişletilebilirliği  
 Çekirdek özelliği, [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] yeni görüntü codec bileşenleri için genişletilebilirlik modelidir. Bu yönetilmeyen arabirimler codec bileşenleri ile tümleştirmek codec geliştiricilerin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yeni resim biçimleri tarafından otomatik olarak kullanılabilmesi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Genişletilebilirlik örneği için [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], bkz: [Win32 Codec örneği](http://go.microsoft.com/fwlink/?LinkID=160052). Bu örnek kod çözücü ve Kodlayıcı özel resim biçimi için nasıl oluşturulacağını gösterir.  
  
> [!NOTE]
>  Codec sistem tanıması dijital olarak imzalanması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Imaging.BitmapSource>  
 <xref:System.Windows.Media.Imaging.BitmapImage>  
 <xref:System.Windows.Controls.Image>  
 <xref:System.Windows.Media.Imaging.BitmapMetadata>  
 [2B grafik ve görüntü](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Win32 Codec örneği](http://go.microsoft.com/fwlink/?LinkID=160052)
