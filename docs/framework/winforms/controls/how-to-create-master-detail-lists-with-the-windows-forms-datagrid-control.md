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
ms.openlocfilehash: 92b4a7d9513ce0ec9b7c02f57c23fa4267fb26ad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302419"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="491bf-102">Nasıl yapılır: Windows Forms DataGrid Denetimi ile Ana/Ayrıntı Listeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="491bf-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="491bf-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="491bf-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="491bf-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="491bf-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="491bf-105">Varsa, <xref:System.Data.DataSet> içeren bir dizi ilgili tabloları, iki kullanabilirsiniz <xref:System.Windows.Forms.DataGrid> ana/ayrıntı biçiminde verileri görüntülemek için denetimler.</span><span class="sxs-lookup"><span data-stu-id="491bf-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="491bf-106">Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak atanan ve ikinci ayrıntıları kılavuz olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="491bf-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="491bf-107">Ana listesinde bir girişi seçtiğinizde, tüm ilgili alt girişlerinin Ayrıntılar listesinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="491bf-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="491bf-108">Örneğin, varsa, <xref:System.Data.DataSet> Müşteriler tablosu ile ilgili bir sipariş tablonuz içeren ana kılavuz olmasını Customers ve Orders tablosunu ayrıntıları kılavuz olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="491bf-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="491bf-109">Ana grid'den gelen bir müşteri seçildiğinde, Northwind'deki Siparişler tablosunda, müşteriyle ilgili Siparişler tüm ayrıntılar kılavuzunda görüntülenmekteydi.</span><span class="sxs-lookup"><span data-stu-id="491bf-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="491bf-110">Ana/ayrıntı ilişkisi program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="491bf-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="491bf-111">İki yeni oluşturma <xref:System.Windows.Forms.DataGrid> denetler ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="491bf-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="491bf-112">Tablolar, veri kümesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="491bf-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="491bf-113">Türünde bir değişken bildirmek <xref:System.Data.DataRelation> oluşturmak istediğiniz ilişkiyi göstermek üzere.</span><span class="sxs-lookup"><span data-stu-id="491bf-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="491bf-114">İlişki için bir ad belirterek ve tablo, sütun ve iki tablo tie öğesi belirterek ilişki örneği.</span><span class="sxs-lookup"><span data-stu-id="491bf-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="491bf-115">İlişki Ekle <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Relations%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="491bf-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="491bf-116">Kullanım <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi <xref:System.Windows.Forms.DataGrid> her kılavuzların bağlamak için <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="491bf-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="491bf-117">Aşağıdaki örnek, daha önce oluşturulan, müşteriler ve Siparişler tablolarını arasında ana/ayrıntı ilişkisi gösterilmektedir <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="491bf-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="491bf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="491bf-118">See also</span></span>

- [<span data-ttu-id="491bf-119">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="491bf-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="491bf-120">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="491bf-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="491bf-121">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="491bf-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
