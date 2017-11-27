---
title: "Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d266d85e10ca8e77cd32338096cf3a3b761c188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme
Bu örnek nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Slider> çizgilerinin sahip denetimini.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.TickBar> Ayarladığınızda görüntüler <xref:System.Windows.Controls.Slider.TickPlacement%2A> dışında bir değere özelliğine <xref:System.Windows.Controls.Primitives.TickPlacement.None>, varsayılan değer olan.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Slider> ile bir <xref:System.Windows.Controls.Primitives.TickBar> işaretleri görüntüler. <xref:System.Windows.Controls.Slider.TickPlacement%2A> Ve <xref:System.Windows.Controls.Slider.TickFrequency%2A> özellikleri değer çizgilerinin ve aralarındaki aralığı konumunu tanımlayın. Taşıdığınızda <xref:System.Windows.Controls.Primitives.Thumb>, araç ipuçlarını görüntüleme değeri <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Araç ipuçları gerçekleştiği özelliği tanımlar. <xref:System.Windows.Controls.Primitives.Thumb> Hareketleri karşılık gelen değer çizgilerinin konuma çünkü <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ayarlanır `true`.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Slider.Ticks%2A> onay işaretleri boyunca oluşturmak için özelliğini <xref:System.Windows.Controls.Slider> düzensiz aralıklarla.  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [Kaydırıcı Nasıl Yapılır Konuları](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
