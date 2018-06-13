---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimi ile ana / ayrıntı listeleri oluşturma'
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
ms.openlocfilehash: 528d07b766987bdeca22ce480c601a2bdd324c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531124"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Varsa, <xref:System.Data.DataSet> bir dizi içerir ilgili tabloları, iki kullanabilirsiniz <xref:System.Windows.Forms.DataGrid> verileri ana/ayrıntı biçimde görüntülemek için kontrol eder. Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak atanan ve ikinci ayrıntıları kılavuz olarak atanan. Ana listesinde bir girişi seçtiğinizde, tüm ilgili alt girdilerini ayrıntıları listesinde gösterilir. Örneğin, varsa, <xref:System.Data.DataSet> Müşteriler tablosu ile ilgili Siparişler tablosu içeren ana kılavuz olarak Müşteriler tablosu ve ayrıntıları kılavuz olarak Siparişler tablosundaki belirtmeniz gerekir. Bir müşteri Ana kılavuzdan seçildiğinde, o müşteri Siparişler tablosundaki ilişkili siparişleri tümünün Ayrıntılar kılavuzunda görüntülenir.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Ana/ayrıntı ilişkisi programlı olarak ayarlamak için  
  
1.  İki yeni oluşturmak <xref:System.Windows.Forms.DataGrid> denetler ve bunların özelliklerini ayarlayın.  
  
2.  Tabloları kümesine ekleyin.  
  
3.  Türünde bir değişken bildirme <xref:System.Data.DataRelation> oluşturmak istiyorsanız ilişki temsil etmek için.  
  
4.  İlişki için bir ad belirtmek ve tablo, sütun ve iki tablo tie öğesi belirterek ilişki örneği oluşturur.  
  
5.  İlişkinin eklemek <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Relations%2A> koleksiyonu.  
  
6.  Kullanım <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi <xref:System.Windows.Forms.DataGrid> her biri için kılavuzları bağlamak için <xref:System.Data.DataSet>.  
  
     Aşağıdaki örnek, müşteriler ve siparişler tablolar arasında daha önce oluşturulan bir ana öğe/ayrıntı ilişkisi gösterilmiştir <xref:System.Data.DataSet> (`ds`).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
