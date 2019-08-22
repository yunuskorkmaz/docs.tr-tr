---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666215"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip>

<xref:System.Windows.Forms.ToolBar> Denetimin integral bir bölümü, ona eklediğiniz düğmelerdir. Bunlar menü komutlarına kolay erişim sağlamak için kullanılabilir veya alternatif olarak, menü yapısında kullanılamayan kullanıcılarınıza komutları göstermek için uygulamanızın kullanıcı arabiriminin başka bir alanına yerleştirilebilecek.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ToolBar> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

### <a name="to-add-buttons-at-design-time"></a>Tasarım zamanında düğme eklemek için

1. <xref:System.Windows.Forms.ToolBar> Denetimi seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.ToolBar.Buttons%2A> özelliği tıklatıp seçin ve sonra da Visual Studio 'nun Özellikler penceresi üç nokta (![...) düğmesini tıklatın.](./media/visual-studio-ellipsis-button.png)ToolBarButton 'ı açmak için  **Koleksiyon Düzenleyicisi**.

3. Denetime düğme eklemek ve kaldırmak için Ekle ve **Kaldır** düğmelerini kullanın. <xref:System.Windows.Forms.ToolBar>

4. Düzenleyicinin sağ tarafındaki bölmede görüntülenen **Özellikler** penceresinde tek düğmelerin özelliklerini yapılandırın. Aşağıdaki tabloda dikkate alınması gereken bazı önemli özellikler gösterilmektedir.

    |Özellik|Açıklama|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Açılan araç çubuğu düğmesinde görüntülenecek menüyü ayarlar. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği olarak <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>ayarlanmalıdır. Bu özellik, <xref:System.Windows.Forms.ContextMenu> bir başvuru olarak sınıfının bir örneğini alır.|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Bir değiştirme stili araç çubuğu düğmesinin kısmen gönderilip atılmayacağını ayarlar. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği olarak <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>ayarlanmalıdır.|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Geçiş stili bir araç çubuğu düğmesinin Şu anda basılmış durumunda olup olmadığını ayarlar. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği veya <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>olarak <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> ayarlanmalıdır.|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Araç çubuğu düğmesinin stilini ayarlar. <xref:System.Windows.Forms.ToolBarButtonStyle> Numaralandırmadaki değerlerden biri olmalıdır.|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Düğme tarafından görünen metin dizesi.|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Düğme için araç Ipucu olarak görünen metin.|

5. İletişim kutusunu kapatmak ve belirlediğiniz bölmeleri oluşturmak için **Tamam** ' a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [Nasıl yapılır: Bir araç çubuğu düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar Denetimine Genel Bakış](toolbar-control-overview-windows-forms.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
