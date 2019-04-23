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
ms.openlocfilehash: cc364f3609f8041378b0b03b8e1bc8f312fade18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319917"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms'ta verileri görüntüleyebilirsiniz <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde **DataGridTableStyle** nesneleri ve bunlara ekleme **GridTableStylesCollection** nesne üzerinden erişilen <xref:System.Windows.Forms.DataGrid> denetimin **TableStyles** özelliği. Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler **DataGridTableStyle** nesnenin **MappingName** özelliği. Varsayılan olarak, veri tablosunun tüm sütunları belirtilen hiçbir sütun stillerini sahip bir tablo stili görüntüler. Tablodaki hangi sütunların ekleyerek görünür kısıtlayabilirsiniz **DataGridColumnStyle** nesneleri için **GridColumnStylesCollection** aracılığıyla erişilen nesne  **GridColumnStyles** her özellik **DataGridTableStyle** nesne.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>DataGrid denetimine tablo ve sütun programsal olarak eklemek için  
  
1. Tablodaki verileri görüntülemek için öncelikle bağlanmalıdır <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Sütun stillerini programlı olarak belirtme, her zaman Oluştur **DataGridColumnStyle** nesneleri ve bunları Ekle **GridColumnStylesCollection** eklemeden önce nesne  **DataGridTableStyle** nesneleri için **GridTableStylesCollection** nesne. Boş bir eklediğinizde **DataGridTableStyle** nesnesini koleksiyonuna **DataGridColumnStyle** nesneleri otomatik olarak üretilen sizin için. Yeni eklemeyi denerseniz, bu nedenle, bir özel durum oluşturulur **DataGridColumnStyle** yinelenen nesneleriyle **MappingName** değerler **GridColumnStylesCollection**nesne.  
  
2. Yeni bir tablo stili bildirme ve eşleme adını ayarlayın.  
  
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
  
3. Yeni bir sütun stili bildirme ve eşleme adını ve diğer özellikleri ayarlayın.  
  
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
  
4. Çağrı **Ekle** yöntemi **GridColumnStylesCollection** nesne için tablo stili sütun eklemek için  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5. Çağrı **Ekle** yöntemi **GridTableStylesCollection** veri kılavuzu için tablo stili eklenecek nesne.  
  
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
- [Nasıl yapılır: Silme veya Windows Forms DataGrid denetiminde sütunları gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
