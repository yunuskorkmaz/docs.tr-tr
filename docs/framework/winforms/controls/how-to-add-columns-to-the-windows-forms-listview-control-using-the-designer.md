---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 9ddff31e4d66ffef2600a1246b35c0a66154c341
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190430"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme
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
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
