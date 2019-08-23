---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimiyle ana ayrıntı listeleri oluşturma'
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
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914758"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Bir dizi ilişkili tablo <xref:System.Windows.Forms.DataGrid> içeriyorsa,verileriana/ayrıntıbiçimindegöstermekiçinikidenetimkullanabilirsiniz.<xref:System.Data.DataSet> Biri <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir. Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir. Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve Siparişler tablosu olarak ayrıntılar kılavuzu olacak şekilde belirtirsiniz. Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Programlı olarak ana/ayrıntılı ilişki ayarlamak için  
  
1. İki yeni <xref:System.Windows.Forms.DataGrid> denetim oluşturun ve özelliklerini ayarlayın.  
  
2. Veri kümesine tablo ekleyin.  
  
3. Oluşturmak istediğiniz ilişkiyi temsil etmek <xref:System.Data.DataRelation> için türünde bir değişken bildirin.  
  
4. İlişki için bir ad belirterek ve iki tabloyu barındıracak tablo, sütun ve öğeyi belirterek ilişkiyi oluşturun.  
  
5. <xref:System.Data.DataSet> İlişkiyi<xref:System.Data.DataSet.Relations%2A> nesnenin koleksiyonuna ekleyin.  
  
6. Izgaraların her birini öğesine <xref:System.Windows.Forms.DataGrid> bağlamak için <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanın <xref:System.Data.DataSet>.  
  
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
- [Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
