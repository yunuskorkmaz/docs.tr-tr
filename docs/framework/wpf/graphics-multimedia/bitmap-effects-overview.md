---
title: Bit Eşlem Efektlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935295"
---
# <a name="bitmap-effects-overview"></a>Bit Eşlem Efektlerine Genel Bakış
Bit eşlem efektleri, tasarımcıların ve geliştiricilerin, işlenmiş Windows Presentation Foundation (WPF) içeriğine görsel etkiler uygulamasına olanak tanır. Örneğin, bit eşlem efektleri bir görüntüye veya düğmeye kolayca <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekt veya bulanıklaştırma efekti uygulamanıza olanak tanır.  
  
> [!IMPORTANT]
> .NET Framework 4 veya sonraki sürümlerde, <xref:System.Windows.Media.Effects.BitmapEffect> sınıf artık kullanılmıyor. <xref:System.Windows.Media.Effects.BitmapEffect> Sınıfını kullanmaya çalışırsanız, eski bir özel durum alırsınız. <xref:System.Windows.Media.Effects.BitmapEffect> Sınıfın<xref:System.Windows.Media.Effects.Effect> kullanımdan kalkmamış alternatifi sınıfı. Çoğu durumda, <xref:System.Windows.Media.Effects.Effect> sınıfı önemli ölçüde daha hızlıdır.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF bit eşlem efektleri  
 Bit eşlem efektleri<xref:System.Windows.Media.Effects.BitmapEffect> (nesne) basit piksel işleme işlemleridir. Bit eşlem efekti bir <xref:System.Windows.Media.Imaging.BitmapSource> giriş olarak alır ve bir bulanıklaştırma ya da gölge gibi Efekti uyguladıktan sonra yeni <xref:System.Windows.Media.Imaging.BitmapSource> bir oluşturur. Her bit eşlem efekti, <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>gibi filtreleme özelliklerini denetleyebilen özellikleri sunar.  
  
 Özel bir durum olarak, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]efektler, <xref:System.Windows.Controls.Button> veya <xref:System.Windows.Controls.TextBox>gibi canlı <xref:System.Windows.Media.Visual> nesnelerde özellikler olarak ayarlanabilir. Piksel işleme, çalışma zamanında uygulanır ve işlenir. Bu durumda, oluşturma sırasında bir <xref:System.Windows.Media.Visual> otomatik olarak <xref:System.Windows.Media.Imaging.BitmapSource> eşdeğerine dönüştürülür ve öğesine <xref:System.Windows.Media.Effects.BitmapEffect>giriş olarak aktarılır. Çıktı, <xref:System.Windows.Media.Visual> nesnenin varsayılan işleme davranışının yerini alır. Bu, nesnelerin <xref:System.Windows.Media.Effects.BitmapEffect> görselleri yalnızca yazılımda işlemesini zorlamasına neden olur, ancak efektler uygulandığında görsellerde donanım ivmesi yoktur.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>odak dışı görünen bir nesnenin benzetimini yapar.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>bir nesnenin çevresi etrafında bir renk Halo oluşturur.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>bir nesnenin arkasında gölge oluşturur.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>bir görüntünün yüzeyini belirtilen eğriye göre Başlatan bir eğim oluşturur.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>yapay ışık kaynağından derinlik ve doku <xref:System.Windows.Media.Visual> izlenimi vermek için bir ' ın bir kabartma eşlemesi oluşturur.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bit eşlem efektleri yazılım modunda işlenir. Bir efekt uygulayan herhangi bir nesne yazılımda da işlenir. Büyük görseller üzerinde bit eşlem efektleri kullanırken veya bir bit eşlem efektinin özellikleri canlandırdığınızda, performans en çok düşer. Bu, bit eşlem efektlerini bu şekilde bu şekilde kullanmamalısınız, ancak kullanıcılarınızın bekledikleri deneyimi aldığından emin olmak için dikkatli ve test etmeniz gerekir.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bit eşlem efektleri kısmi güven yürütmeyi desteklemez. Bir uygulamanın bit eşlem efektlerini kullanmak için tam güven izinleri olmalıdır.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Efekt uygulama  
 <xref:System.Windows.Media.Effects.BitmapEffect>, üzerindeki <xref:System.Windows.Media.Visual>bir özelliktir. <xref:System.Windows.Controls.Button>Bu nedenle <xref:System.Windows.Controls.Image> ,<xref:System.Windows.Media.DrawingVisual>,, veya<xref:System.Windows.UIElement>gibi görsellere efekt uygulamak, bir özelliği ayarlamak kadar kolaydır. <xref:System.Windows.UIElement.BitmapEffect%2A><xref:System.Windows.Media.Effects.BitmapEffect> ,<xref:System.Windows.Media.Effects.BitmapEffectGroup> tek bir nesneye ayarlanabilir veya birden çok efekt nesnesi kullanılarak zincirleme yapılabilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Effects.BitmapEffect> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]nasıl uygulanacağını gösterir.  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Effects.BitmapEffect> kod içinde nasıl uygulanacağını gösterir.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Media.Effects.BitmapEffect> Veya<xref:System.Windows.Controls.Canvas>gibi bir düzen kapsayıcısına uygulandığında, efekt, onun tüm alt öğeleri dahil olmak üzere, öğe veya görselin görsel ağacına uygulanır.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Özel etkiler oluşturma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], yönetilen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarda kullanılabilecek özel etkiler oluşturmak için yönetilmeyen arabirimler de sağlar. Özel bit eşlem efektleri oluşturmaya yönelik ek başvuru malzemeleri için, [YÖNETILMEYEN WPF bit eşlem efekti](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Yönetilmeyen WPF bit eşlem efekti](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Güvenlik](../security-wpf.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
