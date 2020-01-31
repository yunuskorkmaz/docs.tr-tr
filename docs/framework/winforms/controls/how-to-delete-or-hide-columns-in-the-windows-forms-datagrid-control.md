---
title: DataGrid denetimindeki sütunları silme veya gizleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743300"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesnelerinin özelliklerini ve yöntemlerini (<xref:System.Windows.Forms.DataGridTableStyle> sınıfının üyesi olan) kullanarak Windows Forms <xref:System.Windows.Forms.DataGrid> denetimindeki sütunları program aracılığıyla silebilir veya gizleyebilirsiniz.  
  
 Silinen veya gizli sütunlar, kılavuzun bağlandığı veri kaynağında hala bulunur ve yine de programlı olarak erişilebilir. Yalnızca DataGrid 'de görünür olmayacaktır.  
  
> [!NOTE]
> Uygulamanız belirli veri sütunlarına erişmezse ve DataGrid 'de görüntülenmesini istemiyorsanız, bu durumda bunları ilk yerde veri kaynağına dahil etmek gerekli değildir.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>DataGrid 'den bir sütunu programlı olarak silmek için  
  
1. Formunuzun bildirimler alanında <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> özelliğini veri kaynağınızda stilini uygulamak istediğiniz tabloya ayarlayın. Aşağıdaki örnek, zaten ayarlanmış olduğunu varsayan <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
3. Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesnesini DataGrid 'in tablo stilleri koleksiyonuna ekleyin.  
  
4. Silinecek sütunun sütun dizinini belirterek <xref:System.Windows.Forms.DataGrid><xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonunun <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> yöntemini çağırın.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>DataGrid 'deki bir sütunu programlı bir şekilde gizlemek için  
  
1. Formunuzun bildirimler alanında <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini, stili uygulamak istediğiniz veri kaynağınızdaki tabloya ayarlayın. Aşağıdaki kod örneği, zaten ayarlanmış olduğunu varsayan <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
3. Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesnesini DataGrid 'in tablo stilleri koleksiyonuna ekleyin.  
  
4. `Width` özelliğini 0 olarak ayarlayarak sütunu gizleyin, gizlenecek sütunun sütun dizinini belirtin.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
