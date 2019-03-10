---
title: "Nasıl yapılır: Windows Forms ListView Tasarımcısı'nı kullanarak denetimine sütun ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 725976e0d4b5903659cc264902890329bd13fcad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717290"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Windows Forms ListView Tasarımcısı'nı kullanarak denetimine sütun ekleme
Windows Forms <xref:System.Windows.Forms.ListView> denetim her liste için birden çok sütun görüntüleyebilir, öğe **ayrıntıları** görünümü. Sütunları türlerinden her liste öğesi hakkında bilgi görüntülemek için kullanabilirsiniz. Örneğin, dosya adı, dosya türü, boyutu ve dosyanın en son değiştirildiği tarih dosyaların listesini görüntüleyebilirsiniz. Oluşturulduktan sonra sütun doldurma üzerinde daha fazla bilgi için bkz: [nasıl yapılır: Görüntü denetimiyle Windows sütunlardaki alt öğeleri Forms ListView denetiminde](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ListView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-columns-in-the-designer"></a>Sütunların Tasarımcısı'nda eklemek için  
  
1.  İçinde **özellikleri** penceresinde ayarlayın denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>.  
  
2.  İçinde **özellikleri** penceresinde tıklayın **üç nokta** düğmesine (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.ListView.Columns%2A> özelliği.  
  
     **ColumnHeader Koleksiyonu Düzenleyicisi** görünür.  
  
3.  Kullanım **Ekle** yeni sütun ekleme düğmesi. Ardından sütun başlığını seçin ve kendi metin (sütun başlığını), metin hizalamasını ve genişliğini ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)
