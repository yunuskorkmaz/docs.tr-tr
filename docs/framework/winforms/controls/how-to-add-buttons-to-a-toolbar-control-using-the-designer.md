---
title: "Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccd63cb88661db7601b87eec6bdf3a959afb8bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ToolBar> kontrol; ancak, <xref:System.Windows.Forms.ToolBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Bütünleyici <xref:System.Windows.Forms.ToolBar> denetimidir ona eklediğiniz düğmeler. Bunlar, menü komutlarını kolay erişim sağlamak için kullanılabilir veya alternatif olarak, bunlar menü yapısındaki kullanılabilir değil, kullanıcılarınıza komutları kullanıma sunmak için uygulamanızın kullanıcı arabiriminin bir diğer alan yerleştirilebilir.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ToolBar> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-buttons-at-design-time"></a>Tasarım zamanında düğmeleri eklemek için  
  
1.  Seçin <xref:System.Windows.Forms.ToolBar> denetim.  
  
2.  İçinde **özellikleri** penceresinde tıklatın <xref:System.Windows.Forms.ToolBar.Buttons%2A> onu seçin ve özellik **üç nokta** (![VisualStudioEllipsesButton ekran] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) açmak için düğmeye **ToolBarButton Koleksiyonu Düzenleyicisi**.  
  
3.  Kullanım **Ekle** ve **kaldırmak** ekleyip düğmelerden Kaldır düğmelerini <xref:System.Windows.Forms.ToolBar> denetim.  
  
4.  Düğmelerin özelliklerini yapılandırmak **özellikleri** Düzenleyicisinin sağ taraftaki bölmede görüntülenen penceresi. Aşağıdaki tabloda dikkate alınması gereken bazı önemli özellikleri gösterir.  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Menü açılan araç çubuğu düğmesini görüntülenecek ayarlar. Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Bu özellik bir örneğini alır <xref:System.Windows.Forms.ContextMenu> sınıfı bir başvuru olarak.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|İki durumlu stili araç çubuğu düğmesi kısmen gönderilen olup olmadığını belirler. Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|İki durumlu stili araç çubuğu düğmesi şu anda zorlanan durumda olup olmadığını belirler. Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> veya <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Araç çubuğu düğmesi stilini ayarlar. Değerlerden biri olmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle> numaralandırması.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Düğme tarafından görüntülenen metin dizesi.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Düğme için bir araç ipucu olarak görüntülenen metin.|  
  
5.  Tıklatın **Tamam** iletişim kutusunu kapatmak ve belirttiğiniz panelleri oluşturmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolBar>  
 [Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar Denetimi](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
