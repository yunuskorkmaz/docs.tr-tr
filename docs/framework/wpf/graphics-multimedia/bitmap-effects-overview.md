---
title: Bit Eşlem Efektlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 7a93c5e247af7c9a54799721553ba486164a12e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bitmap-effects-overview"></a>Bit Eşlem Efektlerine Genel Bakış
Bit eşlem efektleri tasarımcıları etkinleştirin ve görsel efektler uygulamak için geliştiricilere Windows Presentation Foundation (WPF) içerik çizilir. Örneğin, bit eşlem efektleri kolayca uygulamanıza izin bir <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekti veya Bulanıklaştırma etkili bir görüntü veya bir düğme.  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] veya sonraki sürümlerde, <xref:System.Windows.Media.Effects.BitmapEffect> sınıf artık kullanılmıyor. Kullanmayı denerseniz <xref:System.Windows.Media.Effects.BitmapEffect> sınıfı, geçersiz bir özel durum alırsınız. Gereksiz olmayan alternatif <xref:System.Windows.Media.Effects.BitmapEffect> sınıfı <xref:System.Windows.Media.Effects.Effect> sınıfı. Çoğu durumda, <xref:System.Windows.Media.Effects.Effect> sınıftır önemli ölçüde daha hızlıdır.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF Bit eşlem etkileri  
 Efektler bit eşlem (<xref:System.Windows.Media.Effects.BitmapEffect> nesnesi) basit piksel işleme işlemleridir. Bir bit eşlem etkinleşir bir <xref:System.Windows.Media.Imaging.BitmapSource> yeni bir oluşturur ve bir girdi olarak <xref:System.Windows.Media.Imaging.BitmapSource> bulandırma veya gölge gibi etkisi uyguladıktan sonra. Her bit eşlem efekti filtreleme özelliklerini gibi denetleyebilirsiniz özellikleri sunar <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> , <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Bir özel durum olarak içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], efektler özellikleri olarak üzerinde ayarlanabilir canlı <xref:System.Windows.Media.Visual> gibi nesneleri bir <xref:System.Windows.Controls.Button> veya <xref:System.Windows.Controls.TextBox>. Piksel işleme uygulanan ve çalışma zamanında çizilir. Bu durumda, işleme, zamanında bir <xref:System.Windows.Media.Visual> otomatik olarak dönüştürülür kendi <xref:System.Windows.Media.Imaging.BitmapSource> eşdeğer ve giriş olarak Sat <xref:System.Windows.Media.Effects.BitmapEffect>. Çıktı değiştirir <xref:System.Windows.Media.Visual> nesnesinin varsayılan işleme davranışı. Nedeni budur <xref:System.Windows.Media.Effects.BitmapEffect> nesneleri görsel efektler uygulandığında hiçbir donanım hızlandırmasını görselleri yalnızca yazılımda işlemek için zorla.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> Odağı görünen bir nesnenin benzetimini yapar.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> bir nesnenin çevresinde renkli ışık oluşturur.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bir nesnenin arkasında gölge oluşturur.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> Belirtilen eğri göre bir görüntü yüzeyinin başlatır eğimi oluşturur.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> ın çarpma eşlemesini oluşturur bir <xref:System.Windows.Media.Visual> Yapay ışık kaynağından doku ve derinlik izlenim vermek için.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bit eşlem efektleri yazılım modunda işlenir. Efekt uygulayan herhangi bir nesne de yazılımda işlenir. En çok ne zaman bit eşlem kullanarak büyük görselleri veya bir bit eşlem efekti özelliklerini canlandırdığınızda etkiler performans düşer. Bu şekilde hiç bit eşlem efektleri kullanmamalıdır, ancak dikkatli ve kullanıcılarınızın beklediğiniz deneyimi aldıklarından emin olmak için baştan sona test tümden kullanmamanız budur.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bit eşlem efektleri kısmi güven yürütme desteklemez. Bir uygulama bit eşlem efektlerini kullanmak için tam güven izinleri olmalıdır.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Bir efekt nasıl uygulanır  
 <xref:System.Windows.Media.Effects.BitmapEffect> bir özelliği açıktır <xref:System.Windows.Media.Visual>. Bu nedenle efektleri, Görsellere gibi uygulama bir <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, veya <xref:System.Windows.UIElement>, bir özellik ayarlama olarak kadar kolaydır. <xref:System.Windows.UIElement.BitmapEffect%2A> tek bir ayarlanabilir <xref:System.Windows.Media.Effects.BitmapEffect> nesne veya birden çok etkileri zincirleme yapılabilir kullanarak <xref:System.Windows.Media.Effects.BitmapEffectGroup> nesnesi.  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.Effects.BitmapEffect> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.Effects.BitmapEffect> kod.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Zaman bir <xref:System.Windows.Media.Effects.BitmapEffect> bir düzen kapsayıcısına gibi uygulanan <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.Canvas>, öğenin veya tüm alt öğeleri de dahil olmak üzere visual görsel ağacına etkisi uygulanır.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Özel efektler oluşturma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullanılabilir özel efektler oluşturmak için yönetilmeyen arabirimleri de sağlar yönetilen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. Özel bit eşlem efektleri oluşturmada ek başvuru bilgileri için bkz: [Yönetilmeyen WPF Bit eşlem efekti](https://msdn.microsoft.com/library/ms735092.aspx) belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Yönetilmeyen WPF Bit eşlem efekti](https://msdn.microsoft.com/library/ms735092.aspx)  
 [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
