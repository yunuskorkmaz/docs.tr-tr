---
title: Bit Eşlem Efektlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187002"
---
# <a name="bitmap-effects-overview"></a>Bit Eşlem Efektlerine Genel Bakış
Bitmap efektleri, tasarımcıların ve geliştiricilerin işlenen Windows Presentation Foundation (WPF) içeriğine görsel efektler uygulamalarını sağlar. Örneğin, bitmap efektleri görüntüye veya <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> düğmeye kolayca efekt veya bulanıklık efekti uygulamanızı sağlar.  
  
> [!IMPORTANT]
> .NET Framework 4 veya sonraki <xref:System.Windows.Media.Effects.BitmapEffect> durumlarda sınıf geçersizdir. <xref:System.Windows.Media.Effects.BitmapEffect> Sınıfı kullanmaya çalışırsanız, eski bir özel durum alırsınız. <xref:System.Windows.Media.Effects.BitmapEffect> Sınıfın eski olmayan alternatifi <xref:System.Windows.Media.Effects.Effect> sınıftır. Çoğu durumda, <xref:System.Windows.Media.Effects.Effect> sınıf önemli ölçüde daha hızlıdır.  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>WPF Bitmap Efektleri  
 Bitmap efektleri<xref:System.Windows.Media.Effects.BitmapEffect> (nesne) basit piksel işleme işlemleridir. Bitmap efekti <xref:System.Windows.Media.Imaging.BitmapSource> bir giriş olarak alır <xref:System.Windows.Media.Imaging.BitmapSource> ve efekti uyguladıktan sonra bulanıklık veya bırakma gölgesi gibi yeni bir giriş üretir. Her biteşme efekti, <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>'nin .  
  
 Özel bir durum [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]olarak, etkileri gibi canlı <xref:System.Windows.Media.Visual> nesneler üzerinde özellikleri olarak <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>ayarlanabilir veya . Piksel işleme uygulanır ve çalışma zamanında işlenir. Bu durumda, işleme sırasında, a <xref:System.Windows.Media.Visual> otomatik olarak eşdeğerine <xref:System.Windows.Media.Imaging.BitmapSource> dönüştürülür ve . <xref:System.Windows.Media.Effects.BitmapEffect> Çıktı, nesnenin <xref:System.Windows.Media.Visual> varsayılan oluşturma davranışının yerini alır. Bu nedenle <xref:System.Windows.Media.Effects.BitmapEffect> nesneler görselleri yazılımda işlemeye zorlar, yani efektler uygulandığında görseller üzerinde donanım ivmesi yoktur.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>odak dışında görünen bir nesneyi simüle eder.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>bir nesnenin çevresi etrafında bir renk halesi oluşturur.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>nesnenin arkasında gölge oluşturur.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>belirli bir eğriye göre görüntünün yüzeyini yükselten bir eğimli oluşturur.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>yapay bir ışık kaynağından derinlik ve doku izlenimi vermek için a <xref:System.Windows.Media.Visual> bir kabartma haritalama oluşturur.  
  
> [!NOTE]
> WPF bitmap efektleri yazılım modunda işlenir. Efekt uygulayan herhangi bir nesne de yazılımda işlenir. Büyük görseller üzerinde Bitmap efektleri veya Bitmap efektinin anaimating özellikleri kullanılarak performans en çok düşürülür. Bu, Bitmap efektlerini bu şekilde kullanmamanız gerektiği şeklinde değildir, ancak kullanıcılarınızın beklediğiniz deneyimi elde ettiğinden emin olmak için dikkatli olmalı ve iyice test emelisiniz.  
  
> [!NOTE]
> WPF bitmap efektleri kısmi güven yürütmeyi desteklemez. Bir uygulama bitmap efektleri kullanmak için tam güven izinleri olmalıdır.  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>Efekt Nasıl Uygulanır?  
 <xref:System.Windows.Media.Effects.BitmapEffect>üzerinde <xref:System.Windows.Media.Visual>bir özelliktir. Bu nedenle <xref:System.Windows.Controls.Button>Görsellere , , <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.DrawingVisual>, veya <xref:System.Windows.UIElement>, gibi efektler uygulamak, bir özelliği ayarlamak kadar kolaydır. <xref:System.Windows.UIElement.BitmapEffect%2A>tek <xref:System.Windows.Media.Effects.BitmapEffect> bir nesneye ayarlanabilir veya <xref:System.Windows.Media.Effects.BitmapEffectGroup> birden çok efekt nesne kullanılarak zincirlenebilir.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Effects.BitmapEffect> 'in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]nasıl uygulanacağı göster  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Effects.BitmapEffect> kodun nasıl uygulanacağı gösteriş gösterir.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Bir <xref:System.Windows.Media.Effects.BitmapEffect> düzen kapsayıcısına uygulandığında, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Canvas>efekt tüm alt öğeleri de dahil olmak üzere öğenin veya görselin görsel ağacına uygulanır.  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>Özel Efektler Oluşturma  
 WPF ayrıca yönetilen WPF uygulamalarında kullanılabilecek özel efektler oluşturmak için yönetilmeyen arabirimler de sağlar. Özel bitmap efektleri oluşturmak için ek başvuru malzemesi için [yönetilmeyen WPF Bitmap Efekti](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Yönetilmeyen WPF Bitmap Etkisi](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Güvenlik](../security-wpf.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
