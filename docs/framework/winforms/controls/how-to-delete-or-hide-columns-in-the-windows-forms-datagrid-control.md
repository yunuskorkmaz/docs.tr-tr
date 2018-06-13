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
ms.openlocfilehash: 6541ffff1149e5df13c43ee392ffa8b221c8407d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534560"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Program aracılığıyla silme veya Windows Forms'ta sütunları gizleme <xref:System.Windows.Forms.DataGrid> özelliklerini ve yöntemlerini kullanarak denetim <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri (üyeleri <xref:System.Windows.Forms.DataGridTableStyle> sınıfı).  
  
 Veri kaynağı kılavuz bağlı ve hala programlı olarak erişilebilir silinmiş ya da gizli sütunlar hala var. Yalnızca artık datagrid denetiminde görünür değildir.  
  
> [!NOTE]
>  Uygulamanızı belirli veri sütunlarının erişmez ve bunları datagrid denetiminde görüntülenen istemiyorsanız, ardından bu veri kaynağındaki ilk başta dahil etmek gerekli değildir büyük olasılıkla.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>DataGrid programlı olarak bir sütun silmek için  
  
1.  Formunuz bildirimleri alanında yeni bir örneğini bildirme <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.  
  
2.  Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> stil uygulamak istediğiniz veri kaynağınız tablosuna özelliği. Aşağıdaki örnek kullanır <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> zaten ayarlanmış varsayar özelliği.  
  
3.  Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyonunda nesnesine.  
  
4.  Çağrı <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> silmek için sütunun sütun dizini belirtme koleksiyonu.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>DataGrid sütununda program aracılığıyla gizleme  
  
1.  Formunuz bildirimleri alanında yeni bir örneğini bildirme <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.  
  
2.  Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle> stil uygulamak istediğiniz veri kaynağınız tablosuna. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> zaten ayarlanmış varsayar özelliği.  
  
3.  Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyonunda nesnesine.  
  
4.  Ayarlayarak sütun gizleme kendi `Width` özelliği 0 olarak gizlemek için sütunun sütun dizini belirtme.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
