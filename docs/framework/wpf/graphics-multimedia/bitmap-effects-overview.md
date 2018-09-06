---
title: Bit Eşlem Efektlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 97b878621d5aa1860cd955755d9bbc344b95b993
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724249"
---
# <a name="bitmap-effects-overview"></a>Bit Eşlem Efektlerine Genel Bakış
Bit eşlem efektleri tasarımcılara ve Windows Presentation Foundation (WPF) içerik görsel efektler uygulamak için geliştirici çizilir. Örneğin, bit eşlem efektleri kolayca uygulamanıza izin bir <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> veya Bulanıklaştırma efektini görüntü ya da bir düğme.  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ya da sonraki <xref:System.Windows.Media.Effects.BitmapEffect> sınıf artık kullanılmıyor. Kullanmayı denerseniz <xref:System.Windows.Media.Effects.BitmapEffect> sınıfı, geçersiz bir özel durum alırsınız. Gereksiz olmayan alternatif <xref:System.Windows.Media.Effects.BitmapEffect> sınıfı <xref:System.Windows.Media.Effects.Effect> sınıfı. Çoğu durumda <xref:System.Windows.Media.Effects.Effect> sınıfı, önemli ölçüde daha hızlıdır.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF Bit eşlem efektleri  
 Bit eşlem etkileri (<xref:System.Windows.Media.Effects.BitmapEffect> nesne) basit piksel işleme işlemlerdir. Bir bit eşlem etkisi alır bir <xref:System.Windows.Media.Imaging.BitmapSource> oluşturan yeni bir giriş olarak <xref:System.Windows.Media.Imaging.BitmapSource> gibi bulanıklaştırma veya bir gölge efektini uyguladıktan sonra. Her bit eşlem etkisi filtreleme özelliklerini gibi denetleyen özellikler sunan <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> , <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Bir özel durum olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], efektler ayarlanabilir özellikleri olarak canlı <xref:System.Windows.Media.Visual> gibi nesneleri bir <xref:System.Windows.Controls.Button> veya <xref:System.Windows.Controls.TextBox>. Piksel işleme uygulanan ve çalışma zamanında çizilir. Bu durumda, işleme, anında bir <xref:System.Windows.Media.Visual> otomatik olarak dönüştürülür, <xref:System.Windows.Media.Imaging.BitmapSource> eşdeğer ve giriş olarak beslenir <xref:System.Windows.Media.Effects.BitmapEffect>. Çıkış değiştirir <xref:System.Windows.Media.Visual> nesnenin varsayılan işleme davranışına. Bu nedenle, <xref:System.Windows.Media.Effects.BitmapEffect> nesneleri görsel efektler uygulandığında yazılımda yalnızca başka bir deyişle hiçbir donanım hızlandırma görsellerindeki işlemek için zorla.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> Odak çıkış görünen bir nesnenin benzetimini yapar.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> Renkli bir nesnenin çevresindeki oluşturur.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> nesnenin arkasında bir gölge oluşturur.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> görüntüyü belirtilen eğri göre yüzeyine oluşturan eğimi oluşturur.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> çarpma eşlemesi oluşturur bir <xref:System.Windows.Media.Visual> doku ve derinlik izlenimi yapay bir ışık kaynağından vermek için.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bit eşlem efektleri yazılım modunda işlenir. Efekt uygulanan herhangi bir nesne de yazılımda işlenir. Performansı en iyi, bit eşlem kullanarak büyük görselleri ya da bir bit eşlem etkisi hareketlendirme özelliklerini etkiler düşer. Bu, bit eşlem efektleri hiç bu şekilde kullanmamanız gerekir, ancak dikkatli ve kullanıcılarınızın deneyimini beklediğiniz aldıklarından emin olmak için baştan sona test varsayalım değil içindir.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bit eşlem efektleri kısmi güven yürütme desteklemez. Bir uygulama, bit eşlem efektleri kullanmak için tam güven izinleri olmalıdır.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Efekt uygulama  
 <xref:System.Windows.Media.Effects.BitmapEffect> üzerinde bir özelliği olan <xref:System.Windows.Media.Visual>. Bu nedenle efektleri gibi Görsellere, uygulama bir <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, veya <xref:System.Windows.UIElement>, bir özelliği ayarlamak oldukça kolaydır. <xref:System.Windows.UIElement.BitmapEffect%2A> tek bir ayarlanabilir <xref:System.Windows.Media.Effects.BitmapEffect> nesnesi veya birden fazla efekt zincirleme yapılabilir kullanarak <xref:System.Windows.Media.Effects.BitmapEffectGroup> nesne.  
  
 Aşağıdaki örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.Effects.BitmapEffect> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Aşağıdaki örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.Effects.BitmapEffect> kod.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Olduğunda bir <xref:System.Windows.Media.Effects.BitmapEffect> gibi bir düzen kapsayıcısı için uygulanan <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.Canvas>, öğenin veya visual tüm alt öğeleri dahil olmak üzere, görsel ağaçta değişiklik etkisi uygulanır.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Özel efekt oluşturma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullanılabilir özel efekt oluşturma yönetilmeyen arabirimler de sağlar yönetilen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. Özel bit eşlem efektleri oluşturmak için referans materyalleri için bkz: [Yönetilmeyen WPF Bit eşlem etkisi](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [WPF yönetilmeyen bit eşlem etkisi](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
 [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
