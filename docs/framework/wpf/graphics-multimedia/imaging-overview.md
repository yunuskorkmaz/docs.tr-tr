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
ms.openlocfilehash: b60f2871062a12d3bee91a9c6d9883222b3034f4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733571"
---
# <a name="imaging-overview"></a>Görüntülemeye Genel Bakış
Bu konu, Microsoft Windows Presentation Foundation Imaging bileşenine bir giriş sağlar. WPF Imaging, geliştiricilerin resimleri görüntülemesine, dönüştürmelerine ve biçimlendirmeye olanak sağlar.  

## <a name="wpf-imaging-component"></a>WPF Imaging bileşeni  
 WPF Imaging, Microsoft Windows 'daki görüntüleme özellikleri açısından önemli geliştirmeler sağlar. Bir bit eşlem görüntüleme veya ortak denetimde görüntü kullanma gibi görüntüleme özellikleri, daha önce Microsoft Windows Grafik Cihaz Arabirimi (GDI) veya Microsoft Windows GDI+ kitaplıklarına bağımlıdır. Bu API, taban çizgisi görüntüleme işlevselliği sağlar, ancak codec genişletilebilirliği ve yüksek uygunlukta görüntü desteği gibi özelliklerin bulunmaması. WPF Imaging, GDI ve GDI+ ' nın eksiklılarını aşmak için tasarlanmıştır ve uygulamalarınızın içindeki görüntüleri görüntülemesi ve kullanmak için yeni bir API kümesi sağlar.  
  
 Yönetilen bir bileşeni ve yönetilmeyen bileşeni WPF Görüntüleme API 'sine erişmenin iki yolu vardır. Yönetilmeyen bileşen aşağıdaki özellikleri sağlar.  
  
- Yeni veya özel görüntü biçimleri için genişletilebilirlik modeli.  
  
- Bit eşlem (BMP), Joint Photografik uzmanları grubu (JPEG), Taşınabilir Ağ Grafikleri (PNG), etiketli resim dosyası biçimi (TIFF), Microsoft Windows Medya fotoğrafı, grafik değişim biçimi (GIF) gibi yerel görüntü biçimlerinde geliştirilmiş performans ve güvenlik ve simgesi (. ico).  
  
- Kanal başına 8 bite kadar yüksek bit derinlikli görüntü verilerinin korunması (piksel başına 32 bit).  
  
- Geri dönüşlü görüntü ölçekleme, kırpma ve döndürme.  
  
- Basitleştirilmiş renk yönetimi.  
  
- Dosya içi, özel meta veriler için destek.  
  
