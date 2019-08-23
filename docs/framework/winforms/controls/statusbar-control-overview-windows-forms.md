---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964429"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.  
  
 Windows Forms [StatusBar denetimi](statusbar-control-windows-forms.md) , genellikle pencerenin altında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır. <xref:System.Windows.Forms.StatusBar>denetimlerin, durumu göstermek için metin veya simgeleri görüntüleyen ve bir animasyonun çalıştığını gösteren bir animasyon içindeki simge dizisi olan durum çubuğu panellerine sahip olabilir; Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimini kullanma  
 Internet Explorer, fare köprünün üzerine geldiğinde bir sayfanın URL 'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word size sayfa konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme gibi düzenleme modları hakkında bilgi verir; Visual Studio, serbest yerleştirilmiş Windows 'u yerleştirilmiş veya kayan olarak nasıl işleyebileceğiniz hakkında içeriğe duyarlı bilgiler vermek için durum çubuğunu kullanır.  
  
 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Özelliği `false` (<xref:System.Windows.Forms.StatusBar.Text%2A> varsayılan) olarak ayarlayarak durum çubuğunda tek bir ileti görüntüleyebilir ve durum çubuğunun özelliğini durum çubuğunda görünmesini istediğiniz metin olarak ayarlayabilirsiniz. <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Özelliğini olarak `true` ayarlayarak vemetodunu<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> kullanarak, birden fazla bilgi türü göstermek için durum çubuğunu panellere bölebilirsiniz. <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
