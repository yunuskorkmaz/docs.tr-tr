---
title: StatusBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742871"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.  
  
 Windows Forms [StatusBar denetimi](statusbar-control-windows-forms.md) , genellikle pencerenin altında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır. <xref:System.Windows.Forms.StatusBar> denetimleri, durumu göstermek için metin veya simgeleri görüntüleyen ve bir animasyonun çalıştığını gösteren bir animasyon içindeki bir simge dizisi olan durum çubuğu panellerine sahip olabilir; Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimini kullanma  
 Internet Explorer, fare köprünün üzerine geldiğinde bir sayfanın URL 'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word size sayfa konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme gibi düzenleme modları hakkında bilgi verir; Visual Studio, serbest yerleştirilmiş Windows 'u yerleştirilmiş veya kayan olarak nasıl işleyebileceğiniz hakkında içeriğe duyarlı bilgiler vermek için durum çubuğunu kullanır.  
  
 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) olarak ayarlayarak ve durum çubuğunun <xref:System.Windows.Forms.StatusBar.Text%2A> özelliğini durum çubuğunda görünmesini istediğiniz metin olarak ayarlayarak durum çubuğunda tek bir ileti görüntüleyebilirsiniz. <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` olarak ayarlayarak ve <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection><xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemini kullanarak birden fazla bilgi türü göstermek için durum çubuğunu panellere bölebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
