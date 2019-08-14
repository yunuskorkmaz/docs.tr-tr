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
ms.openlocfilehash: fcf5e8e68492f4d1ff75221384b08ffad2b939f3
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971956"
---
# <a name="imaging-overview"></a>Görüntülemeye Genel Bakış
Bu konu, [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]öğesine bir giriş sağlar. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]geliştiricilerin resimleri görüntülemesine, dönüştürmelerine ve biçimlendirmeye olanak sağlar.  

## <a name="wpf-imaging-component"></a>WPF Imaging bileşeni  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]içindeki [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]görüntüleme özelliklerine önemli geliştirmeler sağlar. Bir bit eşlem görüntüleme veya ortak denetimde görüntü kullanma gibi görüntüleme özellikleri, daha önce Microsoft Windows Grafik Cihaz Arabirimi (GDI) veya Microsoft Windows GDI+ kitaplıklarına bağımlıdır. Bu API, taban çizgisi görüntüleme işlevselliği sağlar, ancak codec genişletilebilirliği ve yüksek uygunlukta görüntü desteği gibi özelliklerin bulunmaması. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)], GDI ve GDI+ 'ın eksiklılarını aşmak ve uygulamalarınızın içindeki görüntüleri görüntülemesi ve kullanmak için yeni bir API kümesi sağlamak üzere tasarlanmıştır.  
  
 Yönetilen bir bileşen ve yönetilmeyen bileşen [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] API 'sine erişmenin iki yolu vardır. Yönetilmeyen bileşen aşağıdaki özellikleri sağlar.  
  
- Yeni veya özel görüntü biçimleri için genişletilebilirlik modeli.  
  
- Bit eşlem (BMP), Joint Photografik uzmanları grubu (JPEG), [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)],, grafik değişim biçimi (GIF) ve simge (. ico) dahil yerel görüntü biçimlerinde gelişmiş performans ve güvenlik.  
  
- Kanal başına 8 bite kadar yüksek bit derinlikli görüntü verilerinin korunması (piksel başına 32 bit).  
  
- Geri dönüşlü görüntü ölçekleme, kırpma ve döndürme.  
  
- Basitleştirilmiş renk yönetimi.  
  
- Dosya içi, özel meta veriler için destek.  
  
