---
title: 'Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 5de7645ecbf2123df849046a152643cd629b4898
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038231"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip>

<xref:System.Windows.Forms.ToolBar>düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeleri içinde görüntüleyebilir. Bu, <xref:System.Windows.Forms.ImageList> bileşene görüntü eklenerek ve <xref:System.Windows.Forms.ToolBar> denetimi ile ilişkilendirerek elde edilir.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ToolBar> denetim ve <xref:System.Windows.Forms.ImageList> bileşen içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.


### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Tasarım zamanında bir araç çubuğu düğmesine simge ayarlamak için

1. <xref:System.Windows.Forms.ImageList> Bileşene resim ekleyin. Daha fazla bilgi için [nasıl yapılır: Tasarımcı](how-to-add-or-remove-imagelist-images-with-the-designer.md)ile ImageList görüntüleri ekleyin veya kaldırın.

2. <xref:System.Windows.Forms.ToolBar> Formunuzdaki denetimi seçin.

3. **Özellikler** penceresinde, <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ImageList%2A> özelliğini <xref:System.Windows.Forms.ImageList> bileşen olarak ayarlayın.

4. ![](./media/visual-studio-ellipsis-button.png)Seçmek için <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.Buttons%2A> denetimin özelliğine tıklayın ve sonra ToolBarButton koleksiyon düzenleyicisini açmak için üç nokta (Visual Studio 'nun Özellikler penceresi) düğmesine tıklayın.

5. <xref:System.Windows.Forms.ToolBar> Denetime düğme eklemek için **Ekle** düğmesini kullanın.

6. **ToolBarButton koleksiyon düzenleyicisinin**sağ tarafındaki bölmede görüntülenen <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> **Özellikler** penceresinde, her bir araç çubuğu düğmesinin özelliğini listedeki değerlerden birine, bu düğmeye eklediğiniz görüntülerden çizmiş olacak şekilde ayarlayın. <xref:System.Windows.Forms.ImageList> bileşen.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [ImageList Bileşeni](imagelist-component-windows-forms.md)
