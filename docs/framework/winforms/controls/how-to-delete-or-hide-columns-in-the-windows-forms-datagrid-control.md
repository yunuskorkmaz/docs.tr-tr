---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme'
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
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967382"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimindeki sütunları, <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesnelerinin özelliklerini ve yöntemlerini ( <xref:System.Windows.Forms.DataGridTableStyle> sınıfının üyesi olan) kullanarak program aracılığıyla silebilir veya gizleyebilirsiniz.  
  
 Silinen veya gizli sütunlar, kılavuzun bağlandığı veri kaynağında hala bulunur ve yine de programlı olarak erişilebilir. Yalnızca DataGrid 'de görünür olmayacaktır.  
  
> [!NOTE]
> Uygulamanız belirli veri sütunlarına erişmezse ve DataGrid 'de görüntülenmesini istemiyorsanız, bu durumda bunları ilk yerde veri kaynağına dahil etmek gerekli değildir.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>DataGrid 'den bir sütunu programlı olarak silmek için  
  
1. Formunuzun bildirimler alanında, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> Özelliğini veri kaynağınızda stilini uygulamak istediğiniz tabloya ayarlayın. Aşağıdaki örnek, önceden ayarlanmış <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> olduğunu varsayan özelliği kullanır.  
  
3. Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesneyi DataGrid 'in tablo stilleri koleksiyonuna ekleyin.  
  
4. Silinecek sütunun sütun dizinini belirterek <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonunun yönteminiçağırın.<xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A>  
  
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
  
1. Formunuzun bildirimler alanında, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Öğesininözelliğini,verikaynağınızdakistilini<xref:System.Windows.Forms.DataGridTableStyle> uygulamak istediğiniz tabloya ayarlayın. Aşağıdaki kod örneği, zaten ayarlanmış <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> olduğunu varsayan özelliği kullanır.  
  
3. Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesneyi DataGrid 'in tablo stilleri koleksiyonuna ekleyin.  
  
4. `Width` Özelliğini 0 olarak ayarlayarak ve gizlenecek sütunun sütun dizinini belirterek sütunu gizleyin.  
  
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

- [Nasıl yapılır: Windows Forms DataGrid denetimindeki çalışma zamanında görünen verileri değiştirme](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
