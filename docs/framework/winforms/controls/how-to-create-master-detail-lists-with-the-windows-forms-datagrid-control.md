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
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="42aff-102">Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42aff-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="42aff-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="42aff-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="42aff-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="42aff-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="42aff-105"><xref:System.Data.DataSet> bir dizi ilişkili tablo içeriyorsa, verileri bir ana/ayrıntı biçiminde göstermek için iki <xref:System.Windows.Forms.DataGrid> denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42aff-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="42aff-106">Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="42aff-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="42aff-107">Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="42aff-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="42aff-108">Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve siparişler tablosunun ayrıntılar kılavuzu olacak şekilde belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42aff-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="42aff-109">Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="42aff-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="42aff-110">Programlı olarak ana/ayrıntılı ilişki ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="42aff-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="42aff-111">İki yeni <xref:System.Windows.Forms.DataGrid> denetimi oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="42aff-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="42aff-112">Veri kümesine tablo ekleyin.</span><span class="sxs-lookup"><span data-stu-id="42aff-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="42aff-113">Oluşturmak istediğiniz ilişkiyi göstermek için <xref:System.Data.DataRelation> türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="42aff-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="42aff-114">İlişki için bir ad belirterek ve iki tabloyu barındıracak tablo, sütun ve öğeyi belirterek ilişkiyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42aff-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="42aff-115">İlişkiyi <xref:System.Data.DataSet> nesnesinin <xref:System.Data.DataSet.Relations%2A> koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="42aff-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="42aff-116">Kılavuzların her birini <xref:System.Data.DataSet>bağlamak için <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="42aff-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="42aff-117">Aşağıdaki örnek, daha önce oluşturulan <xref:System.Data.DataSet> (`ds`) müşteriler ve siparişler tabloları arasında bir ana/ayrıntı ilişkisinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42aff-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42aff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42aff-118">See also</span></span>

- [<span data-ttu-id="42aff-119">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="42aff-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="42aff-120">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42aff-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="42aff-121">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="42aff-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
