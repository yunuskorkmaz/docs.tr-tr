---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama'
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
ms.openlocfilehash: 5da74abb107bc93bff496a35ecfc7a1233e5a76d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702964"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="31ab3-102">Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="31ab3-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
>  <span data-ttu-id="31ab3-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="31ab3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="31ab3-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="31ab3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="31ab3-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetim bir veri kaynağından bilgileri görüntülemek için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31ab3-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="31ab3-106">Çağırarak denetimini çalışma zamanında bağlama <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31ab3-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="31ab3-107">Çeşitli veri kaynaklarından verileri görüntüleyebilse de, en sık karşılaşılan veri kümeleri ve veri görünümleri kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="31ab3-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="31ab3-108">DataGrid denetimi program aracılığıyla veri-bağlamak için</span><span class="sxs-lookup"><span data-stu-id="31ab3-108">To data-bind the DataGrid control programmatically</span></span>  
  
1.  <span data-ttu-id="31ab3-109">DataSet'i doldurmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="31ab3-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="31ab3-110">Veri kaynağı bir veri kümesi veya bir veri kümesi tabloyu temel alan bir veri görünümü, forma DataSet'i doldurmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31ab3-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="31ab3-111">Kullandığınız tam kod burada veri veri kümesi alma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="31ab3-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="31ab3-112">Veri kümesi doğrudan bir veritabanından doldurulmuş, genellikle arama `Fill` adlı bir veri kümesi doldurur aşağıdaki örnekte olduğu gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="31ab3-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="31ab3-113">Bir XML Web hizmetinden doldurulmuş veri kümesi, genellikle kodunuzda Hizmeti'nin bir örneğini oluşturur ve ardından bir veri kümesi döndürülecek yöntemlerinden birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="31ab3-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="31ab3-114">XML Web hizmetinden dataset sonra yerel kümenize birleştirin.</span><span class="sxs-lookup"><span data-stu-id="31ab3-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="31ab3-115">Aşağıdaki örnek, bir XML Web hizmeti olarak adlandırılan bir örneğini nasıl oluşturacağınızı gösterir. `CategoriesService`, arama, `GetCategories` yöntemi ve sonuç veri kümesini yerel bir veri kümesine adlı birleştirme `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="31ab3-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2.  <span data-ttu-id="31ab3-116">Çağrı <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi, veri kaynağı ve veri üyesi geçirme.</span><span class="sxs-lookup"><span data-stu-id="31ab3-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="31ab3-117">Veri üyesi açıkça geçirebilirsiniz ihtiyacınız yoksa boş bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="31ab3-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31ab3-118">Kılavuzun ilk kez bağlanıyorsanız, denetimin ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="31ab3-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="31ab3-119">Ancak, ayarlandıktan sonra bu özellikleri sıfırlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="31ab3-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="31ab3-120">Bu nedenle, her zaman kullanmanız önerilir <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31ab3-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="31ab3-121">Aşağıdaki örnek nasıl program aracılığıyla adlı bir veri kümesi Müşteriler tablosunda adlarınıza bağlayabileceğiniz gösterir `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="31ab3-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="31ab3-122">Müşteriler tablosu veri kümesi yalnızca tablodaki ise, kılavuz alternatif olarak bu şekilde bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31ab3-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  <span data-ttu-id="31ab3-123">(İsteğe bağlı) Sütun stillerini ve uygun tablo stilleri kılavuza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31ab3-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="31ab3-124">Hiçbir tablo stilleri varsa, bir tablo görürsünüz ancak en az biçimlendirme ile tüm sütunlar görünür.</span><span class="sxs-lookup"><span data-stu-id="31ab3-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ab3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31ab3-125">See also</span></span>
- [<span data-ttu-id="31ab3-126">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31ab3-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="31ab3-127">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="31ab3-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="31ab3-128">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="31ab3-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="31ab3-129">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="31ab3-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
