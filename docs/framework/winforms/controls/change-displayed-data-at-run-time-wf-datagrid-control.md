---
title: DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142387"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur. Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
  
 Tasarım zamanı özelliklerini kullanarak <xref:System.Windows.Forms.DataGrid> bir Windows Forms oluşturduktan sonra, çalışma zamanında ızgara <xref:System.Data.DataSet> nesnesinin öğelerini dinamik olarak değiştirmek de isteyebilirsiniz. Bu, tablonun tek tek değerlerinde yapılan değişiklikleri veya denetime <xref:System.Windows.Forms.DataGrid> bağlı hangi veri kaynağının değiştirini içerebilir. Tek tek değerlerdeki değişiklikler <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> denetim üzerinden değil, nesne aracılığıyla yapılır.  
  
### <a name="to-change-data-programmatically"></a>Verileri programlı olarak değiştirmek için  
  
1. Nesneden istenen tabloyu <xref:System.Data.DataSet> ve tablodan istenen satır ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.  
  
    > [!NOTE]
    > Tablonun ilk tablosunu <xref:System.Data.DataSet> veya ilk satırını belirtmek için 0'ı kullanın.  
  
     Aşağıdaki örnekte, bir veri kümesinin ilk tablosunun ilk satırının ikinci `Button1`girişinin nasıl değiştirilen i' yi tıklatarak nasıl değiştirilen bir . ( <xref:System.Data.DataSet> `ds`) ve`0` Tablolar `1`( ve ) daha önce oluşturulmuştur.  
  
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
  
     (Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid> denetimi farklı bir veri kaynağına bağlamak için yöntemi kullanabilirsiniz. Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetiminiz olabilir.  
  
### <a name="to-change-the-datasource-programmatically"></a>DataSource'u programlı olarak değiştirmek için  
  
1. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Yöntemi bağlamak istediğiniz veri kaynağı nın ve tablonun adına ayarlayın.  
  
     Aşağıdaki örnek, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntem kullanarak tarih kaynağının Pubs veritabanındaki Yazarlar tablosuna bağlı ADO.NET veri denetimi (adoPubsAuthors) olarak nasıl değiştirilebildiğini gösterir.  
  
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
