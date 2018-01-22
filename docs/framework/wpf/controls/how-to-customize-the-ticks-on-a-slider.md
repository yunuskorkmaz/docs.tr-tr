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
ms.workload: dotnet
ms.openlocfilehash: d21d2950ed228bf588a202419c222ee86dde5b0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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
 [Kaydırıcı Nasıl Yapılır Konuları](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
