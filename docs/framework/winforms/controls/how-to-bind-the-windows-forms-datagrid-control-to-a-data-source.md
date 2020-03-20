---
title: DataGrid Denetimini Veri Kaynağına Bağlama
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
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182250"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="40b28-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="40b28-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="40b28-103">Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="40b28-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="40b28-104">Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)</span><span class="sxs-lookup"><span data-stu-id="40b28-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="40b28-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından gelen bilgileri görüntülemek için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="40b28-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="40b28-106"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Yöntemi arayarak denetimi çalışma zamanında bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="40b28-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="40b28-107">Çeşitli veri kaynaklarından veri görüntüleyebiliyor olsanız da, en tipik kaynaklar veri kümeleri ve veri görünümleridir.</span><span class="sxs-lookup"><span data-stu-id="40b28-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="40b28-108">DataGrid denetimini programlı olarak bağlamak için</span><span class="sxs-lookup"><span data-stu-id="40b28-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="40b28-109">Veri kümesini doldurmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="40b28-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="40b28-110">Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünümüyse, veri kümesini doldurmak için forma kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="40b28-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="40b28-111">Tam kullandığınız kod, veri kümesinin verileri nereden aldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40b28-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="40b28-112">Veri kümesi doğrudan bir veritabanından dolduruluyorsa, aşağıdaki `Fill` örnekte olduğu gibi genellikle bir veri bağdaştırıcısı `DsCategories1`yöntemini çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="40b28-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="40b28-113">Veri kümesi bir XML Web hizmetinden dolduruluyorsa, genellikle kodunuzdaki hizmetin bir örneğini oluşturur ve ardından veri kümesini döndürmek için yöntemlerinden birini ararsınız.</span><span class="sxs-lookup"><span data-stu-id="40b28-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="40b28-114">Ardından XML Web hizmetindeki veri kümesini yerel veri kümenizle birleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40b28-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="40b28-115">Aşağıdaki örnek, xml Web hizmetinin `CategoriesService`bir örneğini nasıl `GetCategories` oluşturabileceğinizi gösterir, yöntemini çağırın ve `DsCategories1`elde edilen veri kümesini aşağıdaki gibi yerel bir veri kümesiyle birleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40b28-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="40b28-116">Denetimin <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırın, veri kaynağını ve veri üyesini geçirin.</span><span class="sxs-lookup"><span data-stu-id="40b28-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="40b28-117">Bir veri üyesini açıkça geçirmeniz gerekmiyorsa, boş bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="40b28-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40b28-118">Izgarayı ilk kez bağlıyorsanız, denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40b28-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="40b28-119">Ancak, bu özellikleri ayarlandıktan sonra sıfırlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="40b28-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="40b28-120">Bu nedenle, her zaman <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="40b28-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="40b28-121">Aşağıdaki örnek, aşağıdaki adlı `DsCustomers1`bir veri kümesinde Müşteriler tablosuna nasıl programlı olarak bağlanabileceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="40b28-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="40b28-122">Müşteriler tablosu veri kümesindeki tek tabloysa, ızgarayı alternatif olarak şu şekilde bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40b28-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="40b28-123">(İsteğe bağlı) Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="40b28-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="40b28-124">Tablo stilleri yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ve tüm sütunlar görünür.</span><span class="sxs-lookup"><span data-stu-id="40b28-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b28-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40b28-125">See also</span></span>

- [<span data-ttu-id="40b28-126">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="40b28-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="40b28-127">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="40b28-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="40b28-128">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="40b28-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="40b28-129">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="40b28-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
