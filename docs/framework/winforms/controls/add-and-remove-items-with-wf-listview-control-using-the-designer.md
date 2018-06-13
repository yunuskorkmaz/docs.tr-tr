---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimi ile Öğe Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 9e50283eb21a6d5dc558bed67b5fdf341dd56288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528739"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimi ile Öğe Ekleme ve Kaldırma
Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> denetim oluşur öncelikle öğesi belirtme ve Özellikler atayarak. Liste öğe ekleme veya kaldırma herhangi bir zamanda yapılabilir.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ListView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Tasarımcı kullanarak öğe eklemek veya kaldırmak için  
  
1.  Seçin <xref:System.Windows.Forms.ListView> denetim.  
  
2.  İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.ListView.Items%2A> özelliği.  
  
     **ListViewItem Koleksiyonu Düzenleyicisi** görüntülenir.  
  
3.  Bir öğe eklemek için tıklatın **Ekle** düğmesi. Yeni öğe özelliklerini gibi daha sonra ayarlamak <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.  
  
4.  Bir öğeyi kaldırmak için onu seçin ve tıklatın **kaldırmak** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
