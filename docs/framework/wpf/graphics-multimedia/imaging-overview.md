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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186690"
---
# <a name="imaging-overview"></a>Görüntülemeye Genel Bakış
Bu konu, Microsoft Windows Presentation Foundation Görüntüleme Bileşeni'ne giriş sağlar. WPF Görüntüleme, geliştiricilerin görüntüleri görüntülemesine, dönüştürmesine ve biçimlendirmesine olanak tanır.  

## <a name="wpf-imaging-component"></a>WPF Görüntüleme Bileşeni  
 WPF Görüntüleme, Microsoft Windows'daki görüntüleme özelliklerinde önemli geliştirmeler sağlar. Bitmap görüntüleme veya ortak denetimde görüntü kullanma gibi görüntüleme özellikleri daha önce Microsoft Windows Graphics Device Interface (GDI) veya Microsoft Windows GDI+ kitaplıklarına dayanıyordu. Bu API'ler temel görüntüleme işlevselliği sağlar, ancak kodeksi genişletilebilirlik desteği ve yüksek doğruluk görüntü desteği gibi özelliklerden yoksundur. WPF Görüntüleme, GDI ve GDI+'nın eksikliklerini aşmak ve uygulamalarınızdaki görüntüleri görüntülemek ve kullanmak için yeni bir API seti sağlamak üzere tasarlanmıştır.  
  
 WPF Görüntüleme API'sine, yönetilen bir bileşene ve yönetilmeyen bir bileşene erişmenin iki yolu vardır. Yönetilmeyen bileşen aşağıdaki özellikleri sağlar.  
  
- Yeni veya tescilli görüntü biçimleri için genişletilebilirlik modeli.  
  
- Bitmap (BMP), Joint Photographics Experts Group (JPEG), Portable Network Graphics (PNG), Tagged Image File Format (TIFF), Microsoft Windows Media Photo, Graphics Change Format (GIF) dahil olmak üzere yerel görüntü biçimlerinde geliştirilmiş performans ve güvenlik, ve simge (.ico).  
  
- Kanal başına 8 bit (piksel başına 32 bit) kadar yüksek bit derinliğigörüntü verilerinin korunması.  
  
- Zararsız görüntü ölçekleme, kırpma ve döndürme.  
  
- Basitleştirilmiş renk yönetimi.  
  
- Dosya içi, özel meta veriler için destek.  
  
