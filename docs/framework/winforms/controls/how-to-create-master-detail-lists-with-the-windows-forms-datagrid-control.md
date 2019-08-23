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
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="11046-102">Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="11046-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="11046-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="11046-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="11046-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="11046-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="11046-105">Bir dizi ilişkili tablo <xref:System.Windows.Forms.DataGrid> içeriyorsa,verileriana/ayrıntıbiçimindegöstermekiçinikidenetimkullanabilirsiniz.<xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="11046-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="11046-106">Biri <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="11046-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="11046-107">Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="11046-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="11046-108">Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve Siparişler tablosu olarak ayrıntılar kılavuzu olacak şekilde belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11046-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="11046-109">Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="11046-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="11046-110">Programlı olarak ana/ayrıntılı ilişki ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="11046-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="11046-111">İki yeni <xref:System.Windows.Forms.DataGrid> denetim oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="11046-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="11046-112">Veri kümesine tablo ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11046-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="11046-113">Oluşturmak istediğiniz ilişkiyi temsil etmek <xref:System.Data.DataRelation> için türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="11046-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="11046-114">İlişki için bir ad belirterek ve iki tabloyu barındıracak tablo, sütun ve öğeyi belirterek ilişkiyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="11046-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="11046-115"><xref:System.Data.DataSet> İlişkiyi<xref:System.Data.DataSet.Relations%2A> nesnenin koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11046-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="11046-116">Izgaraların her birini öğesine <xref:System.Windows.Forms.DataGrid> bağlamak için <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanın <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="11046-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="11046-117">Aşağıdaki örnek, daha önce oluşturulan <xref:System.Data.DataSet> (`ds`) müşteriler ve siparişler tabloları arasında bir ana/ayrıntı ilişkisinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11046-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11046-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11046-118">See also</span></span>

- [<span data-ttu-id="11046-119">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="11046-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="11046-120">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11046-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="11046-121">Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="11046-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
