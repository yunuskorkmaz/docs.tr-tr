---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 27608a7fbce5e9aa815b43e1d7202fa11e52ee1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175610"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Bir Windows Forms oluşturduktan sonra <xref:System.Windows.Forms.DataGrid> tasarım-zamanı Özellikleri'ni kullanarak da öğelerini dinamik olarak değiştirmek isteyebilirsiniz <xref:System.Data.DataSet> kılavuzunun çalışma zamanında nesne. Bu tablo ya da tek tek değerlere değişiklikleri içerebilir veya veri kaynağını değiştirme bağlı <xref:System.Windows.Forms.DataGrid> denetimi. Değişiklikler tek tek değerlere aracılığıyla yapılır <xref:System.Data.DataSet> nesnesi değil, <xref:System.Windows.Forms.DataGrid> denetimi.  
  
### <a name="to-change-data-programmatically"></a>Verileri program aracılığıyla değiştirme  
  
1.  İstenen tablosundan belirtin <xref:System.Data.DataSet> nesne ve istenen tablodan alan satır ve hücre yeni değere eşit olarak ayarlayın.  
  
    > [!NOTE]
    >  İlk tablonun belirtmek için <xref:System.Data.DataSet> veya tablonun ilk satırının 0 kullanın.  
  
     Aşağıdaki örnek, bir veri kümesinin ilk tablonun ilk satırın ikinci girdi değiştirmek gösterilmektedir `Button1`. <xref:System.Data.DataSet> (`ds`) Ve tablo (`0` ve `1`) önceden oluşturulmuş.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Çalışma zamanında kullanabileceğiniz <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> bağlamak için yöntemi <xref:System.Windows.Forms.DataGrid> denetimi için farklı bir veri kaynağı. Örneğin, birkaç olabilir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] veri denetimleri, her bağlı için farklı bir veritabanı.  
  
### <a name="to-change-the-datasource-programmatically"></a>Veri kaynağında programlı olarak değiştirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi bağlamak için istediğiniz tabloyu ve veri kaynağı adı.  
  
     Aşağıdaki örnekte, tarih kullanarak kaynak değiştirmeye gösterilmektedir <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yönteme bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Pubs veritabanı yazarlar tablosuna bağlanmış veri denetimi (adoPubsAuthors).  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Veri Kümeleri](../../data/adonet/ado-net-datasets.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
