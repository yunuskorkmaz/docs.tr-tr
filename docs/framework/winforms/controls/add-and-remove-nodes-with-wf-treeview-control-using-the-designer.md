---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ecf0b758a9c45a0354a68b6cbfecdb1c49ab390f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640384"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms çünkü <xref:System.Windows.Forms.TreeView> denetimi dikkat kendi üst düğümlerinin nedir için ödeme gerekir düğüm eklerken bu düğümleri hiyerarşik bir biçimde görüntüler.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TreeView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Ekleme veya düğümleri kaldırma Tasarımcısı'nda  
  
1. Seçin <xref:System.Windows.Forms.TreeView> denetimi.  
  
2. İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.  
  
     **Editor objektu TreeNode** görünür.  
  
3. Düğümler eklemek için bir kök düğümü olmalıdır; bir mevcut değilse, öncelikle bir kök tıklayarak eklemelisiniz **ekleme kök** düğmesi. Kök veya başka bir düğüme seçtikten sonra alt düğümleri ekleyebilirsiniz **alt öğe Ekle** düğmesi.  
  
4. Düğümleri silmek için silin ve ardından için düğümü seçin **Sil** düğmesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)