- Yönetilen bileşen, animasyon ve grafik gibi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]diğer WPF özellikleriyle görüntülerin sorunsuz entegrasyonunu sağlamak için yönetilmeyen altyapıyı kullanır. Yönetilen bileşen ayrıca, WPF uygulamalarında yeni görüntü biçimlerinin otomatik olarak tanınmasını sağlayan Windows Presentation Foundation (WPF) görüntüleme kodeksi genişletilebilirlik modelinden de yararlanır.  
  
 Yönetilen WPF Görüntüleme API'sinin çoğu <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> ad alanında bulunur, ancak <xref:System.Windows.Media?displayProperty=nameWithType> ad <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageDrawing> alanı gibi ve <xref:System.Windows.Controls?displayProperty=nameWithType> ad <xref:System.Windows.Controls.Image> alanında bulunan ve ad alanında bulunan birkaç önemli tür bulunur.  
  
 Bu konu, yönetilen bileşen hakkında ek bilgiler sağlar. Yönetilmeyen API hakkında daha fazla bilgi için [yönetilmeyen WPF Görüntüleme Bileşeni](/windows/desktop/wic/-wic-lh) belgelerine bakın.  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>WPF Görüntü Biçimleri  

 Codec, belirli bir ortam biçimini çözmek veya kodlamak için kullanılır. WPF Görüntüleme BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF ve ICON görüntü biçimleri için bir codec içerir. Bu codec'lerin her biri uygulamaların deşifre edilmesini ve ICON dışında kendi resim biçimlerini kodlamasını sağlar.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>görüntülerin kodlanması nda ve kodlanmasında kullanılan önemli bir sınıftır. WPF Görüntüleme ardışık hattının temel yapı taşıdır ve belirli bir boyut ve çözünürlükte tek, sabit bir piksel kümesini temsil eder. A, <xref:System.Windows.Media.Imaging.BitmapSource> birden çok kare görüntüsünün tek bir çerçevesi olabilir veya bir <xref:System.Windows.Media.Imaging.BitmapSource>. WPF görüntülemede kullanılan birincil sınıfların çoğunun üst <xref:System.Windows.Media.Imaging.BitmapFrame>öğesidir.  
  
 A, <xref:System.Windows.Media.Imaging.BitmapFrame> görüntü biçiminin gerçek biteş verilerini depolamak için kullanılır. GIF ve TIFF <xref:System.Windows.Media.Imaging.BitmapFrame>gibi biçimler görüntü başına birden çok kareyi desteklese de, birçok görüntü biçimi yalnızca tek bir biçimi destekler. Çerçeveler kod çözücüler tarafından giriş verisi olarak kullanılır ve görüntü dosyaları oluşturmak için kodlayıcılara aktarılır.  
  
 Aşağıdaki örnek, a'dan <xref:System.Windows.Media.Imaging.BitmapFrame> nasıl <xref:System.Windows.Media.Imaging.BitmapSource> oluşturulduğunu ve sonra bir TIFF görüntüsüne nasıl eklendirilebildiğini gösterir.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Görüntü Biçimi Çözme  
 Görüntü çözme, görüntü biçiminin sistem tarafından kullanılabilecek görüntü verilerine çevrilmedir. Görüntü verileri daha sonra farklı bir biçimde görüntülemek, işlemek veya kodlamak için kullanılabilir. Kod çözücü seçimi görüntü biçimine bağlıdır. Belirli bir kod çözücü belirtilmediği sürece codec seçimi otomatiktir. WPF bölümünde [Görüntüleyen Görüntüler](#_displayingimages) bölümündeki örnekler otomatik kod çözmeyi gösterir. Yönetilmeyen WPF Görüntüleme arayüzleri kullanılarak geliştirilen ve sisteme kayıtlı özel biçimli kod çözücüler otomatik olarak kod çözücü seçimine katılır. Bu, özel biçimlerin WPF uygulamalarında otomatik olarak görüntülenmesini sağlar.  
  
 Aşağıdaki örnek, BMP biçimli bir görüntünün şifresini çözmek için bir bitmap kod çözücükullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Görüntü Biçimi Kodlama  
 Görüntü kodlama, görüntü verilerinin belirli bir görüntü biçimine çevrilmedir. Kodlanmış görüntü verileri daha sonra yeni görüntü dosyaları oluşturmak için kullanılabilir. WPF Görüntüleme, yukarıda açıklanan görüntü biçimlerinin her biri için kodlayıcısağlar.  
  
 Aşağıdaki örnek, yeni oluşturulan bitmap görüntüsünü kaydetmek için bir kodlayıcının kullanımını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>WPF'de Görüntüleri Görüntüleme  
 Bir Windows Sunu Temeli (WPF) uygulamasında görüntü görüntülemenin birkaç yolu vardır. Görüntüler bir <xref:System.Windows.Controls.Image> denetim kullanılarak görüntülenebilir, bir <xref:System.Windows.Media.ImageBrush>görsel üzerine boyanabilir, bir <xref:System.Windows.Media.ImageDrawing>' kullanarak çizilebilir.  
  
### <a name="using-the-image-control"></a>Görüntü Denetimini Kullanma  
 <xref:System.Windows.Controls.Image>bir çerçeve öğesi dir ve uygulamalarda görüntüleri görüntülemek için birincil yoludur. In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Image> , iki şekilde kullanılabilir; sözdizimi veya özellik sözdizimi atfetmek. Aşağıdaki örnek, hem öznitelik sözdizimini hem de özellik etiketi sözdizimini kullanarak 200 piksel genişliğinde bir görüntünün nasıl işlenir olduğunu gösterir. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için [bkz.](../advanced/dependency-properties-overview.md)  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Örneklerin çoğu, <xref:System.Windows.Media.Imaging.BitmapImage> bir resim dosyasına başvurmak için bir nesne kullanır. <xref:System.Windows.Media.Imaging.BitmapImage>yükleme <xref:System.Windows.Media.Imaging.BitmapSource> için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] optimize edilmiş ve görüntüleri bir denetim olarak <xref:System.Windows.Controls.Image.Source%2A> görüntülemek için <xref:System.Windows.Controls.Image> kolay bir yoldur özelbir durumdur.  
  
 Aşağıdaki örnek, bir görüntünün kod kullanarak 200 piksel genişliğinde nasıl oluşturulabildiğini gösterir.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>birden çok <xref:System.ComponentModel.ISupportInitialize> özellik üzerinde başlatma en iyi duruma getirmek için arabirimi uygular. Özellik değişiklikleri yalnızca nesne başlatma sırasında oluşabilir. Başlatmanın başladığını bildirmek ve <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> başlatmanın tamamlandığını bildirmek için arayın. Başharfe bulaştığında, özellik değişiklikleri yoksayılır.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Görüntüleri Döndürme, Dönüştürme ve Kırpma  
 WPF, kullanıcıların özellikleri kullanarak <xref:System.Windows.Media.Imaging.BitmapImage> veya başka <xref:System.Windows.Media.Imaging.BitmapSource> nesneler <xref:System.Windows.Media.Imaging.CroppedBitmap> kullanarak görüntüleri dönüştürmelerine olanak <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>tanır. Bu görüntü dönüşümleri görüntüyü ölçeklendirebilir veya döndürebilir, görüntünün piksel biçimini değiştirebilir veya görüntüyü kırabilir.  
  
 Görüntü döndürmeleri <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> <xref:System.Windows.Media.Imaging.BitmapImage>. Rotasyonlar sadece 90 derecelik artışlarla yapılabilir. Aşağıdaki örnekte, bir görüntü 90 derece döndürülür.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Görüntüyü gri tonlama gibi farklı bir piksel <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>biçimine dönüştürme yapılır. Aşağıdaki örneklerde, bir görüntü <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Bir görüntüyü kırpmak <xref:System.Windows.UIElement.Clip%2A> için, <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.Imaging.CroppedBitmap> özelliği veya özelliği kullanılabilir. Genellikle, yalnızca bir görüntünün bir bölümünü görüntülemek <xref:System.Windows.UIElement.Clip%2A> istiyorsanız, kullanılmalıdır. Kırpılmış bir görüntüyü kodlamanız ve kaydetmeniz <xref:System.Windows.Media.Imaging.CroppedBitmap> gerekiyorsa, bu görüntü kullanılmalıdır. Aşağıdaki örnekte, bir görüntü Klip özelliği kullanılarak <xref:System.Windows.Media.EllipseGeometry>kırpılır.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Görüntüleri Germe  
 Özellik, <xref:System.Windows.Controls.Image.Stretch%2A> bir resmin kapsayıcısını doldurmak için nasıl gerildiğini denetler. Özellik, <xref:System.Windows.Controls.Image.Stretch%2A> numaralandırma ile <xref:System.Windows.Media.Stretch> tanımlanan aşağıdaki değerleri kabul eder:  
  
