---
title: ToolBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: 7b39c8e3dca88e968b43ba5ff14794e2e77247d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174817"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> denetimi form üzerinde bir satır aşağı açılan menüler ve komutlar etkinleştirme bit eşlemli düğmeler görüntüleyen bir denetim çubuğu kullanılır. Bu nedenle, bir araç çubuğu düğmesini seçerek bir menü komutu için eşdeğer olabilir. Düğmeler, görünür ve pushbuttons, aşağı açılan menüler veya ayırıcı davranır şekilde yapılandırılabilir. Genellikle, bir araç çubuğu düğmeleri ve bir uygulamanın en sık kullanılan işlevler ve komutlar için hızlı erişim sağlayan bir uygulama menüsü yapısı öğelere karşılık gelen menüleri içerir.  
  
## <a name="working-with-the-toolbar-control"></a>Araç çubuğu denetimiyle çalışma  
 A <xref:System.Windows.Forms.ToolBar> denetimi genellikle "yerleştirilmiştir" üst pencereye üst kısmında, ancak ayrıca pencere tarafına sabitlenebilir. Kullanıcı, fare işaretçisini bir araç çubuğu düğmesini işaret ettiğinde, bir araç çubuğu araç ipuçları görüntüleyebilirsiniz. Bir araç ipucu düğmesini veya menünün amaçlı kısaca açıklayan küçük bir açılır penceredir. Araç ipuçları, görüntülenecek <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> özelliği ayarlanmalıdır `true`.  
  
> [!NOTE]
>  Bazı uygulamalar, "uygulama pencerenin Kaydır" ve konumlandırılmasına olanağına sahip araç çubuğuna benzer denetimleri özellik. Windows Forms araç çubuğu denetimi bu işlemleri yapmak mümkün değil.  
  
 Zaman <xref:System.Windows.Forms.ToolBar.Appearance%2A> özelliği <xref:System.Windows.Forms.ToolBarAppearance>, yükseltilmiş ve üç boyutlu araç çubuğu düğmeleri görünür. Ayarlayabileceğiniz <xref:System.Windows.Forms.ToolBar.Appearance%2A> araç çubuğuna özelliği <xref:System.Windows.Forms.ToolBarAppearance> araç ve düğmeleri düz bir görünüm sağlamak için. Düz bir düğmenin üzerine fare işaretçisi hareket ettirdiğinde düğmenin görünümünü için üç boyutlu değiştirir. Araç çubuğu düğmeleri ayırıcılarını kullanarak mantıksal gruplar halinde ayrılabilir. Ayırıcı ile bir araç çubuğu düğmesi olduğunu <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliğini <xref:System.Windows.Forms.ToolBarButtonStyle>. Araç çubuğunda boş alan olarak görünür. Araç bir düz görünüm olduğunda düğme ayırıcıları düğmeler arasındaki boşluklar yerine çizgiler olarak görünür.  
  
 <xref:System.Windows.Forms.ToolBar> Denetimi ekleyerek araç çubukları oluşturmanıza imkan tanır <xref:System.Windows.Forms.Button> nesneleri için bir <xref:System.Windows.Forms.ToolBar.Buttons%2A> koleksiyonu. Düğme eklemek için koleksiyon düzenleyicisini kullanma bir <xref:System.Windows.Forms.ToolBar> denetimi; her <xref:System.Windows.Forms.Button> nesne olmalıdır metin veya atanan görüntü ancak her ikisini de atayabilirsiniz. Sağlanan görüntü ile ilişkili bir [ImageList](imagelist-component-windows-forms.md) bileşeni. Çalışma zamanında ekleme veya kaldırma düğmelerden <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> kullanarak <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> ve <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> yöntemleri. Düğmeler, programı için bir <xref:System.Windows.Forms.ToolBar>, kodu ekleyin <xref:System.Windows.Forms.ToolBar.ButtonClick> olayları <xref:System.Windows.Forms.ToolBar>kullanarak <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> hangi düğmesine tıklandığını belirleme için sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [Nasıl yapılır: Bir ToolBar denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: ToolBar düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme](how-to-trigger-menu-events-for-toolbar-buttons.md)
