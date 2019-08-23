---
title: ToolBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: c7c19783963bb315a0356979797c6f4d4e3b9e08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929589"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip>  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> denetimi, açılan menülerin ve komutları etkinleştirmek için bit eşlenmiş düğmelerin bir satırını görüntüleyen bir denetim çubuğu olarak formlarda kullanılır. Bu nedenle, bir araç çubuğu düğmesine tıklamak bir menü komutu seçmeye eşdeğer olabilir. Düğmeler görüntülenecek ve pushbutton, açılan menüler veya ayırıcılar olarak davranacak şekilde yapılandırılabilir. Genellikle bir araç çubuğu, uygulamanın menü yapısındaki öğelere karşılık gelen düğme ve menüleri içerir ve uygulamanın en sık kullanılan işlevlerine ve komutlarına hızlı erişim sağlar.  
  
## <a name="working-with-the-toolbar-control"></a>Araç çubuğu denetimiyle çalışma  
 Bir <xref:System.Windows.Forms.ToolBar> denetim genellikle üst penceresinin üst kısmında "yerleştirildi", ancak pencerenin herhangi bir tarafına da yerleştirilmiş olabilir. Bir araç çubuğu, Kullanıcı fare işaretçisini bir araç çubuğu düğmesinde işaret ediyorsa araç ipuçlarını gösterebilir. Araç Ipucu, düğmeyi veya menünün amacını kısaca açıklayan küçük bir açılır pencere penceresidir. Araç ipuçlarını <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> göstermek için özelliği olarak `true`ayarlanmalıdır.  
  
> [!NOTE]
> Belirli uygulamalar Özellik denetimleri, uygulama penceresinin üzerinde "float" özelliğine sahip ve yeniden konumlandırılabilir olan araç çubuğuna çok benzer. Windows Forms ToolBar denetimi bu eylemleri yapamaz.  
  
 <xref:System.Windows.Forms.ToolBar.Appearance%2A> Özelliği olarak<xref:System.Windows.Forms.ToolBarAppearance>ayarlandığında, araç çubuğu düğmeleri kabarık ve üç boyutlu görünür. Araç çubuğuna ve düğmelerine <xref:System.Windows.Forms.ToolBar.Appearance%2A> düz bir görünüm vermek için <xref:System.Windows.Forms.ToolBarAppearance> araç çubuğunun özelliğini olarak ayarlayabilirsiniz. Fare işaretçisi düz bir düğmenin üzerine geldiğinde, düğme görünümü üç boyutlu olarak değişir. Araç çubuğu düğmeleri ayırıcılar kullanılarak mantıksal gruplara ayrılabilir. Ayırıcı <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği olarak <xref:System.Windows.Forms.ToolBarButtonStyle>ayarlanmış bir araç çubuğu düğmesidir. Araç çubuğunda boş alan olarak görünür. Araç çubuğunun düz bir görünümü olduğunda, düğme ayırıcıları düğmeler arasındaki boşluklar yerine satırlar halinde görünür.  
  
 Denetim <xref:System.Windows.Forms.ToolBar> , <xref:System.Windows.Forms.Button> bir<xref:System.Windows.Forms.ToolBar.Buttons%2A> koleksiyona nesneler ekleyerek araç çubukları oluşturmanıza olanak sağlar. Bir <xref:System.Windows.Forms.ToolBar> denetime düğme eklemek için koleksiyon düzenleyicisini kullanabilirsiniz; her ikisini de atayabilseniz <xref:System.Windows.Forms.Button> de, her nesne metin veya atanmış bir görüntüye sahip olmalıdır. Görüntü, ilişkili bir [ImageList](imagelist-component-windows-forms.md) bileşeni tarafından sağlanır. Çalışma zamanında, <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> ve <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> yöntemlerini kullanarak düğme ekleyebilir veya kaldırabilirsiniz. İçindeki düğmeleri <xref:System.Windows.Forms.ToolBar>programlamak için, hangi düğmenin tıklandığını anlamak üzere <xref:System.Windows.Forms.ToolBar.ButtonClick> <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sınıfının <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliğini kullanarak <xref:System.Windows.Forms.ToolBar>olayına kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [Nasıl yapılır: Araç çubuğu denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: Bir araç çubuğu düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları](how-to-trigger-menu-events-for-toolbar-buttons.md)
