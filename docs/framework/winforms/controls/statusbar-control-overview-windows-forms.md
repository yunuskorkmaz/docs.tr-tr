---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505431"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.  
  
 Windows Forms [StatusBar denetimine](statusbar-control-windows-forms.md) formlarında genellikle bir uygulama çeşitli durum bilgilerini görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır. <xref:System.Windows.Forms.StatusBar> denetimleri, metin veya durumu ya da bir işlemin çalıştığını gösteren simgeler animasyonda bir dizi belirtmek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, belgeyi Microsoft Word gösteren kaydediliyor.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimi kullanma  
 Internet Explorer köprünün üzerine fare geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word sayfası konumu, bölüm konumu ve üzerine yazma ve izleme düzeltme gibi modları düzenleme hakkında bilgi sağlar; ve Visual Studio yerleştirilebilir pencerelerin kayan ya da yerleşik olarak işlemek nasıl belirten gibi bağlama duyarlı bilgileri vermek için durum çubuğunu kullanır.  
  
 Ayarlayarak durum çubuğuna tek bir ileti görüntüleyebilir <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğuna durum çubuğunda görüntülenmesini istediğiniz metin. Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
