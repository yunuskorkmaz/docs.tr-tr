---
title: 'Nasıl yapılır: Tasarımcı kullanarak ToolBar düğmesi için simge tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: ba24cb13b80a90bbf309ae23de15b33caf14735b
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303380"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak ToolBar düğmesi için simge tanımlama
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 <xref:System.Windows.Forms.ToolBar> düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeler içlerindeki görüntüleyebilir. Bu görüntüleri eklerken size sağlanır <xref:System.Windows.Forms.ImageList> bileşeni ve onunla ilişkili <xref:System.Windows.Forms.ToolBar> denetimi.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form ile bir <xref:System.Windows.Forms.ToolBar> denetimi ve bir <xref:System.Windows.Forms.ImageList> bileşeni. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Tasarım zamanında bir araç çubuğu düğmesi için simge ayarlamak için  
  
1.  Görüntüleri ekleme <xref:System.Windows.Forms.ImageList> bileşeni. Daha fazla bilgi için [nasıl yapılır: Tasarımcı ile ImageList görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Seçin <xref:System.Windows.Forms.ToolBar> formunuzdaki denetimi.  
  
3.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ImageList%2A> özelliğini <xref:System.Windows.Forms.ImageList> bileşeni.  
  
4.  Tıklayın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.Buttons%2A> özelliği seçin ve üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmakiçindüğmeyi**ToolBarButton Koleksiyonu Düzenleyicisi**.  
  
5.  Kullanım **Ekle** düğmeleri eklemek için Ekle düğmesine <xref:System.Windows.Forms.ToolBar> denetimi.  
  
6.  İçinde **özellikleri** sağ tarafındaki bölmede görüntülenen penceresi **ToolBarButton Koleksiyonu Düzenleyicisi**ayarlayın <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> her araç çubuğu düğmesi listede yer alan değerlerden birine özelliği, eklediğiniz görüntülerinden alınan <xref:System.Windows.Forms.ImageList> bileşeni.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ToolBar>
- [Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar Denetimi](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
- [ImageList Bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
