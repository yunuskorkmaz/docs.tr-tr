---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: a7b03ab5417eacf7962f2a05b674ceb45c7d558c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115738"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="9180b-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="9180b-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="9180b-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="9180b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9180b-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9180b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9180b-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetim bir veri kaynağından bilgileri görüntülemek için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9180b-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="9180b-106">Ayarlayarak tasarım zamanında denetimi bağlama <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri veya çağırarak çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9180b-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="9180b-107">Çeşitli veri kaynaklarından verileri görüntüleyebilse de, en sık karşılaşılan veri kümeleri ve veri görünümleri kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="9180b-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="9180b-108">Tasarım zamanında veri kaynağının kullanılabilir olup olmadığını — Örneğin, bir veri kümesi veya bir veri görünümü örneği formu içeren — veri kaynağına kılavuz tasarım zamanında bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9180b-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="9180b-109">Sonra veri kılavuzunda nasıl görüneceğini önizlemesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9180b-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="9180b-110">Bu kılavuz ayrıca programlı olarak ve çalışma zamanında bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9180b-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="9180b-111">Çalışma zamanında alma bilgilere dayanarak bir veri kaynağı istediğinizde bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9180b-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="9180b-112">Örneğin, uygulamayı görüntülemek için bir tablonun adını belirttiğiniz kullanıcı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9180b-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="9180b-113">Gerekli durumlarda tasarım zamanında burada veri kaynağı yok.</span><span class="sxs-lookup"><span data-stu-id="9180b-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="9180b-114">Bu, diziler, koleksiyonlar, yazılmayan veri kümeleri ve veri okuyucu gibi veri kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="9180b-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="9180b-115">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGrid> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9180b-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="9180b-116">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9180b-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="9180b-117">Visual Studio 2005 ' te <xref:System.Windows.Forms.DataGrid> denetimi içinde değil **araç kutusu** varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="9180b-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="9180b-118">Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Araç kutusu öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9180b-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="9180b-119">Visual Studio 2005'te, ayrıca kullandığınız **veri kaynakları** penceresi tasarım zamanı veri bağlama için.</span><span class="sxs-lookup"><span data-stu-id="9180b-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="9180b-120">Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9180b-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9180b-121">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9180b-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9180b-122">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9180b-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9180b-123">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9180b-123">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="9180b-124">Veri DataGrid denetimi Tasarımcısı'nda tek bir tabloya bağlama için</span><span class="sxs-lookup"><span data-stu-id="9180b-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="9180b-125">Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="9180b-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="9180b-126">Veri kaynağı bir veri kümesi ise <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini bağlanacak tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="9180b-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="9180b-127">Veri kaynağı bir veri kümesi veya bir veri kümesi tabloyu temel alan bir veri görünümü, forma DataSet'i doldurmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9180b-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="9180b-128">Kullandığınız tam kod burada veri veri kümesi alma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9180b-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="9180b-129">Veri kümesi doğrudan bir veritabanından doldurulmuş, genellikle arama `Fill` adlı bir veri kümesi doldurur aşağıdaki kod örneğinde olduğu gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="9180b-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="9180b-130">(İsteğe bağlı) Sütun stillerini ve uygun tablo stilleri kılavuza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9180b-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="9180b-131">Hiçbir tablo stilleri varsa, bir tablo görürsünüz ancak en az biçimlendirme ile tüm sütunlar görünür.</span><span class="sxs-lookup"><span data-stu-id="9180b-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="9180b-132">Veri DataGrid denetimi için bir veri kümesi Tasarımcısı'nda birden çok tablodan bağlamak için</span><span class="sxs-lookup"><span data-stu-id="9180b-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="9180b-133">Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="9180b-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="9180b-134">Veri kümesi, ilişkili tabloları içeriyorsa (diğer bir deyişle, bir ilişki nesnesi içeriyorsa) ayarlayın <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini üst tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="9180b-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="9180b-135">DataSet'i doldurmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="9180b-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9180b-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9180b-136">See also</span></span>

- [<span data-ttu-id="9180b-137">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9180b-137">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="9180b-138">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="9180b-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="9180b-139">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="9180b-139">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="9180b-140">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="9180b-140">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="9180b-141">Visual Studio'da verilere erişme</span><span class="sxs-lookup"><span data-stu-id="9180b-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
