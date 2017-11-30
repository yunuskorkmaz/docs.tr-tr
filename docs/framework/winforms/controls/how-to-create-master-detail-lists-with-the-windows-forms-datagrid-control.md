---
title: "Nasıl yapılır: Windows Forms DataGrid denetimi ile ana / ayrıntı listeleri oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cb647e2ed6dcbc97fab15db3166b55c52f635a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="d6cc4-102">Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6cc4-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="d6cc4-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="d6cc4-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d6cc4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="d6cc4-105">Varsa, <xref:System.Data.DataSet> bir dizi içerir ilgili tabloları, iki kullanabilirsiniz <xref:System.Windows.Forms.DataGrid> verileri ana/ayrıntı biçimde görüntülemek için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="d6cc4-106">Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak atanan ve ikinci ayrıntıları kılavuz olarak atanan.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="d6cc4-107">Ana listesinde bir girişi seçtiğinizde, tüm ilgili alt girdilerini ayrıntıları listesinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="d6cc4-108">Örneğin, varsa, <xref:System.Data.DataSet> Müşteriler tablosu ile ilgili Siparişler tablosu içeren ana kılavuz olarak Müşteriler tablosu ve ayrıntıları kılavuz olarak Siparişler tablosundaki belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="d6cc4-109">Bir müşteri Ana kılavuzdan seçildiğinde, o müşteri Siparişler tablosundaki ilişkili siparişleri tümünün Ayrıntılar kılavuzunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="d6cc4-110">Ana/ayrıntı ilişkisi programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6cc4-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="d6cc4-111">İki yeni oluşturmak <xref:System.Windows.Forms.DataGrid> denetler ve bunların özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="d6cc4-112">Tabloları kümesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="d6cc4-113">Türünde bir değişken bildirme <xref:System.Data.DataRelation> oluşturmak istiyorsanız ilişki temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="d6cc4-114">İlişki için bir ad belirtmek ve tablo, sütun ve iki tablo tie öğesi belirterek ilişki örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="d6cc4-115">İlişkinin eklemek <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Relations%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="d6cc4-116">Kullanım <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi <xref:System.Windows.Forms.DataGrid> her biri için kılavuzları bağlamak için <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="d6cc4-117">Aşağıdaki örnek, müşteriler ve siparişler tablolar arasında daha önce oluşturulan bir ana öğe/ayrıntı ilişkisi gösterilmiştir <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="d6cc4-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6cc4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6cc4-118">See Also</span></span>  
 [<span data-ttu-id="d6cc4-119">DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="d6cc4-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="d6cc4-120">DataGrid denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="d6cc4-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="d6cc4-121">Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="d6cc4-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
