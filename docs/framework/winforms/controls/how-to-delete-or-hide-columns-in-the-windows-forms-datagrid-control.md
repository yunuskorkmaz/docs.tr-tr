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
ms.openlocfilehash: d3f1f013cbb5e41c997014f556602b01bab62914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757397"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Program aracılığıyla silin veya Windows Forms sütunları gizleyin <xref:System.Windows.Forms.DataGrid> özellikleri ve yöntemleri kullanarak denetim <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri (üyeleri <xref:System.Windows.Forms.DataGridTableStyle> sınıfı).  
  
 Silinmiş veya gizli sütunları kılavuz bağlı olduğu ve hala program aracılığıyla erişilebilir veri kaynağında varolmaya devam eder. Bundan böyle datagrid denetiminde görünür.  
  
> [!NOTE]
>  Uygulamanızın belirli sütunları veri erişimi yoktur ve bunları DataGrid'deki görüntülenmesini istemiyorsanız, ardından bu veri kaynağındaki ilk başta eklemek gerekli değildir büyük olasılıkla.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Bir sütun DataGrid'den programlı olarak silmek için  
  
1. Formunuza bildirimleri alanında yeni bir örneğini bildirmeniz <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.  
  
2. Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> stile uygulamak istediğiniz veri kaynağı tablosuna özelliği. Aşağıdaki örnekte <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> özelliği zaten ayarlanmış varsayar.  
  
3. Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyona nesne.  
  
4. Çağrı <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> sütun dizini silmek için sütun belirterek koleksiyonu.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Bir sütunun DataGrid'deki program aracılığıyla gizleme  
  
1. Formunuza bildirimleri alanında yeni bir örneğini bildirmeniz <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.  
  
2. Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini <xref:System.Windows.Forms.DataGridTableStyle> tablosuna stile uygulamak istediğiniz veri kaynağı. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> özelliği zaten ayarlanmış varsayar.  
  
3. Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyona nesne.  
  
4. Ayarlayarak sütunu gizleyin kendi `Width` özelliği 0 olarak gizlemek için sütunun sütun dizini belirtme.  
  
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

- [Nasıl yapılır: Windows Forms DataGrid denetiminde çalışma zamanında görüntülenen verileri değiştirme](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
