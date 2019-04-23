---
title: 'Nasıl yapılır: CompositionTarget Kullanarak Çerçeve Aralığı Başına İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 00b416d423a4bdc8bab576add2d77fd305ea6e0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089425"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Nasıl yapılır: CompositionTarget Kullanarak Çerçeve Aralığı Başına İşleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animasyon altyapısı tabanlı çerçeve animasyon oluşturmak için birçok özellik sağlar. Ancak, uygulama senaryoları daha ayrıntılı işleme çerçeve başına temelinde denetime ihtiyacınız vardır. <xref:System.Windows.Media.CompositionTarget> Nesne üzerinde bir çerçeve başına geri alarak özel animasyon oluşturma olanağı sağlar.  
  
 <xref:System.Windows.Media.CompositionTarget> Uygulamanız üzerinde çizilen uzaklaştırabilir temsil eden statik bir sınıftır. <xref:System.Windows.Media.CompositionTarget.Rendering> Olayı her zaman uygulamanın Sahne çizilir. İşleme kare hızı, saniye başına Sahne çizilme sayısıdır.  
  
> [!NOTE]
>  İçin tam kod örneğini kullanarak <xref:System.Windows.Media.CompositionTarget>, bkz: [CompositionTarget örneğini kullanarak](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Olayı tetikler sırasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme. Aşağıdaki örnek, kayıt nasıl gösterir. bir <xref:System.EventHandler> temsilci statik olarak <xref:System.Windows.Media.CompositionTarget.Rendering> metodunda <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 İşleme olay işleyicisi yönteminiz özel çizim içerik oluşturmak için kullanabilirsiniz. Bu olay işleyicisi yöntemi, çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında kalıcı işleme verileri arasında görsel ağaç oluşturma Sahne grafiği, olay işleyicisi yönteminiz için çağrılır. Değişiklikleri görsel ağacı oluşturma Sahne grafiğe güncelleştirmeleri zorlarsanız, ayrıca, olay işleyicisi yönteminiz olarak da anılır. Düzen hesaplandıktan sonra olay işleyicisi yönteminin çağrıldığını unutmayın. Ancak, bu düzen bir kez daha önce işleme hesaplanacağı anlamına gelir, olay işleyicisi yönteminiz düzenini değiştirebilirsiniz.  
  
 Aşağıdaki örnek nasıl sağlayabilirsiniz özel çizim gösterir bir <xref:System.Windows.Media.CompositionTarget> olay işleyicisi yöntemi. Bu durumda, arka plan rengini <xref:System.Windows.Controls.Canvas> fare koordinat konumuna göre bir renk değeri ile çizilir. İçinde fareyi hareket <xref:System.Windows.Controls.Canvas>, kendi arka plan rengi değişir. Ayrıca, geçerli geçen süresini ve işlenmiş çerçeve sayısı göre ortalama kare hızı hesaplanır.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Özel çiziminize farklı hızlarda farklı bilgisayarlarda çalışan keşfedebilir. Kare hızı, özel çizim değil olmasıdır bağımsız. Çalıştırdığınız sistemin ve sistem, iş yüküne bağlı olarak <xref:System.Windows.Media.CompositionTarget.Rendering> olay saniye başına farklı sayıda çağrılır. Çalıştıran bir cihaz için performans ve grafik donanım özelliği belirleme hakkında bilgi için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması, bakın [grafik işleme katmanları](../advanced/graphics-rendering-tiers.md).  
  
 Ekleyerek veya kaldırarak bir işleme <xref:System.EventHandler> olayı tetiklenmekte olan sırada temsilci ertelenmesini kadar olay bittikten sonra geciktirilir. Bu nasıl ile tutarlıdır <xref:System.MulticastDelegate>-dayalı olayları, ortak dil çalışma zamanı (CLR) işlenir. Ayrıca, işleme olaylarının herhangi belirli bir sırada çağrılacak garanti edilmez unutmayın. Birden fazla varsa <xref:System.EventHandler> belirli bir sıraya üzerinde temsilciler tek bir kayıt işlemi <xref:System.Windows.Media.CompositionTarget.Rendering> olay ve çoğullamalısınız doğru temsilciler kendiniz düzenleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.CompositionTarget>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
