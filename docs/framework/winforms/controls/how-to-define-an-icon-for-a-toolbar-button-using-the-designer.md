---
title: "Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e72b2516efab3bc5b5d8cc7cacb66f149f3a66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ToolBar> kontrol; ancak, <xref:System.Windows.Forms.ToolBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 <xref:System.Windows.Forms.ToolBar>düğmeleri kullanıcılar tarafından kolay bir şekilde tanımlanması için bunları içinde simge görüntüleyebilir. Bu görüntüleri ekleme aracılığıyla elde edilen <xref:System.Windows.Forms.ImageList> bileşeni ve onunla ilişkili <xref:System.Windows.Forms.ToolBar> denetim.  
  
 Aşağıdaki yordamı gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ToolBar> denetim ve bir <xref:System.Windows.Forms.ImageList> bileşeni. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Tasarım zamanında bir araç çubuğu düğmesi için simge ayarlamak için  
  
1.  Görüntüleri ekleme <xref:System.Windows.Forms.ImageList> bileşeni. Daha fazla bilgi için bkz: [nasıl yapılır: tasarımcı ile ImageList'görüntüleri ekleyip](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Seçin <xref:System.Windows.Forms.ToolBar> formunuzda denetim.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ImageList%2A> özelliğine <xref:System.Windows.Forms.ImageList> bileşeni.  
  
4.  Tıklatın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.Buttons%2A> seçin ve üç nokta düğmesine özelliği (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmakiçindüğmeye**ToolBarButton Koleksiyonu Düzenleyicisi**.  
  
5.  Kullanım **Ekle** düğmeleri için Ekle düğmesini <xref:System.Windows.Forms.ToolBar> denetim.  
  
6.  İçinde **özellikleri** sağ taraftaki bölmede görüntülenen penceresi **ToolBarButton Koleksiyonu Düzenleyicisi**ayarlayın <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> her araç çubuğu düğmesi listesinde değerlerden birine özelliği, eklediğiniz görüntülerden çizilmiş <xref:System.Windows.Forms.ImageList> bileşeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolBar>  
 [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar Denetimi](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList Bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
