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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917721"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Tasarım zamanı özelliklerini kullanarak bir Windows Forms <xref:System.Windows.Forms.DataGrid> oluşturduktan sonra, çalışma zamanında kılavuzun <xref:System.Data.DataSet> nesne öğelerini dinamik olarak değiştirmek de isteyebilirsiniz. Bu, tablonun tek tek değerlerine yapılan değişiklikleri veya <xref:System.Windows.Forms.DataGrid> denetime hangi veri kaynağının bağlandığını değiştirmek içerebilir. Tek tek değerlerde yapılan değişiklikler, <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> denetim değil, nesnesi aracılığıyla yapılır.  
  
### <a name="to-change-data-programmatically"></a>Verileri program aracılığıyla değiştirmek için  
  
1. <xref:System.Data.DataSet> Nesneden istenen tabloyu ve tablodaki istenen satırı ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.  
  
    > [!NOTE]
    > Tablonun ilk tablosunu <xref:System.Data.DataSet> veya ilk satırını belirtmek için 0 kullanın.  
  
     Aşağıdaki örnek, öğesine tıklayarak `Button1`bir veri kümesinin ilk tablosunun ilk satırının ikinci girişinin nasıl değiştirileceğini gösterir. () Ve`0` tabloları (ve `1`) daha önce oluşturulmuştur.`ds` <xref:System.Data.DataSet>  
  
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
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Çalışma zamanında, <xref:System.Windows.Forms.DataGrid> denetimi farklı bir veri <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> kaynağına bağlamak için yöntemini kullanabilirsiniz. Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetimine sahip olabilirsiniz.  
  
### <a name="to-change-the-datasource-programmatically"></a>Veri kaynağını program aracılığıyla değiştirmek için  
  
1. Yöntemini, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> bağlamak istediğiniz veri kaynağı ve tablo adına ayarlayın.  
  
     Aşağıdaki örnek, pubs veritabanındaki yazarlar tablosuna bağlı olan ADO.NET veri denetimine <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (adopubsauthors) yöntemi kullanılarak tarih kaynağının nasıl değiştirileceğini gösterir.  
  
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
- [Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
