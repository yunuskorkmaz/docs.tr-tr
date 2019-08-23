---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922732"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="dcb28-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="dcb28-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="dcb28-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="dcb28-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="dcb28-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dcb28-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="dcb28-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dcb28-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="dcb28-106"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Yöntemi çağırarak denetimi çalışma zamanında bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="dcb28-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="dcb28-107">Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.</span><span class="sxs-lookup"><span data-stu-id="dcb28-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="dcb28-108">DataGrid denetimini programlama yoluyla veri bağlama</span><span class="sxs-lookup"><span data-stu-id="dcb28-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="dcb28-109">Veri kümesini dolduracak kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="dcb28-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="dcb28-110">Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dcb28-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="dcb28-111">Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dcb28-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="dcb28-112">Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle bir veri bağdaştırıcısının `Fill` yöntemini, aşağıdaki örnekte olduğu gibi, adlı `DsCategories1`bir veri kümesini dolduran şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dcb28-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="dcb28-113">Veri kümesi bir XML Web hizmetinden doldurulduysa, genellikle kodunuzda hizmetin bir örneğini oluşturun ve ardından bir veri kümesi döndürmek için yöntemlerinden birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dcb28-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="dcb28-114">Daha sonra veri kümesini XML Web hizmetinden yerel veri kümeniz ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcb28-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="dcb28-115">Aşağıdaki örnek, adlı `CategoriesService`bir XML Web hizmetinin örneğini nasıl oluşturabileceğiniz, `GetCategories` yöntemini çağırabilmeniz ve elde edilen veri kümesini adlı `DsCategories1`yerel bir veri kümesinde birleştirme işlemini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="dcb28-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <span data-ttu-id="dcb28-116"><xref:System.Windows.Forms.DataGrid> Denetiminyönteminiçağırın,verikaynağınıve<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> bir veri üyesini geçirerek.</span><span class="sxs-lookup"><span data-stu-id="dcb28-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="dcb28-117">Bir veri üyesini açıkça geçirmeniz gerekmiyorsa boş bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="dcb28-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dcb28-118">Kılavuzu ilk kez bağlıyorsanız, denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcb28-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="dcb28-119">Ancak, ayarlandıklarında bu özellikleri sıfırlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dcb28-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="dcb28-120">Bu nedenle, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi her zaman kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="dcb28-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="dcb28-121">Aşağıdaki örnek, adlı `DsCustomers1`bir veri kümesindeki Customers tablosuna programlı bir şekilde nasıl bağlayacağınız gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dcb28-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="dcb28-122">Veri kümesindeki tek tablo müşteriler tablosu ise bu şekilde kılavuza bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dcb28-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="dcb28-123">Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dcb28-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="dcb28-124">Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.</span><span class="sxs-lookup"><span data-stu-id="dcb28-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb28-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcb28-125">See also</span></span>

- [<span data-ttu-id="dcb28-126">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dcb28-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="dcb28-127">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="dcb28-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="dcb28-128">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="dcb28-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="dcb28-129">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="dcb28-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
