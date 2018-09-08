---
title: Görüntülemeye Genel Bakış
ms.date: 03/30/2017
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
ms.openlocfilehash: 10cdf5b8cf475c95e086b447b36a569da2173fa9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195681"
---
# <a name="imaging-overview"></a>Görüntülemeye Genel Bakış
Bu konuda tanıtır [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] geliştiricilerin görüntülemek, dönüştürme ve görüntü biçimlendirme sağlar.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF görüntüleme bileşeni  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] içinde görüntüleme özelliğinde önemli iyileştirmeler sağlar [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Bit eşlem görüntüleme veya ortak denetiminde resim kullanma gibi özellikleri Imaging daha önce bağımlıdır [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] veya [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] kitaplıkları. Bunlar [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] taban çizgisi görüntüleme işlevselliği sağlar, ancak codec genişletilebilirlik ve yüksek uygunluğa sahip görüntü desteği desteği gibi özellikleri eksik. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] eksikliklerini aşmak için tasarlanmış [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ve [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] ve yeni bir dizi [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] görüntüleme ve uygulamalarınızı yansımalar kullanma.  
  
 Erişmenin iki yöntemi vardır [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], bir yönetilen bileşen ve yönetilmeyen bir bileşen. Yönetilmeyen bileşeni aşağıdaki özellikleri sağlar.  
  
-   Yeni veya özel görüntü biçimleri için genişletilebilirlik modeli.  
  
-   Geliştirilmiş performans ve güvenlik dahil olmak üzere yerel görüntü biçimleri [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]ve simge (.ico).  
  
-   Yüksek bit derinliği görüntü veri koruma (32 bit / piksel) kanal başına 8 bit.  
  
-   Geri dönüşlü resim ölçeklendirmeyi, kırpma ve döndürme.  
  
-   Basitleştirilmiş renk yönetimi.  
  
-   Dosya içinde özel meta verileri desteği.  
  
-   Yönetilmeyen altyapı diğer görüntüleri sorunsuz tümleştirme sağlamak üzere yönetilen bileşen yararlanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi özellikleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animasyon ve grafik. Yönetilen bileşen yeni görüntü biçimlerinde otomatik olarak tanınmasını sağlayan Windows Presentation Foundation (WPF) görüntü codec genişletilebilirlik modeli de faydalanır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Çoğu yönetilen [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] bulunan <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> ad alanı, birkaç önemli tür rağmen gibi <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.ImageDrawing> bulunan <xref:System.Windows.Media?displayProperty=nameWithType> ad alanı ve <xref:System.Windows.Controls.Image> içindeyeralıyor<xref:System.Windows.Controls?displayProperty=nameWithType> ad alanı.  
  
 Bu konu, yönetilen bileşen hakkında ek bilgi sağlar. Yönetilmeyen hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] bkz [Yönetilmeyen WPF görüntüleme bileşeni](/windows/desktop/wic/-wic-lh) belgeleri.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF görüntü biçimleri  
 Bir codec bileşeni, belirli bir medya biçiminin kodlamak veya kodunu için kullanılır. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] bir codec bileşeni içerir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]ve resim biçimlerini simgesi. Her codec simgesi hariç olmak üzere, kendi ilgili görüntü biçimlerini kodlama ve kodunu çözme uygulamaları etkinleştirin.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> önemli bir sınıf, kod çözme ve görüntülerini kodlama içinde kullanılır. Temel yapı bloğu olduğu [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] işlem hattı ve belirli bir boyut ve çözümleme piksel tek, sabit bir kümesini temsil eder. A <xref:System.Windows.Media.Imaging.BitmapSource> tek çerçevesi çoklu bir çerçeve resminin olabilir ya da gerçekleştirilen bir dönüştürme sonucu olabilir bir <xref:System.Windows.Media.Imaging.BitmapSource>. İçinde kullanılan birincil sınıfların çoğu üst olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi Imaging <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> görüntü biçimi ' gerçek bit eşlem verileri depolamak için kullanılır. Çok sayıda görüntü biçimlerini yalnızca tek bir destek <xref:System.Windows.Media.Imaging.BitmapFrame>, ancak gibi biçimler [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] ve [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] resim başına birden çok çerçeveyi destekler. Çerçeve tarafından kod çözücüleri girdi verisi olarak kullanılan ve görüntü dosyaları oluşturmak için kodlayıcıya geçirilir.  
  
 Aşağıdaki örnek, gösterir nasıl bir <xref:System.Windows.Media.Imaging.BitmapFrame> içinden oluşturulan bir <xref:System.Windows.Media.Imaging.BitmapSource> ve daha sonra eklenen bir [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] görüntü.  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Görüntü biçimlerinin kodunu çözme  
 Görüntü kodu çözme sistem tarafından kullanılabilecek bir görüntü verileri için bir görüntü biçimi çevrilmesidir. Görüntü verileri işleme, görüntüleme ya da farklı bir biçimde kodlamak için sonra kullanılabilir. Kod çözücü seçim resim biçimine bağlıdır. Belirli bir kod çözücü belirtilmediği sürece codec seçimi otomatik olarak gerçekleşir. Örneklerde [görüntüleme görüntüleri ' WPF'de](#_displayingimages) bölüm göstermek otomatik kod çözme. Yönetilmeyen kullanılarak geliştirilmiş bir özel biçim kod çözücüleri [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] arabirimleri ve sistemi ile otomatik olarak kayıtlı kod çözücü seçimine katılır. Böylece, otomatik olarak görüntülenecek özel biçimler [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Aşağıdaki örnek kodu çözülecek bir bit eşlem kod çözücü kullanımını gösterir. bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] Resmi Biçimlendir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Görüntü biçimi kodlama  
 Görüntü kodlama belirli bir resim biçimine görüntü verilerini çevrilmesidir. Kodlanmış resim verileri, ardından yeni resim dosyaları oluşturmak için kullanılabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] Yukarıda açıklanan görüntü biçimleri için Kodlayıcıları sağlar.  
  
 Aşağıdaki örnek, bir kodlayıcı, yeni oluşturulan bir bit eşlem görüntüsüne kaydetmek için kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>WPF içinde görüntüleri görüntüleme  
 Bir Windows Presentation Foundation (WPF) uygulamasında bir görüntüyü birkaç yolu vardır. Kullanarak görüntüleri görüntülenebilir bir <xref:System.Windows.Controls.Image> denetimi, bir görsel kullanarak boyanan bir <xref:System.Windows.Media.ImageBrush>, veya kullanılarak çizilen bir <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Görüntü denetimi kullanma  
 <xref:System.Windows.Controls.Image> çerçeve öğesi ve uygulamalarda resimleri görüntülemek için birincil yolu değildir. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> iki yolu; öznitelik sözdizimi veya özellik sözdizimi kullanılabilir. Aşağıdaki örnek, öznitelik söz dizimi hem özellik etiketi sözdizimi kullanarak 200 piksel bir görüntüsünü işlemek nasıl gösterir. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Çok sayıda örnek bir <xref:System.Windows.Media.Imaging.BitmapImage> bir görüntü dosyasına başvurmak için nesne. <xref:System.Windows.Media.Imaging.BitmapImage> özelleştirilmiş <xref:System.Windows.Media.Imaging.BitmapSource> için iyileştirilmiş [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yükleniyor ve resimleri görüntülemek için kolay bir yoludur <xref:System.Windows.Controls.Image.Source%2A> , bir <xref:System.Windows.Controls.Image> denetimi.  
  
 Aşağıdaki örnek kodu kullanarak 200 piksel bir görüntüsünü işlemek nasıl gösterir.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> uygulayan <xref:System.ComponentModel.ISupportInitialize> başlatma birden çok özellikleri en iyi duruma getirme arabirimi. Özellik değişiklikleri yalnızca nesnesini başlatma sırasında ortaya çıkabilir. Çağrı <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> başlatmanın başladı sinyal ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> başlatmanın tamamlandığını göstermek için. Başlatıldıktan sonra özellik değişiklikleri göz ardı edilir.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Döndürme, dönüştürülmesi ve bu görüntüleri kırpma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Görüntü özelliklerini kullanarak dönüştürmek kullanıcıların sağlayan <xref:System.Windows.Media.Imaging.BitmapImage> veya ek kullanarak <xref:System.Windows.Media.Imaging.BitmapSource> gibi nesneleri <xref:System.Windows.Media.Imaging.CroppedBitmap> veya <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Bu görüntü dönüşümleri ölçeğini veya görüntü döndürme, görüntü piksel biçimini değiştirme veya görüntü kırpma.  
  
 Görüntü döndürme kullanılarak gerçekleştirilir <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> özelliği <xref:System.Windows.Media.Imaging.BitmapImage>. Döndürme yalnızca 90 derece artışlarla yapılabilir. Aşağıdaki örnekte, bir görüntü 90 derece döndürülür.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Gri tonlamalı yapıldığı gibi görüntüyü bir farklı piksel biçimine dönüştürme kullanarak <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Aşağıdaki örneklerde, bir görüntü için dönüştürülür <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Ya da görüntü kırpma için <xref:System.Windows.UIElement.Clip%2A> özelliği <xref:System.Windows.Controls.Image> veya <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanılabilir. Henüz genellikle, bir görüntünün bir kısmını görüntülemek istiyorsanız <xref:System.Windows.UIElement.Clip%2A> kullanılmalıdır. Kodlama ve bir kırpılan resim kaydetmek gerekiyorsa <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanılmalıdır. Aşağıdaki örnekte, küçük resim özelliği kullanarak bir resim kırpılmış bir <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Görüntüleri uzatma  
 <xref:System.Windows.Controls.Image.Stretch%2A> Özellik denetler görüntü kapsayıcısının dolduracak şekilde nasıl genişletilir. <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.Stretch> sabit listesi:  
  
-   <xref:System.Windows.Media.Stretch.None>: Görüntü çıkış alanı dolduracak şekilde uzatılır değil. Görüntü çıkış alanından daha büyük ise, görüntünün ne uymayan kırpma çıkış alanına çizilir.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Görüntü, çıkış alana sığacak şekilde ölçeklendirilir. Görüntü yüksekliğini ve genişliğini bağımsız olarak ölçeklenir olduğundan, özgün resmin en boy oranını korunmayabilir. Diğer bir deyişle, görüntünün çıkış kapsayıcısı tamamen doldurmak için karışmış olabilir.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Görüntü, çıkış alanına tamamen sığacak şekilde ölçeklendirilir. Görüntünün en boy oranı korunur.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Görüntü, bir görüntünün özgün en boy oranını koruyarak tamamen çıkış alanı dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki örnek, her bir kullanılabilir uygular <xref:System.Windows.Media.Stretch> sabit listeleri için bir <xref:System.Windows.Controls.Image>.  
  
 Aşağıdaki görüntüde, örneğin çıktısında gösterildiği ve farklı etkisini gösterir <xref:System.Windows.Controls.Image.Stretch%2A> ayarları görüntüye uygulanır.  
  
 ![TileBrush Esnetme ayarları farklı](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Farklı esnetme ayarları  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Görüntülerle boyama  
 Görüntüleri görüntülenebilir bir uygulamada boyama tarafından bir <xref:System.Windows.Media.Brush>. Fırçalar boyama etkinleştirme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] basit, düz renk düzenleri ve görüntü karmaşık kümelerine nesneleri. Görüntülerle boyama için kullanmak bir <xref:System.Windows.Media.ImageBrush>. Bir <xref:System.Windows.Media.ImageBrush> bir tür <xref:System.Windows.Media.TileBrush> bir bit eşlem görüntüsü olarak tanımlayan içeriği. Bir <xref:System.Windows.Media.ImageBrush> tarafından belirtilen tek bir görüntü görüntüler, <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği. Etkinleştirme, bozulmayı önlemek ve desenleri ve diğer efektler üretmek nasıl resim, hizalı ve döşendiğini uzatılacağını denetleyebilirsiniz. İle gerçekleştirilebilir bazı efektler aşağıdaki çizimde bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıkış örnekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Şekiller, denetimleri, metin ve görüntü Fırçalar doldurmak için  
  
 Aşağıdaki örnek bir görüntü kullanarak bir düğmenin arka plan boyama yapmayı gösteren bir <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Hakkında ek bilgi için <xref:System.Windows.Media.ImageBrush> ve boyama görüntüleri görmek [görüntüler, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Resim meta verileri  
 Bazı görüntü dosyaları içerik veya dosyanın özelliklerini açıklayan meta veriler içerir. Örneğin, çoğu dijital kameraları, marka ve model görüntü yakalamak için kullanılan kameranın hakkında meta veriler içeren bir görüntü oluşturun. Her görüntü biçimi meta verileri farklı işler ancak [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] her desteklenen görüntü biçimi için meta verileri alma ve depolama Tekdüzen bir yol sağlar.  
  
 Meta verilerine erişimi aracılığıyla sağlanır <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapSource> nesne. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> döndürür bir <xref:System.Windows.Media.Imaging.BitmapMetadata> görüntüsü tarafından bulunan tüm meta veriler içeren nesne. Bu veriler, bir meta veri şema veya farklı şemaların birleşimi olabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] Aşağıdaki resim meta veri şemalarını destekler: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], metin (PNG metinsel veriler) [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], ve [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Meta verileri okuma işlemini basitleştirmek için <xref:System.Windows.Media.Imaging.BitmapMetadata> gibi kolayca erişilebilecek adlandırılmış özellikleri sağlayan <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, ve <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Bu özelliklerin birçoğu ayrıca meta veri yazma için kullanılabilir. Meta veri okumak için ek destek, meta verileri sorgu okuyucu tarafından sağlanır. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> Yöntemi gibi bir dize sorgusuna sağlayarak bir meta veri sorgu okuyucu almak için kullanılır *"/ app1 EXIF /"*. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> depolanan metin almak için kullanılan *"/ metin/açıklama"* konumu.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Meta veri yazma için bir meta veri sorgu yazıcı kullanılır. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> Sorgu yazıcısını alır ve istenen değere ayarlar. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> depolanan metin yazmak için kullanılan *"/ metin/açıklama"* konumu.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Codec genişletilebilirliği  
 Bir çekirdek özelliği [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] yeni görüntü codec bileşenleri için genişletilebilirlik modeli. Bu yönetilmeyen arabirimler codec bileşenleri ile tümleştirmek codec geliştiricilerin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yeni görüntü biçimleri tarafından otomatik olarak kullanılabilmesi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
 Genişletilebilirlik gösteren bir örnek [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], bkz: [Win32 örnek Codec](https://go.microsoft.com/fwlink/?LinkID=160052). Bu örnek, bir kod çözücü ve bir özel görüntü biçimi için Kodlayıcı nasıl oluşturulacağını gösterir.  
  
> [!NOTE]
>  Codec sistem tanıması dijital olarak imzalanması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Imaging.BitmapSource>  
 <xref:System.Windows.Media.Imaging.BitmapImage>  
 <xref:System.Windows.Controls.Image>  
 <xref:System.Windows.Media.Imaging.BitmapMetadata>  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Win32 Codec örneği](https://go.microsoft.com/fwlink/?LinkID=160052)
