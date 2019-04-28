---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimine Tablolar ve Sütunlar Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 5e530b475745a3df7482b9ea4276f004d13ec055
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642457"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimine Tablolar ve Sütunlar Ekleme

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms'ta verileri görüntüleyebilirsiniz <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde <xref:System.Windows.Forms.DataGridTableStyle> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.GridTableStylesCollection> aracılığıyla erişilen nesne <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği. Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>. Varsayılan olarak, belirtilen sütun stillerini olmadan bir tablo stili veri tablosunun tüm sütunları görüntüler. Tablodaki hangi sütunların ekleyerek görünür kısıtlayabilirsiniz <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri için <xref:System.Windows.Forms.GridColumnStylesCollection>, aracılığıyla erişilen <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> her özellik <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.DataGrid> denetimi. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' te varsayılan olarak <xref:System.Windows.Forms.DataGrid> denetimi içinde değil **araç kutusu**. Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Araç kutusu öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Tablo Tasarımcısı'nda DataGrid denetimi eklemek için  
  
1. Tablodaki verileri görüntülemek için öncelikle bağlanmalıdır <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimi Tasarımcısı'nı kullanarak bir veri kaynağına bağlama](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2. Seçin <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği, Özellikler penceresinde ve ardından üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki görüntülenecek özelliği **DataGridTableStyle Koleksiyonu Düzenleyicisi**.  
  
3. Koleksiyon Düzenleyicisi'nde **Ekle** tablo stili eklenecek.  
  
4. Tıklayın **Tamam** için koleksiyon düzenleyicisini kapatın ve yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda, denetime bağlı herhangi bir veri tabloları için açılır listede görünür <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> tablo stili özelliğidir.  
  
5. İçinde **üyeleri** kutusu Koleksiyonu Düzenleyicisi, tabloyu stilini tıklatın.  
  
6. İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> görüntülemek istediğiniz tablo değeri.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>DataGrid denetimi Tasarımcısı'nda bir sütun eklemek için  
  
1. İçinde **üyeleri** kutusunun **DataGridTableStyle Koleksiyonu Düzenleyicisi**, uygun tablo stili seçin. İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonu ve ardından üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png " vbEllipsesButton")) görüntülenecek özelliğin yanındaki **DataGridColumnStyle Koleksiyonu Düzenleyicisi**.  
  
2. Koleksiyon Düzenleyicisi'nde **Ekle** sütun stili eklemek veya yanındaki aşağı oka tıklayın **Ekle** sütun türünü belirtin.  
  
     Ya da seçin aşağı açılan kutusunda <xref:System.Windows.Forms.DataGridTextBoxColumn> veya <xref:System.Windows.Forms.DataGridBoolColumn> türü.  
  
3. Kapatmak için Tamam'a tıklayın **DataGridColumnStyle Koleksiyonu Düzenleyicisi**, yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda, tüm veri sütunlarını ilişkili veri tablosu için açılır listede görünür <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sütun style özelliği.  
  
4. İçinde **üyeleri** kutusu Koleksiyonu Düzenleyicisi, sütun stilini tıklatın.  
  
5. İçinde **özellikleri** Koleksiyonu Düzenleyicisi, seçim kutusunu <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> görüntülemek istediğiniz sütun için değer.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Silme veya Windows Forms DataGrid denetiminde sütunları gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
