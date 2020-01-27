---
title: DataGrid denetiminde çalışma zamanında görünen verileri değiştirme
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740593"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Tasarım zamanı özelliklerini kullanarak bir Windows Forms <xref:System.Windows.Forms.DataGrid> oluşturduktan sonra, çalışma zamanında kılavuzun <xref:System.Data.DataSet> nesnesinin öğelerini dinamik olarak değiştirmek de isteyebilirsiniz. Bu, tablodaki tek tek değerler veya <xref:System.Windows.Forms.DataGrid> denetimine hangi veri kaynağının bağlandığını değiştirme gibi değişiklikler içerebilir. Tek tek değerlerde yapılan değişiklikler <xref:System.Windows.Forms.DataGrid> denetiminden değil <xref:System.Data.DataSet> nesnesi aracılığıyla yapılır.  
  
### <a name="to-change-data-programmatically"></a>Verileri program aracılığıyla değiştirmek için  
  
1. <xref:System.Data.DataSet> nesnesinden istenen tabloyu ve tablodaki istenen satırı ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.  
  
    > [!NOTE]
    > <xref:System.Data.DataSet> ilk tablosunu veya tablonun ilk satırını belirtmek için 0 kullanın.  
  
     Aşağıdaki örnek, `Button1`' ye tıklayarak bir veri kümesinin ilk satırının ilk satırının ikinci girişinin nasıl değiştirileceğini gösterir. <xref:System.Data.DataSet> (`ds`) ve tablolar (`0` ve `1`) önceden oluşturulmuştur.  
  
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
  
     Çalışma zamanında, <xref:System.Windows.Forms.DataGrid> denetimini farklı bir veri kaynağına bağlamak için <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanabilirsiniz. Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetimine sahip olabilirsiniz.  
  
### <a name="to-change-the-datasource-programmatically"></a>Veri kaynağını program aracılığıyla değiştirmek için  
  
1. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini, bağlamak istediğiniz veri kaynağı ve tablonun adı olarak ayarlayın.  
  
     Aşağıdaki örnek, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanarak, pubs veritabanındaki yazarlar tablosuna bağlanan bir ADO.NET veri denetimine (adoPubsAuthors) göre tarih kaynağının nasıl değiştirileceğini gösterir.  
  
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
