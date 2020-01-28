---
title: Tasarımcıyı kullanarak DataGrid denetimine tablolar ve sütunlar ekleme
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: fed7465fbe665b1945161653616e3a21640e0b2a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746255"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimine Tablolar ve Sütunlar Ekleme

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

<xref:System.Windows.Forms.DataGridTableStyle> nesneleri oluşturarak ve bunları <xref:System.Windows.Forms.DataGrid> denetiminin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliğinden erişilen <xref:System.Windows.Forms.GridTableStylesCollection> nesnesine ekleyerek tablo ve sütunlardaki Windows Forms <xref:System.Windows.Forms.DataGrid> denetimindeki verileri görüntüleyebilirsiniz. Her tablo stili, <xref:System.Windows.Forms.DataGridTableStyle><xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğinde hangi veri tablosunun belirtilen içeriğini görüntüler. Varsayılan olarak, sütun stilleri olmayan bir tablo stili, bu veri tablosu içindeki tüm sütunları görüntüler. Her <xref:System.Windows.Forms.DataGridTableStyle><xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği aracılığıyla erişilen <xref:System.Windows.Forms.GridColumnStylesCollection><xref:System.Windows.Forms.DataGridColumnStyle> nesneleri ekleyerek tablodaki hangi sütunların görüneceğini sınırlayabilirsiniz.

Aşağıdaki yordamlar, bir <xref:System.Windows.Forms.DataGrid> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Bu tür bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetimleri ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' de varsayılan olarak <xref:System.Windows.Forms.DataGrid> denetimi **araç kutusunda**değildir. Ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: öğeleri ekleme araç kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Tasarımcıda DataGrid denetimine tablo eklemek için

1. Tablodaki verileri göstermek için öncelikle <xref:System.Windows.Forms.DataGrid> denetimini bir veri kümesine bağlamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGrid denetimini bir veri kaynağına bağlama](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. Özellikler penceresi <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliğini seçin ve sonra, **DataGridTableStyle koleksiyon düzenleyicisini**göstermek için özelliğin yanındaki üç![nokta düğmesini (...) ve ardından Özellikler penceresi) tıklatın.

3. Koleksiyon Düzenleyicisi 'nde tablo stili eklemek için **Ekle** ' ye tıklayın.

4. Koleksiyon düzenleyicisini kapatmak için **Tamam** ' ı tıklatın ve ardından <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak yeniden açın.

     Koleksiyon düzenleyicisini yeniden açtığınızda, denetime bağlanacak tüm veri tabloları tablo stilinin <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği için aşağı açılan listede görüntülenir.

5. Koleksiyon düzenleyicisinin **Üyeler** kutusunda tablo stiline tıklayın.

6. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, göstermek istediğiniz tablo için <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> değerini seçin.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Tasarımcıda DataGrid denetimine bir sütun eklemek için

1. **DataGridTableStyle koleksiyonu düzenleyicisinin** **Üyeler** kutusunda uygun tablo stilini seçin. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonunu seçin ve sonra DataGrid sütununun yanındaki üç nokta düğmesini (...](./media/visual-studio-ellipsis-button.png)Özellikler penceresi), **DataGrid ColumnStyle koleksiyon düzenleyicisini**göstermek için özelliği ' ne![.

2. Koleksiyon Düzenleyicisi 'nde, sütun stili eklemek için **Ekle** ' ye tıklayın veya bir sütun türü belirtmek için **Ekle** ' nin yanındaki aşağı oka tıklayın.

     Açılan kutuda <xref:System.Windows.Forms.DataGridTextBoxColumn> veya <xref:System.Windows.Forms.DataGridBoolColumn> türünü seçebilirsiniz.

3. Tamam ' a tıklayarak **DataGridColumnStyle koleksiyon düzenleyicisini**kapatın ve ardından <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak yeniden açın.

     Koleksiyon düzenleyicisini yeniden açtığınızda, ilişkili veri tablosundaki tüm veri sütunları sütun stilinin <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliği için aşağı açılan listede görüntülenir.

4. Koleksiyon düzenleyicisinin **Üyeler** kutusunda sütun stiline tıklayın.

5. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, göstermek istediğiniz sütun için <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> değerini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
