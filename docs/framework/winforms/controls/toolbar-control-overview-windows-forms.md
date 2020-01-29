---
title: ToolBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735489"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> denetimi yerini alır ve <xref:System.Windows.Forms.ToolBar> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.ToolBar> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> denetimi, açılan menülerin ve komutları aktive eden bit eşlenmiş düğmelerin bir satırını görüntüleyen bir denetim çubuğu olarak formlarda kullanılır. Bu nedenle, bir araç çubuğu düğmesine tıklamak bir menü komutu seçmeye eşdeğer olabilir. Düğmeler görüntülenecek ve pushbutton, açılan menüler veya ayırıcılar olarak davranacak şekilde yapılandırılabilir. Genellikle bir araç çubuğu, uygulamanın menü yapısındaki öğelere karşılık gelen düğme ve menüleri içerir ve uygulamanın en sık kullanılan işlevlerine ve komutlarına hızlı erişim sağlar.  
  
## <a name="working-with-the-toolbar-control"></a>Araç çubuğu denetimiyle çalışma  
 Bir <xref:System.Windows.Forms.ToolBar> denetimi genellikle üst penceresinin üst tarafında "yerleştirildi" ve ayrıca pencerenin herhangi bir tarafına yerleştirilmiş olabilir. Bir araç çubuğu, Kullanıcı fare işaretçisini bir araç çubuğu düğmesinde işaret ediyorsa araç ipuçlarını gösterebilir. Araç Ipucu, düğmeyi veya menünün amacını kısaca açıklayan küçük bir açılır pencere penceresidir. Araç Ipuçlarını göstermek için <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> özelliğinin `true`olarak ayarlanması gerekir.  
  
> [!NOTE]
> Belirli uygulamalar Özellik denetimleri, uygulama penceresinin üzerinde "float" özelliğine sahip ve yeniden konumlandırılabilir olan araç çubuğuna çok benzer. Windows Forms ToolBar denetimi bu eylemleri yapamaz.  
  
 <xref:System.Windows.Forms.ToolBar.Appearance%2A> özelliği <xref:System.Windows.Forms.ToolBarAppearance>olarak ayarlandığında, araç çubuğu düğmeleri kabarık ve üç boyutlu görünür. Araç çubuğuna ve düğmelerine düz bir görünüm vermek için araç çubuğunun <xref:System.Windows.Forms.ToolBar.Appearance%2A> özelliğini <xref:System.Windows.Forms.ToolBarAppearance> olarak ayarlayabilirsiniz. Fare işaretçisi düz bir düğmenin üzerine geldiğinde, düğme görünümü üç boyutlu olarak değişir. Araç çubuğu düğmeleri ayırıcılar kullanılarak mantıksal gruplara ayrılabilir. Ayırıcı, <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği <xref:System.Windows.Forms.ToolBarButtonStyle>olarak ayarlanan bir araç çubuğu düğmesidir. Araç çubuğunda boş alan olarak görünür. Araç çubuğunun düz bir görünümü olduğunda, düğme ayırıcıları düğmeler arasındaki boşluklar yerine satırlar halinde görünür.  
  
 <xref:System.Windows.Forms.ToolBar> denetim, bir <xref:System.Windows.Forms.ToolBar.Buttons%2A> koleksiyonuna <xref:System.Windows.Forms.Button> nesneleri ekleyerek araç çubukları oluşturmanıza olanak sağlar. <xref:System.Windows.Forms.ToolBar> denetimine düğme eklemek için koleksiyon düzenleyicisini kullanabilirsiniz; Her bir <xref:System.Windows.Forms.Button> nesnesi metin veya atanmış bir görüntü içermelidir, ancak her ikisini de atayabilirsiniz. Görüntü, ilişkili bir [ImageList](imagelist-component-windows-forms.md) bileşeni tarafından sağlanır. Çalışma zamanında, <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> ve <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> yöntemlerini kullanarak <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> düğme ekleyebilir veya kaldırabilirsiniz. Bir <xref:System.Windows.Forms.ToolBar>düğmelerini programlamak için, hangi düğmenin tıklandığını anlamak üzere <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sınıfının <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliğini kullanarak, <xref:System.Windows.Forms.ToolBar><xref:System.Windows.Forms.ToolBar.ButtonClick> olaylarına kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [Nasıl yapılır: Bir ToolBar Denetimine Düğme Ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](how-to-trigger-menu-events-for-toolbar-buttons.md)
