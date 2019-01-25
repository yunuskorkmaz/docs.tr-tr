---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimi ile ana öğe-ayrıntı listeleri oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: 6ff13264709c4557d698435ac05b7759be58f1e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712898"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid denetimi ile ana/ayrıntı listeleri oluşturma
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Varsa, <xref:System.Data.DataSet> içeren bir dizi ilgili tabloları, iki kullanabilirsiniz <xref:System.Windows.Forms.DataGrid> ana/ayrıntı biçiminde verileri görüntülemek için denetimler. Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak atanan ve ikinci ayrıntıları kılavuz olarak atanır. Ana listesinde bir girişi seçtiğinizde, tüm ilgili alt girişlerinin Ayrıntılar listesinde gösterilir. Örneğin, varsa, <xref:System.Data.DataSet> Müşteriler tablosu ile ilgili bir sipariş tablonuz içeren ana kılavuz olmasını Customers ve Orders tablosunu ayrıntıları kılavuz olarak belirtmeniz gerekir. Ana grid'den gelen bir müşteri seçildiğinde, Northwind'deki Siparişler tablosunda, müşteriyle ilgili Siparişler tüm ayrıntılar kılavuzunda görüntülenmekteydi.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Ana/ayrıntı ilişkisi program üzerinden ayarlamak için  
  
1.  İki yeni oluşturma <xref:System.Windows.Forms.DataGrid> denetler ve özelliklerini ayarlayın.  
  
2.  Tablolar, veri kümesine ekleyin.  
  
3.  Türünde bir değişken bildirmek <xref:System.Data.DataRelation> oluşturmak istediğiniz ilişkiyi göstermek üzere.  
  
4.  İlişki için bir ad belirterek ve tablo, sütun ve iki tablo tie öğesi belirterek ilişki örneği.  
  
5.  İlişki Ekle <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Relations%2A> koleksiyonu.  
  
6.  Kullanım <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi <xref:System.Windows.Forms.DataGrid> her kılavuzların bağlamak için <xref:System.Data.DataSet>.  
  
     Aşağıdaki örnek, daha önce oluşturulan, müşteriler ve Siparişler tablolarını arasında ana/ayrıntı ilişkisi gösterilmektedir <xref:System.Data.DataSet> (`ds`).  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [DataGrid Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