- <xref:System.Windows.Media.Stretch.None>: Görüntü çıkış alanını doldurmak için gerilmiş değildir. Görüntü çıkış alanından daha büyükse, görüntü çıkış alanına çizilir ve uymayanlar kırpılır.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Görüntü çıkış alanına uyacak şekilde ölçeklendirilir. Görüntü yüksekliği ve genişliği bağımsız olarak ölçeklendirildiği için, görüntünün özgün en boy oranı korunmayabilir. Diğer bir deyişle, görüntü çıkış kabını tamamen doldurmak için çarpıtılabilir.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Görüntü, çıkış alanına tamamen sığar şekilde ölçeklendirilir. Görüntünün en boy oranı korunur.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Görüntü, görüntünün orijinal en boy oranını korurken çıkış alanını tamamen dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki örnek, kullanılabilir <xref:System.Windows.Media.Stretch> tümumerasyonların her <xref:System.Windows.Controls.Image>birini bir .  
  
 Aşağıdaki resim, örnekteki çıktıyı gösterir ve görüntüye uygulandığında farklı <xref:System.Windows.Controls.Image.Stretch%2A> ayarların etkisini gösterir.  
  
 ![Farklı TileFırça Streç ayarları](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Farklı esneme ayarları  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Resimlerle Boyama  
 Görüntüler de bir <xref:System.Windows.Media.Brush>ile boyama tarafından bir uygulamada görüntülenebilir . Fırçalar, nesneleri [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] basit, düz renklerden karmaşık desen ve görüntü kümelerine kadar her şeyle boyamanızı sağlar. Görüntülerle boyamak için, bir <xref:System.Windows.Media.ImageBrush>. An, <xref:System.Windows.Media.ImageBrush> içeriğini <xref:System.Windows.Media.TileBrush> bitmap görüntüsü olarak tanımlayan bir türdür. Bir <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği tarafından belirtilen tek bir görüntü görüntüler. Görüntünün nasıl uzadığını, hizalanmasını ve döşenmesini denetleyerek bozulmayı önleyebilir ve desenler ve diğer efektler üretebilirsiniz. Aşağıdaki resimde bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıktı örnekleri](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Görüntü fırçaları şekilleri, denetimleri, metni ve daha fazlasını doldurabilir  
  
 Aşağıdaki örnek, bir düğmenin arka planını bir resim <xref:System.Windows.Media.ImageBrush>kullanarak nasıl boyayacağımı gösterir.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Resimler hakkında <xref:System.Windows.Media.ImageBrush> daha fazla bilgi ve boyama için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>Görüntü Meta verileri  
 Bazı resim dosyaları, içeriği veya dosyanın özelliklerini açıklayan meta veriler içerir. Örneğin, çoğu dijital fotoğraf makinesi, görüntüyü yakalamak için kullanılan kameranın molası ve modeli hakkında meta veriler içeren görüntüler oluşturur. Her görüntü biçimi meta verileri farklı işler, ancak WPF Görüntüleme, desteklenen her görüntü biçimi için meta verileri depolamak ve almak için tek tip bir yol sağlar.  
  
 Meta verilere erişim bir <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> <xref:System.Windows.Media.Imaging.BitmapSource> nesnenin özelliği aracılığıyla sağlanır. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>görüntünün <xref:System.Windows.Media.Imaging.BitmapMetadata> içerdiği tüm meta verileri içeren bir nesne döndürür. Bu veriler bir meta veri şemasında veya farklı düzenlerin bir bileşiminde olabilir. WPF Görüntüleme aşağıdaki görüntü meta veri şemalarını destekler: Değiştirilebilir görüntü dosyası (Exif), tEXt (PNG Metinsel Veriler), görüntü dosyası dizini (IFD), Uluslararası Basın Telekomünikasyon Konseyi (IPTC) ve Genişletilebilir Meta veri platformu (XMP).  
  
 Meta verileri okuma işlemini kolaylaştırmak <xref:System.Windows.Media.Imaging.BitmapMetadata> için, kolayca erişilebilen <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A> <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>birkaç adlandırılmış özellik <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>sağlar. Bu adlandırılmış özelliklerin çoğu meta veri yazmak için de kullanılabilir. Meta verileri okumak için ek destek meta veri sorgu okuyucu tarafından sağlanır. Yöntem, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> *"/app1/exif/"* gibi bir dize sorgusu sağlayarak meta veri sorgusu okuyucusu almak için kullanılır. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> *"/Text/Description"* konumunda depolanan metni elde etmek için kullanılır.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Meta veri yazmak için bir meta veri sorgu yazarı kullanılır. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>sorgu yazarını alır ve istenen değeri ayarlar. Aşağıdaki örnekte, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> *"/Text/Description"* konumunda depolanan metni yazmak için kullanılır.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>Codec Ekstensibilite  
 WPF Görüntülemenin temel özelliği yeni görüntü kodlayıcıları için genişletilebilirlik modelidir. Bu yönetilmeyen arabirimler, codec geliştiricilerinin codec'leri WPF ile tümleştirmelerine olanak sağlar, böylece yeni görüntü biçimleri WPF uygulamaları tarafından otomatik olarak kullanılabilir.  
  
 Genişletilebilirlik API'sinin bir örneği için [Win32 Örnek Codec'e](https://go.microsoft.com/fwlink/?LinkID=160052)bakın. Bu örnek, özel bir görüntü biçimi için kod çözücü ve kodlayıcının nasıl oluşturulabildiğini gösterir.  
  
> [!NOTE]
> Sistemin tanıyabilmesi için codec dijital olarak imzalanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 Örnek Codec](https://go.microsoft.com/fwlink/?LinkID=160052)