- Yönetilen bileşen, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animasyon ve grafik gibi diğer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellikleriyle görüntülerin sorunsuz bir şekilde tümleştirilmesini sağlamak için yönetilmeyen altyapıyı kullanır. Yönetilen bileşen ayrıca, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarda yeni görüntü biçimlerinin otomatik olarak tanınmasını sağlayan Windows Presentation Foundation (WPF) görüntüleme codec genişletilebilirliği modelinden de faydalanır.  
  
 Yönetilen WPF Görüntüleme API 'sinin çoğunluğu <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> ad alanında bulunur, ancak <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.ImageDrawing> gibi çeşitli önemli türler <xref:System.Windows.Media?displayProperty=nameWithType> ad alanında bulunur ve <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls?displayProperty=nameWithType> ad alanında yer alır.  
  
 Bu konu, yönetilen bileşen hakkında ek bilgiler sağlar. Yönetilmeyen API hakkında daha fazla bilgi için [YÖNETILMEYEN WPF Imaging bileşeni](/windows/desktop/wic/-wic-lh) belgelerine bakın.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF resim biçimleri  

 Bir codec bileşeni, belirli bir medya biçiminin kodunu çözmek veya kodlamak için kullanılır. WPF Imaging, BMP, JPEG, PNG, TIFF, Windows Medya fotoğrafı, GIF ve SIMGE resim biçimleri için bir codec bileşeni içerir. Bu codec bileşenlerinden her biri, uygulamaların kodunu çözmelerini ve SIMGE dışında kendi görüntü biçimlerini kodlamalarını sağlar.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>, görüntülerin kod çözmede ve kodlamasında kullanılan önemli bir sınıftır. WPF görüntüleme işlem hattının temel yapı taşıdır ve belirli bir boyut ve çözünürlükte tek bir sabit piksel kümesini temsil eder. <xref:System.Windows.Media.Imaging.BitmapSource> birden çok çerçeve görüntüsünün tek bir çerçevesi olabilir veya bir <xref:System.Windows.Media.Imaging.BitmapSource>üzerinde gerçekleştirilen dönüşümün sonucu olabilir. Bu, <xref:System.Windows.Media.Imaging.BitmapFrame>gibi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Imaging 'de kullanılan birçok birincil sınıfların üst öğesidir.  
  
 Bir görüntü biçiminin gerçek bit eşlem verilerini depolamak için bir <xref:System.Windows.Media.Imaging.BitmapFrame> kullanılır. Birçok görüntü biçimi yalnızca tek bir <xref:System.Windows.Media.Imaging.BitmapFrame>destekler, ancak GIF ve TIFF gibi biçimler görüntü başına birden çok çerçeveyi destekler. Çerçeveler, kod çözücüleri tarafından giriş verisi olarak kullanılır ve görüntü dosyaları oluşturmak için kodlayıcılara geçirilir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Imaging.BitmapFrame> <xref:System.Windows.Media.Imaging.BitmapSource> nasıl oluşturulduğunu ve sonra bir TIFF görüntüsüne eklendiğini gösterir.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Görüntü biçimi kod çözme  
 Görüntü kod çözme, bir görüntü biçiminin sistem tarafından kullanılabilecek verileri görüntüye dönüştürmesidir. Görüntü verileri daha sonra farklı bir biçimde görüntüleme, işleme veya kodlama için kullanılabilir. Kod çözücü seçimi resim biçimini temel alır. Belirli bir kod çözücü belirtilmedikçe, codec bileşeni seçimi otomatiktir. [WPF resimlerini görüntüleme](#_displayingimages) bölümünde örnekleri otomatik kod çözme gösterilmektedir. Yönetilmeyen WPF görüntüleme arabirimleri kullanılarak geliştirilen ve sisteme kaydedilen özel biçim kod çözücüleri, kod çözücü seçimine otomatik olarak katılır. Bu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarında özel biçimlerin otomatik olarak görüntülenmesine izin verir.  
  
 Aşağıdaki örnek, bir BMP biçimli görüntünün kodunu çözmek için bir bit eşlem kod çözücünün kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Görüntü biçimi kodlaması  
 Görüntü kodlama, görüntü verilerinin belirli bir görüntü biçimine çevirmesidir. Daha sonra kodlanmış görüntü verileri yeni resim dosyaları oluşturmak için kullanılabilir. WPF Imaging, yukarıda açıklanan her bir görüntü biçimi için kodlayıcılar sağlar.  
  
 Aşağıdaki örnek, yeni oluşturulan bir bit eşlem görüntüsünü kaydetmek için bir kodlayıcı kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>WPF 'de görüntü görüntüleme  
 Bir Windows Presentation Foundation (WPF) uygulamasında görüntü görüntülemenin birkaç yolu vardır. Görüntüler bir <xref:System.Windows.Controls.Image> denetimi kullanılarak görüntülenebilir, <xref:System.Windows.Media.ImageBrush>kullanılarak görselde boyanmıştır veya <xref:System.Windows.Media.ImageDrawing>kullanılarak çizilir.  
  
### <a name="using-the-image-control"></a>Görüntü denetimini kullanma  
 <xref:System.Windows.Controls.Image>, bir çerçeve öğesidir ve uygulamalarda görüntüleri görüntülemenin birincil yoludur. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> iki şekilde kullanılabilir; öznitelik sözdizimi veya özellik sözdizimi. Aşağıdaki örnek, hem öznitelik sözdizimini hem de özellik etiketi sözdizimini kullanarak bir görüntünün 200 piksel genişliğinde nasıl işleneceğini gösterir. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Örneklerin birçoğu bir resim dosyasına başvurmak için <xref:System.Windows.Media.Imaging.BitmapImage> nesnesini kullanır. <xref:System.Windows.Media.Imaging.BitmapImage>, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yükleme için en iyi duruma getirilmiş özelleştirilmiş bir <xref:System.Windows.Media.Imaging.BitmapSource> ve görüntüleri bir <xref:System.Windows.Controls.Image> denetiminin <xref:System.Windows.Controls.Image.Source%2A> olarak görüntülemenin kolay bir yoludur.  
  
 Aşağıdaki örnek, kod kullanarak bir görüntünün 200 piksel genelinde nasıl işleneceğini gösterir.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>, başlatmayı birden çok özellik üzerinde iyileştirmek için <xref:System.ComponentModel.ISupportInitialize> arabirimini uygular. Özellik değişiklikleri yalnızca nesne başlatılırken oluşabilir. Başlatmanın başladığını göstermek ve başlatmanın tamamlandığını bildirmek için <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> çağırın. Başlatıldıktan sonra özellik değişiklikleri yok sayılır.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Görüntüleri döndürme, dönüştürme ve kırpma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], kullanıcıların <xref:System.Windows.Media.Imaging.BitmapImage> özelliklerini kullanarak veya <xref:System.Windows.Media.Imaging.CroppedBitmap> veya <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>gibi ek <xref:System.Windows.Media.Imaging.BitmapSource> nesneleri kullanarak görüntüleri dönüştürmesine olanak sağlar. Bu görüntü dönüştürmeleri bir görüntüyü ölçeklendirebilir veya döndürebilir, bir görüntünün piksel biçimini değiştirebilir veya bir görüntüyü kırpabilir.  
  
 Resim döndürmeler, <xref:System.Windows.Media.Imaging.BitmapImage><xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> özelliği kullanılarak gerçekleştirilir. Döndürmeler yalnızca 90 derece artışlarla yapılabilir. Aşağıdaki örnekte, bir görüntü 90 derece döndürülür.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Bir görüntüyü gri tonlamalı gibi farklı bir piksel biçimine dönüştürmek <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>kullanılarak yapılır. Aşağıdaki örneklerde bir görüntü <xref:System.Windows.Media.PixelFormats.Gray4%2A>dönüştürülür.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Bir görüntüyü kırpmak için <xref:System.Windows.Controls.Image> veya <xref:System.Windows.Media.Imaging.CroppedBitmap> <xref:System.Windows.UIElement.Clip%2A> özelliği kullanılabilir. Genellikle, yalnızca bir görüntünün bir kısmını göstermek istiyorsanız <xref:System.Windows.UIElement.Clip%2A> kullanılmalıdır. Kırpılmış bir görüntüyü kodlamak ve kaydetmeniz gerekiyorsa <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanılmalıdır. Aşağıdaki örnekte, bir resim, bir <xref:System.Windows.Media.EllipseGeometry>kullanılarak klip özelliği kullanılarak kırpılır.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Görüntüleri uzatma  
 <xref:System.Windows.Controls.Image.Stretch%2A> özelliği bir görüntünün kapsayıcısını doldurmak için nasıl uzatılacağını denetler. <xref:System.Windows.Controls.Image.Stretch%2A> özelliği, <xref:System.Windows.Media.Stretch> numaralandırması tarafından tanımlanan aşağıdaki değerleri kabul eder:  
  
