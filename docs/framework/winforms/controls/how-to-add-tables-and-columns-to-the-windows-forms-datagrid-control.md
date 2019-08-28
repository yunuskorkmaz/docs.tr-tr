---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: bfb0296566fecc2029df16d91c9c04d7daa4b4b5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046164"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

**DataGridTableStyle** nesneleri oluşturarak ve bunları <xref:System.Windows.Forms.DataGrid> denetimin tarafından <xref:System.Windows.Forms.DataGrid> erişilen **GridTableStylesCollection** nesnesine ekleyerek tablo ve sütunlardaki verileri Windows Forms denetiminde görüntüleyebilirsiniz. **TableStyles** özelliği. Her tablo stili, **DataGridTableStyle** nesnesinin **MappingName** özelliğinde belirtilen veri tablosunun içeriğini görüntüler. Varsayılan olarak, hiçbir sütun stili belirtilmemiş bir tablo stili, bu veri tablosundaki tüm sütunları görüntüler. Her bir **DataGridTableStyle** 'ın **GridColumnStyles** özelliğinden erişilen **GridColumnStylesCollection** nesnesine **DataGridColumnStyle** nesneleri ekleyerek tablodaki sütunların görüneceğini kısıtlayabilirsiniz nesne.

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Bir DataGrid 'e programlı bir şekilde tablo ve sütun eklemek için

1. Tablodaki verileri göstermek için öncelikle <xref:System.Windows.Forms.DataGrid> denetimi bir veri kümesine bağlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)bağlayın.

    > [!CAUTION]
    > Program aracılığıyla sütun stillerini belirtirken, her zaman **DataGridColumnStyle** nesneleri oluşturun ve bu nesneye **DataGridTableStyle** nesneleri **eklemeden önce GridColumnStylesCollection nesnesine ekleyin GridTableStylesCollection** nesnesi. Koleksiyona boş bir **DataGridTableStyle** nesnesi eklediğinizde, sizin Için **DataGridColumnStyle** nesneleri otomatik olarak oluşturulur. Sonuç olarak, **GridColumnStylesCollection** nesnesine yinelenen **MappingName** değerleriyle yeni **DataGridColumnStyle** nesneleri eklemeye çalışırsanız bir özel durum oluşturulur.

2. Yeni bir tablo stili bildirin ve onun eşleme adını ayarlayın.

    ```vb
    Dim ts1 As New DataGridTableStyle()
    ts1.MappingName = "Customers"
    ```

    ```csharp
    DataGridTableStyle ts1 = new DataGridTableStyle();
    ts1.MappingName = "Customers";
    ```

    ```cpp
    DataGridTableStyle* ts1 = new DataGridTableStyle();
    ts1->MappingName = S"Customers";
    ```

3. Yeni bir sütun stili bildirin ve onun eşleme adını ve diğer özelliklerini ayarlayın.

    ```vb
    Dim myDataCol As New DataGridBoolColumn()
    myDataCol.HeaderText = "My New Column"
    myDataCol.MappingName = "Current"
    ```

    ```csharp
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();
    myDataCol.HeaderText = "My New Column";
    myDataCol.MappingName = "Current";
    ```

    ```cpp
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();
    myDataCol->HeaderText = "My New Column";
    myDataCol->MappingName = "Current";
    ```

4. Sütunu tablo stiline eklemek için **GridColumnStylesCollection** nesnesinin **Add** metodunu çağırın

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. Tablo stilini veri kılavuzuna eklemek için **GridTableStylesCollection** nesnesinin **Add** metodunu çağırın.

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