- Yönetilen bileşen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animasyon ve grafik gibi diğer özelliklerle görüntülerin sorunsuz bir şekilde tümleştirilmesini sağlamak için yönetilmeyen altyapıyı kullanır. Yönetilen bileşen ayrıca, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarda yeni görüntü biçimlerinin otomatik olarak tanınmasını sağlayan Windows Presentation Foundation (WPF) görüntüleme codec genişletilebilirliği modelinden de faydalanır.  
  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] Yönetilen API 'nin çoğunluğu <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Controls?displayProperty=nameWithType> <xref:System.Windows.Controls.Image> <xref:System.Windows.Media?displayProperty=nameWithType> ad alanında bulunur, ancak gibi birçok önemli tür vardır ancak ad alanında bulunur ve <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> uzayına.  
  
 Bu konu, yönetilen bileşen hakkında ek bilgiler sağlar. Yönetilmeyen API hakkında daha fazla bilgi için [YÖNETILMEYEN WPF Imaging bileşeni](/windows/desktop/wic/-wic-lh) belgelerine bakın.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF resim biçimleri  
 Bir codec bileşeni, belirli bir medya biçiminin kodunu çözmek veya kodlamak için kullanılır. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]BMP, JPEG, [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)],, [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], GIF ve Icon resim biçimleri için bir codec bileşeni içerir. Bu codec bileşenlerinden her biri, uygulamaların kodunu çözmelerini ve SIMGE dışında kendi görüntü biçimlerini kodlamalarını sağlar.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>, görüntülerin kod çözmede ve kodlamasında kullanılan önemli bir sınıftır. Bu işlem [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] hattının temel yapı taşıdır ve belirli bir boyut ve çözünürlükte tek bir sabit piksel kümesini temsil eder. , Birden çok çerçeve görüntüsünün tek bir çerçevesi olabilir veya bir <xref:System.Windows.Media.Imaging.BitmapSource>üzerinde gerçekleştirilen dönüşümün sonucu olabilir. <xref:System.Windows.Media.Imaging.BitmapSource> Bu, Imaging [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Media.Imaging.BitmapFrame>'de gibi kullanılan birincil sınıfların birçoğunun üst öğesidir.  
  
 Bir <xref:System.Windows.Media.Imaging.BitmapFrame> görüntü biçiminin gerçek bit eşlem verilerini depolamak için kullanılır. Birçok görüntü biçimi yalnızca tek <xref:System.Windows.Media.Imaging.BitmapFrame>bir destekler, ancak GIF gibi biçimler ve [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] görüntü başına birden çok çerçeveyi destekler. Çerçeveler, kod çözücüleri tarafından giriş verisi olarak kullanılır ve görüntü dosyaları oluşturmak için kodlayıcılara geçirilir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Imaging.BitmapFrame> <xref:System.Windows.Media.Imaging.BitmapSource> ' dan nasıl oluşturulduğunu ve sonra bir görüntüyeeklendiğinigösterir.[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Görüntü biçimi kod çözme  
 Görüntü kod çözme, bir görüntü biçiminin sistem tarafından kullanılabilecek verileri görüntüye dönüştürmesidir. Görüntü verileri daha sonra farklı bir biçimde görüntüleme, işleme veya kodlama için kullanılabilir. Kod çözücü seçimi resim biçimini temel alır. Belirli bir kod çözücü belirtilmedikçe, codec bileşeni seçimi otomatiktir. [WPF resimlerini görüntüleme](#_displayingimages) bölümünde örnekleri otomatik kod çözme gösterilmektedir. Yönetilmeyen [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] arabirimler kullanılarak geliştirilen ve sistemle kaydedilen özel biçim kod çözücüleri, kod çözücü seçimine otomatik olarak katılır. Bu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özel biçimlerin uygulamalarda otomatik olarak görüntülenmesine izin verir.  
  
 Aşağıdaki örnek, bir BMP biçimli görüntünün kodunu çözmek için bir bit eşlem kod çözücünün kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Görüntü biçimi kodlaması  
 Görüntü kodlama, görüntü verilerinin belirli bir görüntü biçimine çevirmesidir. Daha sonra kodlanmış görüntü verileri yeni resim dosyaları oluşturmak için kullanılabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]Yukarıda açıklanan görüntü biçimlerinin her biri için kodlayıcılar sağlar.  
  
 Aşağıdaki örnek, yeni oluşturulan bir bit eşlem görüntüsünü kaydetmek için bir kodlayıcı kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>WPF 'de görüntü görüntüleme  
 Bir Windows Presentation Foundation (WPF) uygulamasında görüntü görüntülemenin birkaç yolu vardır. Görüntüler, bir <xref:System.Windows.Controls.Image> denetim kullanılarak görüntülenebilir, bir <xref:System.Windows.Media.ImageBrush>görsel üzerinde boyanmış veya kullanılarak çizilir <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Görüntü denetimini kullanma  
 <xref:System.Windows.Controls.Image>, bir çerçeve öğesidir ve uygulamalarda görüntüleri görüntülemenin birincil yoludur. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ,<xref:System.Windows.Controls.Image> iki şekilde kullanılabilir; öznitelik sözdizimi veya özellik sözdizimi. Aşağıdaki örnek, hem öznitelik sözdizimini hem de özellik etiketi sözdizimini kullanarak bir görüntünün 200 piksel genişliğinde nasıl işleneceğini gösterir. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Örneklerin birçoğu bir görüntü dosyasına başvurmak <xref:System.Windows.Media.Imaging.BitmapImage> için bir nesnesi kullanır. <xref:System.Windows.Media.Imaging.BitmapImage>, yükleme için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en iyi duruma getirilmiş ve görüntüleri bir <xref:System.Windows.Controls.Image> denetim olarak <xref:System.Windows.Controls.Image.Source%2A> görüntülemenin kolay bir yoludur. <xref:System.Windows.Media.Imaging.BitmapSource>  
  
 Aşağıdaki örnek, kod kullanarak bir görüntünün 200 piksel genelinde nasıl işleneceğini gösterir.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>birden çok özelliklerde başlatmayı iyileştirmek için arabiriminiuygular.<xref:System.ComponentModel.ISupportInitialize> Özellik değişiklikleri yalnızca nesne başlatılırken oluşabilir. Başlatmanın <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> başladığını belirten ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> başlatmanın tamamlandığını belirten sinyal çağrısı. Başlatıldıktan sonra özellik değişiklikleri yok sayılır.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Görüntüleri döndürme, dönüştürme ve kırpma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Kullanıcıların, <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.Imaging.CroppedBitmap> <xref:System.Windows.Media.Imaging.BitmapSource> veya<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>gibi ek nesneleri kullanarak veya özelliklerini kullanarak görüntüleri dönüştürmesine olanak sağlar. Bu görüntü dönüştürmeleri bir görüntüyü ölçeklendirebilir veya döndürebilir, bir görüntünün piksel biçimini değiştirebilir veya bir görüntüyü kırpabilir.  
  
 Resim döndürmeler, <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> <xref:System.Windows.Media.Imaging.BitmapImage>özelliği kullanılarak gerçekleştirilir. Döndürmeler yalnızca 90 derece artışlarla yapılabilir. Aşağıdaki örnekte, bir görüntü 90 derece döndürülür.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Bir görüntüyü gri tonlamalı gibi farklı bir piksel biçimine dönüştürmek kullanılarak <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>yapılır. Aşağıdaki örneklerde bir görüntü öğesine <xref:System.Windows.Media.PixelFormats.Gray4%2A>dönüştürülür.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Bir görüntüyü <xref:System.Windows.UIElement.Clip%2A> kırpmak için <xref:System.Windows.Controls.Image> ya <xref:System.Windows.Media.Imaging.CroppedBitmap> da özelliği kullanılabilir. Genellikle, yalnızca bir görüntünün <xref:System.Windows.UIElement.Clip%2A> bir kısmını göstermek istiyorsanız kullanılmalıdır. Kırpılmış bir görüntüyü <xref:System.Windows.Media.Imaging.CroppedBitmap> kodlamak ve kaydetmeniz gerekiyorsa, kullanılmalıdır. Aşağıdaki örnekte, bir <xref:System.Windows.Media.EllipseGeometry>resim kullanılarak Clip özelliği kullanılarak kırpılacak.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Görüntüleri uzatma  
 Özelliği <xref:System.Windows.Controls.Image.Stretch%2A> , bir görüntünün kapsayıcısını doldurmak için nasıl uzatılacağını denetler. Özelliği, <xref:System.Windows.Media.Stretch> sabit listesi tarafından tanımlanan aşağıdaki değerleri kabul eder: <xref:System.Windows.Controls.Image.Stretch%2A>  
  
- <xref:System.Windows.Media.Stretch.None>: Görüntü, çıkış alanını doldurmak için uzatılmamıştır. Görüntü çıkış alanından büyükse, görüntü çıkış alanına çizilir ve sığmayan öğeleri kırpmaz.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Görüntü, çıktı alanına uyacak şekilde ölçeklendirilir. Görüntü yüksekliği ve genişliği bağımsız olarak ölçeklendirildikleri için görüntünün orijinal en boy oranı korunmayabilir. Diğer bir deyişle, çıkış kapsayıcısını tamamen doldurması için görüntü çarpıtılmış olabilir.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Görüntü, çıkış alanına tamamen uyacak şekilde ölçeklendirilir. Görüntünün en boy oranı korunur.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Görüntü, görüntünün özgün en boy oranını korurken çıkış alanını tamamen dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki örnek, kullanılabilir <xref:System.Windows.Media.Stretch> Numaralandırmaların her birini bir <xref:System.Windows.Controls.Image>öğesine uygular.  
  
 Aşağıdaki görüntüde, örnekteki çıkış gösterilmektedir ve farklı <xref:System.Windows.Controls.Image.Stretch%2A> ayarların bir görüntüye uygulandığında etkisi gösterilmektedir.  
  
 ![Farklı TileBrush Esnetme ayarları](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Farklı Esnetme ayarları  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Resimlerle boyama  
 Görüntüler, ile boyayarak bir <xref:System.Windows.Media.Brush>uygulamada da görüntülenebilir. Fırçalar, nesneleri basit, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düz renklerle karmaşık desen ve görüntü kümelerine göre boyamanıza imkan tanır. Resimlerle boyamak için bir <xref:System.Windows.Media.ImageBrush>kullanın. , İçeriğini bir bit eşlem <xref:System.Windows.Media.TileBrush> resmi olarak tanımlayan bir türüdür. <xref:System.Windows.Media.ImageBrush> , Özelliği<xref:System.Windows.Media.ImageBrush.ImageSource%2A> tarafından belirtilen tek bir görüntüyü <xref:System.Windows.Media.ImageBrush> görüntüler. Resmin nasıl uzatılacağını, hizalandığını ve döşeli olduğunu denetleyebilir, bu da deformasyonu ve diğer etkileri üretir. Aşağıdaki çizimde, ile <xref:System.Windows.Media.ImageBrush>elde edilebilir bazı etkiler gösterilmektedir.  
  
 ![ImageBrush çıkış örnekleri](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Görüntü fırçaları şekilleri, denetimleri, metinleri ve daha fazlasını doldurabilir  
  
 Aşağıdaki örnek, bir düğmenin arka planının, kullanarak <xref:System.Windows.Media.ImageBrush>bir görüntüyle nasıl boyanacağını gösterir.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Görüntüleri ve boyama hakkında <xref:System.Windows.Media.ImageBrush> ek bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Görüntü meta verileri  
 Bazı görüntü dosyaları, dosyanın içeriğini veya özelliklerini açıklayan meta veriler içerir. Örneğin, çoğu dijital kamera, görüntüyü yakalamak için kullanılan kameranın marka ve modeliyle ilgili meta verileri içeren görüntüler oluşturur. Her görüntü biçimi meta verileri farklı işler [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] , ancak desteklenen her görüntü biçimi için meta verileri depolamak ve almak için Tekdüzen bir yöntem sağlar.  
  
 Meta verilere erişim, bir <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> <xref:System.Windows.Media.Imaging.BitmapSource> nesnenin özelliği aracılığıyla sağlanır. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>görüntünün içerdiği <xref:System.Windows.Media.Imaging.BitmapMetadata> tüm meta verileri içeren bir nesne döndürür. Bu veriler bir meta veri şemasında veya farklı şemalarla birlikte olabilir. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]Aşağıdaki görüntü meta veri şemalarını destekler: Takas edilebilir görüntü dosyası (Exif), metin (PNG metin verileri), görüntü dosyası dizini (ıFD), uluslararası iletişim, telekomünikasyon (ıPTC) ve [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Meta verileri <xref:System.Windows.Media.Imaging.BitmapMetadata> okuma işlemini basitleştirmek için, ve <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>gibi kolayca erişilebilen <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A> <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>çeşitli adlandırılmış özellikler sağlar. Bu adlandırılmış özelliklerin birçoğu, meta verileri yazmak için de kullanılabilir. Meta veri okuma için ek destek, meta veri sorgu okuyucusu tarafından sağlanır. Yöntemi <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> , *"/APP1/Exif/"* gibi bir dize sorgusu sağlayarak meta veri sorgu okuyucuyu almak için kullanılır. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> *"/Text/Description"* konumunda depolanan metni almak için kullanılır.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Meta veri yazmak için bir meta veri sorgu yazıcısı kullanılır. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>sorgu yazıcısını alır ve istenen değeri ayarlar. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> *"/Text/Description"* konumunda depolanan metni yazmak için kullanılır.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Codec genişletilebilirliği  
 Uygulamasının [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] çekirdek özelliği, yeni görüntü codec bileşenleri için genişletilebilirlik modelidir. Bu yönetilmeyen arabirimler, codec geliştiricilerinin codec bileşenlerini ile [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tümleştirmesini sağlar. bu sayede uygulamalar tarafından [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otomatik olarak yeni görüntü biçimleri kullanılabilir.  
  
 Genişletilebilirlik API 'sinin bir örneği için bkz. [Win32 örnek codec bileşeni](https://go.microsoft.com/fwlink/?LinkID=160052). Bu örnek, bir özel görüntü biçimi için bir kod çözücü ve kodlayıcı oluşturmayı gösterir.  
  
> [!NOTE]
>  Sistemin tanıması için codec bileşeninin dijital olarak imzalanması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 örnek codec](https://go.microsoft.com/fwlink/?LinkID=160052)
