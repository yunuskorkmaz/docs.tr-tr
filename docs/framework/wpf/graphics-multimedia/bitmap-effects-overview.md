---
title: Bit Eşlem Efektlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5c304363efe7d0e9bd9e14ff916f8d852ab3a8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636022"
---
# <a name="bitmap-effects-overview"></a>Bit Eşlem Efektlerine Genel Bakış
Bit eşlem efektleri, tasarımcıların ve geliştiricilerin, işlenmiş Windows Presentation Foundation (WPF) içeriğine görsel etkiler uygulamasına olanak tanır. Örneğin, bit eşlem efektleri bir görüntüye veya düğmeye bir <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> etkisini veya Bulanıklaştırma efektini kolayca uygulamanıza olanak tanır.  
  
> [!IMPORTANT]
> .NET Framework 4 veya sonraki sürümlerde, <xref:System.Windows.Media.Effects.BitmapEffect> sınıfı artık kullanılmıyor. <xref:System.Windows.Media.Effects.BitmapEffect> sınıfını kullanmaya çalışırsanız, eski bir özel durum alırsınız. <xref:System.Windows.Media.Effects.BitmapEffect> sınıfının kullanımdan kalkmamış alternatifi <xref:System.Windows.Media.Effects.Effect> sınıfıdır. Çoğu durumda <xref:System.Windows.Media.Effects.Effect> sınıfı önemli ölçüde daha hızlıdır.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF bit eşlem efektleri  
 Bit eşlem efektleri (<xref:System.Windows.Media.Effects.BitmapEffect> nesnesi) basit piksel işleme işlemleridir. Bit eşlem efekti bir <xref:System.Windows.Media.Imaging.BitmapSource> giriş olarak alır ve bir bulanıklaştırma ya da gölge gibi etkiyi uyguladıktan sonra yeni bir <xref:System.Windows.Media.Imaging.BitmapSource> oluşturur. Her bit eşlem efekti, <xref:System.Windows.Media.Effects.BlurBitmapEffect><xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> gibi filtreleme özelliklerini denetleyebilen özellikleri sunar.  
  
 Özel bir durum olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' de efektler, <xref:System.Windows.Controls.Button> veya <xref:System.Windows.Controls.TextBox>gibi canlı <xref:System.Windows.Media.Visual> nesnelerde özellikler olarak ayarlanabilir. Piksel işleme, çalışma zamanında uygulanır ve işlenir. Bu durumda, oluşturma sırasında bir <xref:System.Windows.Media.Visual> otomatik olarak <xref:System.Windows.Media.Imaging.BitmapSource> eşdeğerine dönüştürülür ve <xref:System.Windows.Media.Effects.BitmapEffect>giriş olarak aktarılır. Çıktı, <xref:System.Windows.Media.Visual> nesnesinin varsayılan işleme davranışının yerini alır. <xref:System.Windows.Media.Effects.BitmapEffect> nesnelerinin görselleri yalnızca yazılımda işlemeye zorlamasına neden olur, ancak efektler uygulandığında görsellerde donanım ivmesi yoktur.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>, odak dışı görünen bir nesnenin benzetimini yapar.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> nesnenin çevresi etrafında bir renk Halo oluşturur.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bir nesnenin arkasında gölge oluşturur.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>, bir görüntünün yüzeyini belirtilen eğriye göre Başlatan bir eğim oluşturur.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> yapay ışık kaynağından derinlik ve doku izlenimi vermek için bir <xref:System.Windows.Media.Visual> çarpmaya yönelik bir eşleme oluşturur.  
  
> [!NOTE]
> WPF bit eşlem efektleri yazılım modunda işlenir. Bir efekt uygulayan herhangi bir nesne yazılımda da işlenir. Büyük görseller üzerinde bit eşlem efektleri kullanırken veya bir bit eşlem efektinin özellikleri canlandırdığınızda, performans en çok düşer. Bu, bit eşlem efektlerini bu şekilde bu şekilde kullanmamalısınız, ancak kullanıcılarınızın bekledikleri deneyimi aldığından emin olmak için dikkatli ve test etmeniz gerekir.  
  
> [!NOTE]
> WPF bit eşlem efektleri kısmi güven yürütmeyi desteklemez. Bir uygulamanın bit eşlem efektlerini kullanmak için tam güven izinleri olmalıdır.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Efekt uygulama  
 <xref:System.Windows.Media.Effects.BitmapEffect>, <xref:System.Windows.Media.Visual>bir özelliktir. Bu nedenle, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>veya <xref:System.Windows.UIElement>gibi görsellere efekt uygulamak bir özelliği ayarlamak kadar kolaydır. <xref:System.Windows.UIElement.BitmapEffect%2A>, tek bir <xref:System.Windows.Media.Effects.BitmapEffect> nesnesine ayarlanabilir veya birden çok efekt <xref:System.Windows.Media.Effects.BitmapEffectGroup> nesnesi kullanılarak zincirleme yapılabilir.  
  
 Aşağıdaki örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<xref:System.Windows.Media.Effects.BitmapEffect> nasıl uygulanacağını gösterir.  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Aşağıdaki örnek, koddaki <xref:System.Windows.Media.Effects.BitmapEffect> nasıl uygulanacağını gösterir.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.Canvas>gibi bir düzen kapsayıcısına <xref:System.Windows.Media.Effects.BitmapEffect> uygulandığında, efekt, onun tüm alt öğeleri dahil olmak üzere, öğe veya görselin görsel ağacına uygulanır.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Özel etkiler oluşturma  
 WPF, yönetilen WPF uygulamalarında kullanılabilecek özel etkiler oluşturmak için yönetilmeyen arabirimler de sağlar. Özel bit eşlem efektleri oluşturmaya yönelik ek başvuru malzemeleri için, [YÖNETILMEYEN WPF bit eşlem efekti](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Yönetilmeyen WPF bit eşlem efekti](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Security](../security-wpf.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
