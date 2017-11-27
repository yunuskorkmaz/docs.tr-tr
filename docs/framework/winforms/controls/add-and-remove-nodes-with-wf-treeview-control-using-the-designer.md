---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f6295f915e9204e9996d8902b07a3dfc4c5c2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms çünkü <xref:System.Windows.Forms.TreeView> denetimi kendi üst düğümlerinin nedir için dikkat ödeme gerekir bir düğüm eklerken bu düğümler hiyerarşik bir biçimde görüntüler.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.TreeView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Ekleme veya düğümleri Tasarımcısı'nda kaldırmak için  
  
1.  Seçin <xref:System.Windows.Forms.TreeView> denetim.  
  
2.  İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.  
  
     **TreeNode Düzenleyicisi** görüntülenir.  
  
3.  Düğümler eklemek için bir kök düğümü olmalıdır; bir mevcut değilse, önce bir kök tıklayarak eklemelisiniz **eklemek kök** düğmesi. Kök veya başka bir düğüme seçerek ve tıklatarak daha sonra alt düğümler ekleyebilirsiniz **alt öğe Ekle** düğmesi.  
  
4.  Düğümleri silmek için silin ve ardından düğümü seçin **silmek** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView denetimine genel bakış](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Nasıl yapılır: hangi TreeView düğümüne tıklandığını belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Nasıl yapılır: bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
