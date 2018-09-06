---
title: 'Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 045a2f540a37cdea84d2bf2f3ed1e74e122bdbb5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746116"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme
Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> çizgilerinin olan denetim.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.TickBar> Ayarladığınızda görüntüler <xref:System.Windows.Controls.Slider.TickPlacement%2A> dışında bir değere <xref:System.Windows.Controls.Primitives.TickPlacement.None>, varsayılan değer olan.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> ile bir <xref:System.Windows.Controls.Primitives.TickBar> işaretleri görüntüler. <xref:System.Windows.Controls.Slider.TickPlacement%2A> Ve <xref:System.Windows.Controls.Slider.TickFrequency%2A> özelliklerini değer çizgilerinin ve aralarındaki aralığı konumunu tanımlayın. Taşıdığınızda <xref:System.Windows.Controls.Primitives.Thumb>, araç ipuçlarını görüntüleme değerini <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Özelliği, araç ipucunun nerede gerçekleştiği tanımlar. <xref:System.Windows.Controls.Primitives.Thumb> Hareketleri çünkü çizgilerinin konumuna karşılık gelen <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ayarlanır `true`.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Slider.Ticks%2A> boyunca değer çizgisi oluşturmak için özellik <xref:System.Windows.Controls.Slider> düzensiz aralıklarla.  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [Kaydırıcı ile ilgili nasıl yapılır konuları](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
