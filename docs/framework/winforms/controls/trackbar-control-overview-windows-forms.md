---
title: "TrackBar Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccea982c45ab22a4b2ab81bc80c16dd472144bbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> denetimi (bazen "kaydırıcı" denetimi olarak da adlandırılır), büyük miktarda bilgi arasında gezinmek için veya bir sayısal ayarı görsel olarak ayarlamak için kullanılır. <xref:System.Windows.Forms.TrackBar> Denetim da iki bölümden oluşur: olarak da bilinen bir kaydırıcı ve çizgilerinin kalan kısmıdır. Kaydırma ayarlanabilir bir parçasıdır. Konumuna karşılık gelen <xref:System.Windows.Forms.TrackBar.Value%2A> özelliği. Değer çizgilerinin düzenli aralıklarla aralıklı visual göstergesidir. Trackbar belirtin ve yatay veya dikey hizalanabilir artışlarla taşır. Örneğin, bir sistem için imleç blink oranı ya da fare hızı denetlemek için izleme çubuğunu kullanabilirsiniz.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özelliklerini <xref:System.Windows.Forms.TrackBar> denetim <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, ve <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>ticks aralığını olur. <xref:System.Windows.Forms.TrackBar.Minimum%2A>ve <xref:System.Windows.Forms.TrackBar.Maximum%2A> izleme çubuğunda temsil edilebilir en küçük ve en büyük değerler.  
  
 İki önemli özellik <xref:System.Windows.Forms.TrackBar.SmallChange%2A> ve <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Değeri <xref:System.Windows.Forms.TrackBar.SmallChange%2A> özelliği, Flash taşır sol veya sağ ok tuşunu basılı sahip yanıt konumlar numarasıdır. Değeri <xref:System.Windows.Forms.TrackBar.LargeChange%2A> özelliği, Flash PAGE UP veya PAGE DOWN tuşunu basılı sahip yanıt taşıdığında veya fare yanıtta tıklattığında ya da yan tarafında kalan kısmıdır izleme çubuğunda konumlar numarasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar denetimi](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
