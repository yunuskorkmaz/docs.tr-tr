---
title: TrackBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 1606db73485944f3dfa8b9c084bffda817520c7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200642"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> denetimi (bazen "kaydırıcı" denetimi olarak da adlandırılır), büyük miktarda bilgiyi arasında gezinmek için veya bir sayısal ayar görsel olarak ayarlamak için kullanılır. <xref:System.Windows.Forms.TrackBar> Denetime sahip olmak üzere iki parçadan: parmak olarak da bilinen bir kaydırıcı ve değer çizgileri. Thumb ayarlanabilir bir parçasıdır. Konumuna karşılık gelen <xref:System.Windows.Forms.TrackBar.Value%2A> özelliği. Değer çizgilerinin düzenli aralıklarla aralıklı görsel göstergeleri ' dir. Trackbar belirtin ve yatay veya dikey yönde hizalanabilir artışlarla taşır. Örneğin, bir sistem için imleç yanıp sönme hızı veya fare hızı denetlemek için izleme çubuğu kullanabilirsiniz.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özelliklerini <xref:System.Windows.Forms.TrackBar> denetimi <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, ve <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> saat döngüsü aralığı olur. <xref:System.Windows.Forms.TrackBar.Minimum%2A> ve <xref:System.Windows.Forms.TrackBar.Maximum%2A> izleme çubuğunda temsil edilebilir en küçük ve büyük değerler.  
  
 İki önemli özellikleri <xref:System.Windows.Forms.TrackBar.SmallChange%2A> ve <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Değerini <xref:System.Windows.Forms.TrackBar.SmallChange%2A> konum thumb taşır sol veya sağ ok tuşunu basılı olan yanıt sayısı bir özelliktir. Değerini <xref:System.Windows.Forms.TrackBar.LargeChange%2A> thumb için PAGE UP veya PAGE DOWN tuşunu basılı olan yanıt taşır veya fare yanıtta tıkladığında izleme çubuğunda her iki tarafında kalan kısmıdır, konum sayısına bir özelliktir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar Denetimi](trackbar-control-windows-forms.md)
