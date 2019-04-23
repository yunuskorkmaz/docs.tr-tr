---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 6e08a7013242b0dbb433e288c4f8d788cb4e143b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343850"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma
Bir Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> öncelikle, bulunan öğeyi belirten ve Özellikler atayarak denetimi oluşur. Liste öğe ekleme veya kaldırma herhangi bir zamanda gerçekleştirilebilir.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ListView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Tasarımcı kullanarak bir öğe eklemek veya kaldırmak için  
  
1. Seçin <xref:System.Windows.Forms.ListView> denetimi.  
  
2. İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.ListView.Items%2A> özelliği.  
  
     **ListViewItem Koleksiyonu Düzenleyicisi** görünür.  
  
3. Bir öğe eklemek için tıklayın **Ekle** düğmesi. Yeni öğenin özelliklerini aşağıdaki gibi ayarlayabilirsiniz <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.  
  
4. Bir öğe kaldırmak için onu seçin ve **Kaldır** düğmesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma](how-to-group-items-in-a-windows-forms-listview-control.md)
