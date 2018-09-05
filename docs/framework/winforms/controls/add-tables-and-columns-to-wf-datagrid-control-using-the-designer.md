---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimine Tablolar ve Sütunlar Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 745e866363dc7547ee540b9cac7e1e9fd3cc79ee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504939"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimine Tablolar ve Sütunlar Ekleme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms'ta verileri görüntüleyebilirsiniz <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde <xref:System.Windows.Forms.DataGridTableStyle> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.GridTableStylesCollection> aracılığıyla erişilen nesne <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği. Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>. Varsayılan olarak, belirtilen sütun stillerini olmadan bir tablo stili veri tablosunun tüm sütunları görüntüler. Tablodaki hangi sütunların ekleyerek görünür kısıtlayabilirsiniz <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri için <xref:System.Windows.Forms.GridColumnStylesCollection>, aracılığıyla erişilen <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> her özellik <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.DataGrid> denetimi. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Varsayılan olarak [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> denetimi içinde değil **araç kutusu**. Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: araç kutusu öğeleri Ekle](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Tablo Tasarımcısı'nda DataGrid denetimi eklemek için  
  
1.  Tablodaki verileri görüntülemek için öncelikle bağlanmalıdır <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini kullanarak bir veri kaynağı için tasarımcı bağlama](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Seçin <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği, Özellikler penceresinde ve ardından üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki görüntülenecek özelliği **DataGridTableStyle Koleksiyonu Düzenleyicisi**.  
  
3.  Koleksiyon Düzenleyicisi'nde **Ekle** tablo stili eklenecek.  
  
4.  Tıklayın **Tamam** için koleksiyon düzenleyicisini kapatın ve yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda, denetime bağlı herhangi bir veri tabloları için açılır listede görünür <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> tablo stili özelliğidir.  
  
5.  İçinde **üyeleri** kutusu Koleksiyonu Düzenleyicisi, tabloyu stilini tıklatın.  
  
6.  İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> görüntülemek istediğiniz tablo değeri.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>DataGrid denetimi Tasarımcısı'nda bir sütun eklemek için  
  
1.  İçinde **üyeleri** kutusunun **DataGridTableStyle Koleksiyonu Düzenleyicisi**, uygun tablo stili seçin. İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonu ve ardından üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) görüntülenecek özelliğin yanındaki **DataGridColumnStyle Koleksiyonu Düzenleyicisi**.  
  
2.  Koleksiyon Düzenleyicisi'nde **Ekle** sütun stili eklemek veya yanındaki aşağı oka tıklayın **Ekle** sütun türünü belirtin.  
  
     Ya da seçin aşağı açılan kutusunda <xref:System.Windows.Forms.DataGridTextBoxColumn> veya <xref:System.Windows.Forms.DataGridBoolColumn> türü.  
  
3.  Kapatmak için Tamam'a tıklayın **DataGridColumnStyle Koleksiyonu Düzenleyicisi**, yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda, tüm veri sütunlarını ilişkili veri tablosu için açılır listede görünür <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sütun style özelliği.  
  
4.  İçinde **üyeleri** kutusu Koleksiyonu Düzenleyicisi, sütun stilini tıklatın.  
  
5.  İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> görüntülemek istediğiniz sütun için değer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
