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
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956978"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Nasıl yapılır: CompositionTarget Kullanarak Çerçeve Aralığı Başına İşleme
Animasyon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] altyapısı, çerçeve tabanlı animasyon oluşturmak için birçok özellik sağlar. Ancak, çerçeve başına işleme üzerinde daha ayrıntılı denetime ihtiyacınız olan uygulama senaryoları vardır. <xref:System.Windows.Media.CompositionTarget> Nesnesi, çerçeve başına geri çağırma temelinde özel animasyonlar oluşturma olanağı sağlar.  
  
 <xref:System.Windows.Media.CompositionTarget>, uygulamanızın çizildiği görüntü yüzeyini temsil eden bir statik sınıftır. <xref:System.Windows.Media.CompositionTarget.Rendering> Olay, uygulamanın sahneyi her çizililişinde tetiklenir. İşleme çerçeve oranı, sahnenin saniye başına çizilme sayısıdır.  
  
> [!NOTE]
> Kullanarak <xref:System.Windows.Media.CompositionTarget>tüm kod örnekleri için bkz. [kompozisyon, Oluşturucu örneğini kullanma](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Örnek  
 Olay, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme işlemi sırasında ateşlenir. <xref:System.Windows.Media.CompositionTarget.Rendering> Aşağıdaki örnek, üzerinde <xref:System.EventHandler> <xref:System.Windows.Media.CompositionTarget.Rendering> <xref:System.Windows.Media.CompositionTarget>statik metoda bir temsilciyi nasıl kaydedeceğinizi gösterir.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 İşleme olay işleyicisi yönteminizi özel çizim içeriği oluşturmak için kullanabilirsiniz. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağırılır. Görsel ağaç içindeki kalıcı işleme verilerini kompozisyon sahne grafiğine göre her sıraladığındaolayişleyicisiyönteminizçağırılır.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, görsel ağaçtaki değişiklikler kompozisyon sahneyi grafiğinde güncelleştirmelere zorlmaya zorlandıysanız olay işleyicisi yönteminiz de çağırılır. Olay işleyicisi yönteminizin düzen hesaplandıktan sonra çağrıldığını unutmayın. Bununla birlikte, olay işleyicisi yönteminizin düzeninde değişiklik yapabilirsiniz. Bu, düzenin işlemeden önce daha fazla hesaplanacaktır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.CompositionTarget> olay işleyicisi yönteminde nasıl özel çizim sağlayakullanabileceğinizi gösterir. Bu durumda, öğesinin <xref:System.Windows.Controls.Canvas> arka plan rengi, farenin koordinat konumuna göre bir renk değeri ile çizilir. Fareyi içinde <xref:System.Windows.Controls.Canvas>taşırsanız, arka plan rengi değişir. Ayrıca, ortalama kare hızı geçerli geçen süreye ve işlenen çerçevelerin toplam sayısına göre hesaplanır.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Özel çiziminizin farklı bilgisayarlarda farklı hızlarda çalıştığını fark edebilirsiniz. Bunun nedeni, özel çiziminizde kare hızına bağımsız değildir. Çalıştırdığınız sisteme ve bu sistemin iş yüküne bağlı olarak, <xref:System.Windows.Media.CompositionTarget.Rendering> olay saniyede farklı sayıda kez çağrılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulama çalıştıran bir cihazın grafik donanım özelliğini ve performansını belirleme hakkında bilgi için bkz. [grafik işleme katmanları](../advanced/graphics-rendering-tiers.md).  
  
 Olay başlatıldıktan sonra bir işleme <xref:System.EventHandler> temsilcisini ekleme veya kaldırma, olayın başlatılması bitinceye kadar gecikecek. Bu, ortak dil çalışma <xref:System.MulticastDelegate>zamanında (CLR), tabanlı olayların işlenme ile tutarlıdır. Ayrıca, işleme olaylarının belirli bir sırada çağrılması garanti edilmez. Belirli bir siparişi kullanan <xref:System.EventHandler> birden fazla temsilcileriniz varsa, tek <xref:System.Windows.Media.CompositionTarget.Rendering> bir olayı kaydetmeniz ve temsilcileri doğru sırada kendiniz de çoğullamalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.CompositionTarget>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
