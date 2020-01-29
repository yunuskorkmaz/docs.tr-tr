---
title: DataGrid denetimiyle ana ayrıntı listeleri oluşturma
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
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730986"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Data.DataSet> bir dizi ilişkili tablo içeriyorsa, verileri bir ana/ayrıntı biçiminde göstermek için iki <xref:System.Windows.Forms.DataGrid> denetimi kullanabilirsiniz. Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir. Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir. Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve siparişler tablosunun ayrıntılar kılavuzu olacak şekilde belirtirsiniz. Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Programlı olarak ana/ayrıntılı ilişki ayarlamak için  
  
1. İki yeni <xref:System.Windows.Forms.DataGrid> denetimi oluşturun ve özelliklerini ayarlayın.  
  
2. Veri kümesine tablo ekleyin.  
  
3. Oluşturmak istediğiniz ilişkiyi göstermek için <xref:System.Data.DataRelation> türünde bir değişken bildirin.  
  
4. İlişki için bir ad belirterek ve iki tabloyu barındıracak tablo, sütun ve öğeyi belirterek ilişkiyi oluşturun.  
  
5. İlişkiyi <xref:System.Data.DataSet> nesnesinin <xref:System.Data.DataSet.Relations%2A> koleksiyonuna ekleyin.  
  
6. Kılavuzların her birini <xref:System.Data.DataSet>bağlamak için <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanın.  
  
     Aşağıdaki örnek, daha önce oluşturulan <xref:System.Data.DataSet> (`ds`) müşteriler ve siparişler tabloları arasında bir ana/ayrıntı ilişkisinin nasıl ayarlanacağını gösterir.  
  
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

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