- <xref:System.Windows.Media.Stretch.None>: görüntü, çıkış alanını doldurmak için uzatılmamıştır. Görüntü çıkış alanından büyükse, görüntü çıkış alanına çizilir ve sığmayan öğeleri kırpmaz.  
  
- <xref:System.Windows.Media.Stretch.Fill>: görüntü çıktı alanına uyacak şekilde ölçeklendirilir. Görüntü yüksekliği ve genişliği bağımsız olarak ölçeklendirildikleri için görüntünün orijinal en boy oranı korunmayabilir. Diğer bir deyişle, çıkış kapsayıcısını tamamen doldurması için görüntü çarpıtılmış olabilir.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: görüntü, çıkış alanına tamamen sığacak şekilde ölçeklendirilir. Görüntünün en boy oranı korunur.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: görüntü, görüntünün özgün en boy oranını korurken çıkış alanını tamamen dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki örnek, kullanılabilir <xref:System.Windows.Media.Stretch> Numaralandırmaların her birini bir <xref:System.Windows.Controls.Image>uygular.  
  
 Aşağıdaki görüntüde, örneğin çıktısı gösterilmektedir ve bir görüntüye uygulandığında farklı <xref:System.Windows.Controls.Image.Stretch%2A> ayarlarının olduğunu etkilediğini gösterir.  
  
 ![Farklı TileBrush Esnetme ayarları](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Farklı Esnetme ayarları  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Resimlerle boyama  
 Görüntüler, bir <xref:System.Windows.Media.Brush>ile boyayarak bir uygulamada da görüntülenebilir. Fırçalar, basit ve düz renklerle karmaşık desen ve resim kümelerine [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nesneleri boyamanıza imkan tanır. Resimlerle boyamak için bir <xref:System.Windows.Media.ImageBrush>kullanın. <xref:System.Windows.Media.ImageBrush>, içeriğini bir bit eşlem görüntüsü olarak tanımlayan bir <xref:System.Windows.Media.TileBrush> türüdür. <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği tarafından belirtilen tek bir görüntüyü görüntüler. Resmin nasıl uzatılacağını, hizalandığını ve döşeli olduğunu denetleyebilir, bu da deformasyonu ve diğer etkileri üretir. Aşağıdaki çizimde bir <xref:System.Windows.Media.ImageBrush>ile elde edilebilir bazı etkiler gösterilmektedir.  
  
 ![ImageBrush çıkış örnekleri](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Görüntü fırçaları şekilleri, denetimleri, metinleri ve daha fazlasını doldurabilir  
  
 Aşağıdaki örnek, bir düğmenin arka planının <xref:System.Windows.Media.ImageBrush>kullanarak bir görüntüyle nasıl boyanacağını gösterir.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 <xref:System.Windows.Media.ImageBrush> ve boyama görüntüleri hakkında daha fazla bilgi için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Görüntü meta verileri  
 Bazı görüntü dosyaları, dosyanın içeriğini veya özelliklerini açıklayan meta veriler içerir. Örneğin, çoğu dijital kamera, görüntüyü yakalamak için kullanılan kameranın marka ve modeliyle ilgili meta verileri içeren görüntüler oluşturur. Her görüntü biçimi meta verileri farklı işler, ancak WPF Imaging desteklenen her görüntü biçimi için meta verileri depolamanın ve almanın Tekdüzen bir yolunu sağlar.  
  
 Meta verilere erişim, bir <xref:System.Windows.Media.Imaging.BitmapSource> nesnesinin <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> özelliği aracılığıyla sağlanır. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> görüntünün içerdiği tüm meta verileri içeren bir <xref:System.Windows.Media.Imaging.BitmapMetadata> nesnesi döndürür. Bu veriler bir meta veri şemasında veya farklı şemalarla birlikte olabilir. WPF Imaging, şu görüntü meta veri şemalarını destekler: takas edilebilir görüntü dosyası (Exif), metin (PNG metin verileri), görüntü dosyası dizini (ıFD), uluslararası iletişim (ıPTC) ve Genişletilebilir Meta veri platformu (XMP).  
  
 <xref:System.Windows.Media.Imaging.BitmapMetadata> meta verileri okuma işlemini basitleştirmek için, <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>ve <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>gibi kolayca erişilebilen çeşitli adlandırılmış özellikler sağlar. Bu adlandırılmış özelliklerin birçoğu, meta verileri yazmak için de kullanılabilir. Meta veri okuma için ek destek, meta veri sorgu okuyucusu tarafından sağlanır. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> yöntemi, *"/APP1/Exif/"* gibi bir dize sorgusu sağlayarak meta veri sorgu okuyucusunu almak için kullanılır. Aşağıdaki örnekte, *"/Text/Description"* konumunda depolanan metni almak için <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> kullanılır.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Meta veri yazmak için bir meta veri sorgu yazıcısı kullanılır. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> sorgu yazıcısını alır ve istenen değeri ayarlar. Aşağıdaki örnekte, *"/Text/Description"* konumunda depolanan metni yazmak için <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> kullanılır.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Codec genişletilebilirliği  
 WPF Imaging 'in temel bir özelliği, yeni görüntü codec bileşenleri için genişletilebilirlik modelidir. Bu yönetilmeyen arabirimler, codec geliştiricilerinin codec bileşenlerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ile tümleştirmesini sağlar, böylece yeni resim biçimleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar tarafından otomatik olarak kullanılabilir.  
  
 Genişletilebilirlik API 'sinin bir örneği için bkz. [Win32 örnek codec bileşeni](https://go.microsoft.com/fwlink/?LinkID=160052). Bu örnek, bir özel görüntü biçimi için bir kod çözücü ve kodlayıcı oluşturmayı gösterir.  
  
> [!NOTE]
> Sistemin tanıması için codec bileşeninin dijital olarak imzalanması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 örnek codec](https://go.microsoft.com/fwlink/?LinkID=160052)
