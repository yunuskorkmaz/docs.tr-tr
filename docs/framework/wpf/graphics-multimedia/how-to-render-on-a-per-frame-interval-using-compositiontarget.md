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
ms.openlocfilehash: 7c080c6deca63eacdf0e1123f4ca8bbb495ed9ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561666"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Nasıl yapılır: CompositionTarget Kullanarak Çerçeve Aralığı Başına İşleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animasyon altyapısı tabanlı çerçeve animasyon oluşturmak için birçok özellik sağlar. Ancak, uygulama senaryoları işleme çerçeve başına temelinde geçirmiş denetime ihtiyacınız vardır. <xref:System.Windows.Media.CompositionTarget> Nesne üzerinde bir çerçeve başına geri alarak özel animasyon oluşturma olanağı sağlar.  
  
 <xref:System.Windows.Media.CompositionTarget> Uygulamanızı çekilmeye çalışıldığı görüntü yüzeyini temsil eden bir statik bir sınıftır. <xref:System.Windows.Media.CompositionTarget.Rendering> Olayı uygulamanın görünümü çizildiği her zaman oluşturulur. İşleme kare hızı saniye başına Sahne çizilme sayısıdır.  
  
> [!NOTE]
>  Kullanarak eksiksiz kod örneği için <xref:System.Windows.Media.CompositionTarget>, bkz: [CompositionTarget örneği kullanarak](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Olay harekete sırasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturma işlemi. Aşağıdaki örnek, nasıl kaydedersiniz gösterir bir <xref:System.EventHandler> temsilci statik olarak <xref:System.Windows.Media.CompositionTarget.Rendering> yöntemi <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Özel çizim içeriği oluşturmak için işleme olay işleyicisi yöntemini kullanabilirsiniz. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında verilerini kalıcı işleme arasında görsel ağaç birleşim Sahne grafiği, olay işleyicisi yöntemi için çağrılır. Ayrıca, görsel ağaç değişiklikler birleşim Sahne grafiğe güncelleştirmeleri zorlarsanız, olay işleyicisi yöntemi da adlandırılır. Düzen hesaplandıktan sonra olay işleyicisi yöntemi çağrılır unutmayın. Ancak, bu yerleşim bir kez daha işlemeden önce hesaplanacağı anlamına gelir, olay işleyicisi yöntemi düzenini değiştirebilirsiniz.  
  
 Aşağıdaki örnekte nasıl sağlayabilirsiniz özel çizim gösterir bir <xref:System.Windows.Media.CompositionTarget> olay işleyicisi yöntemi. Bu durumda, arka plan rengini <xref:System.Windows.Controls.Canvas> fare koordinat konumuna bağlı bir renk değeri ile çizilir. Fareyi içinde taşırsanız <xref:System.Windows.Controls.Canvas>, kendi arka plan rengi değişir. Ayrıca, Ortalama kare hızı, geçerli geçen süre ve işlenmiş çerçeve toplam sayısını göre hesaplanır.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Özel çizim farklı bilgisayarlarda farklı hızlarda çalıştığını fark edebilirsiniz. Özel çizim kare hızı olmadığından budur bağımsız. Çalıştırdığınız sistem ve sistem, iş yüküne bağlı olarak <xref:System.Windows.Media.CompositionTarget.Rendering> olayı saniye başına farklı sayıda çağrıldı. Grafik donanım yeteneği ve çalışan bir aygıtın performans düzeyini belirleme hakkında daha fazla bilgi için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, bkz: [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Ekleyerek veya kaldırarak bir işleme <xref:System.EventHandler> olay tetikleme sırada temsilci ertelenmesini kadar olayı tamamlandıktan sonra geciktirilir. Bu nasıl ile tutarlıdır <xref:System.MulticastDelegate>-temelli olaylar Ortak dil çalışma zamanı (CLR) işlenir. Ayrıca işleme olaylarının belirli bir sırada çağrılacak garanti unutmayın. Birden çok varsa <xref:System.EventHandler> belirli bir sıraya üzerinde temsilciler tek bir kaydedeceğini <xref:System.Windows.Media.CompositionTarget.Rendering> olay ve çoğullamalısınız doğru temsilcileri kendiniz sipariş.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.CompositionTarget>  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
