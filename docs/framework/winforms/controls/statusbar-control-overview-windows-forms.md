---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: c3e52a91a31eb898d0176bc35a97cda7de9a8368
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491356"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.  
  
 Windows Forms [StatusBar denetimine](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formlarında genellikle bir uygulama çeşitli durum bilgilerini görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır. <xref:System.Windows.Forms.StatusBar> denetimleri, metin veya durumu ya da bir işlemin çalıştığını gösteren simgeler animasyonda bir dizi belirtmek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] Belge kaydedildiğinde gösteren.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimi kullanma  
 Internet Explorer köprünün üzerine fare geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] sayfası konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme; ve Visual Studio kullanan gibi durum çubuğunun yerleştirilebilir pencerelerin işlemek nasıl belirten gibi bağlama duyarlı bilgileri vermek için düzenleme modunu bilgiler verir olarak yerleşik veya kayan.  
  
 Ayarlayarak durum çubuğuna tek bir ileti görüntüleyebilir <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğuna durum çubuğunda görüntülenmesini istediğiniz metin. Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
