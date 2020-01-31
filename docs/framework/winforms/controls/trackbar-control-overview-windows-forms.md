---
title: TrackBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741458"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> denetimi (bazen "kaydırıcı" denetimi olarak da adlandırılır), büyük miktarda bilgi veya görsel olarak bir sayısal ayarı düzeltmek için kullanılır. <xref:System.Windows.Forms.TrackBar> denetimi iki bölümden oluşur: kaydırıcı olarak da bilinen Thumb ve değer çizgileri. Thumb, ayarlanabilecek bölümüdür. Konumu <xref:System.Windows.Forms.TrackBar.Value%2A> özelliğine karşılık gelir. Değer çizgileri, düzenli aralıklarla boşluklu görsel göstergeler. TrackBar, belirttiğiniz artışlarla ve yatay veya dikey olarak hizalanabilir. Örneğin, bir sistem için imleç yanıp sönme hızını veya fare hızını denetlemek için izleme çubuğunu kullanabilirsiniz.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 <xref:System.Windows.Forms.TrackBar> denetiminin temel özellikleri <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>ve <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, Tick 'lerin yer aldığı aralıkdır. <xref:System.Windows.Forms.TrackBar.Minimum%2A> ve <xref:System.Windows.Forms.TrackBar.Maximum%2A>, izleme çubuğunda gösterilebilen en küçük ve en büyük değerlerdir.  
  
 Diğer iki önemli özellik <xref:System.Windows.Forms.TrackBar.SmallChange%2A> ve <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. <xref:System.Windows.Forms.TrackBar.SmallChange%2A> özelliğinin değeri, sol veya sağ ok tuşuna basıldığında Thumb 'ın yanıt olarak hareket edeceği konumların sayısıdır. <xref:System.Windows.Forms.TrackBar.LargeChange%2A> özelliğinin değeri, SAYFANıN yukarı veya sayfa aşağı tuşuna basıldığında ya da Thumb 'in iki yanındaki izleme çubuğunda fare tıklamasına yanıt olarak hareket edeceği konumların sayısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar Denetimi](trackbar-control-windows-forms.md)
