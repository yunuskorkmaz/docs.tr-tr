---
title: 'İzlenecek yol: Karma Uygulamalarda Veriye Bağlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8afe4732363ec61d73db13e9b190381cbd8f29d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="f66b4-102">İzlenecek yol: Karma Uygulamalarda Veriye Bağlama</span><span class="sxs-lookup"><span data-stu-id="f66b4-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="f66b4-103">Bir veri kaynağı bir denetime bağlama olup, arka plandaki verilere erişimi olan kullanıcılar sağlamak için temel kullanmakta olduğunuz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f66b4-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="f66b4-104">Bu kılavuzda her ikisini de içeren karma uygulamalarda veri bağlamasını nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f66b4-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="f66b4-105">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f66b4-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f66b4-106">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f66b4-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="f66b4-107">Veri şablonu tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f66b4-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="f66b4-108">Form düzenini belirtme.</span><span class="sxs-lookup"><span data-stu-id="f66b4-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="f66b4-109">Veri bağlamalarını belirtme.</span><span class="sxs-lookup"><span data-stu-id="f66b4-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="f66b4-110">Birlikte çalışabilirlik kullanarak verileri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="f66b4-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="f66b4-111">Veri kaynağı projesine ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="f66b4-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="f66b4-112">Veri kaynağına bağlama.</span><span class="sxs-lookup"><span data-stu-id="f66b4-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="f66b4-113">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [karma uygulamalar için örnek veri bağlamada](http://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="f66b4-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](http://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="f66b4-114">İşiniz bittiğinde, karma uygulamalarda veri bağlama özellikleri anlaşılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f66b4-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f66b4-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f66b4-115">Prerequisites</span></span>  
 <span data-ttu-id="f66b4-116">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="f66b4-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="f66b4-117">.</span><span class="sxs-lookup"><span data-stu-id="f66b4-117">.</span></span>  
  
-   <span data-ttu-id="f66b4-118">Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanı erişimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f66b4-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f66b4-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="f66b4-120">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f66b4-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="f66b4-121">Adlı bir WPF uygulaması projesi oluşturduğunuzda `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="f66b4-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="f66b4-122">Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f66b4-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="f66b4-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f66b4-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="f66b4-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f66b4-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="f66b4-125">MainWindow.xaml içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f66b4-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="f66b4-126">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanlarını eşleme.</span><span class="sxs-lookup"><span data-stu-id="f66b4-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="f66b4-127">Varsayılan ad <xref:System.Windows.Controls.Grid> öğesi `mainGrid` atayarak <xref:System.Windows.FrameworkElement.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f66b4-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="f66b4-128">Veri şablonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="f66b4-128">Defining the Data Template</span></span>  
 <span data-ttu-id="f66b4-129">Müşterilerin ana listesi görüntülenir bir <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="f66b4-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="f66b4-130">Aşağıdaki kod örneğinde tanımlayan bir <xref:System.Windows.DataTemplate> adlı nesne `ListItemsTemplate` görsel ağacını denetleyen <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="f66b4-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="f66b4-131">Bu <xref:System.Windows.DataTemplate> atandığı <xref:System.Windows.Controls.ListBox> denetimin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f66b4-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="f66b4-132">Veri şablonu tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="f66b4-132">To define the data template</span></span>  
  
-   <span data-ttu-id="f66b4-133">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="f66b4-134">Form düzenini belirtme</span><span class="sxs-lookup"><span data-stu-id="f66b4-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="f66b4-135">Form düzenini üç satır ve üç sütun içeren bir kılavuz olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f66b4-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="f66b4-136"><xref:System.Windows.Controls.Label> denetimleri, müşterilerin tablodaki her sütun tanımlamak için sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f66b4-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="f66b4-137">Kılavuz düzeni kurmak için</span><span class="sxs-lookup"><span data-stu-id="f66b4-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="f66b4-138">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="f66b4-139">Etiket denetimlerini kurmak için</span><span class="sxs-lookup"><span data-stu-id="f66b4-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="f66b4-140">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="f66b4-141">Veri bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="f66b4-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="f66b4-142">Müşterilerin ana listesi görüntülenir bir <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="f66b4-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="f66b4-143">Ekli `ListItemsTemplate` bağlar bir <xref:System.Windows.Controls.TextBlock> denetimini `ContactName` veritabanından alan.</span><span class="sxs-lookup"><span data-stu-id="f66b4-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="f66b4-144">Her bir müşteri kaydı ayrıntılarını birkaç içinde görüntülenen <xref:System.Windows.Controls.TextBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f66b4-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="f66b4-145">Veri bağlamalarını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="f66b4-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="f66b4-146">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="f66b4-147"><xref:System.Windows.Data.Binding> Sınıf bağlamalar <xref:System.Windows.Controls.TextBox> veritabanı uygun alanlara denetimleri.</span><span class="sxs-lookup"><span data-stu-id="f66b4-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="f66b4-148">Birlikte çalışabilirlik kullanarak verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f66b4-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="f66b4-149">Seçili müşteriye karşılık gelen siparişler görüntülenen bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f66b4-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="f66b4-150">`dataGridView1` Denetim arka plan kod dosyası içindeki veri kaynağına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f66b4-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="f66b4-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimidir bu üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="f66b4-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="f66b4-152">DataGridView denetiminde verileri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="f66b4-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="f66b4-153">Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="f66b4-154">Projeye veri kaynağı ekleme</span><span class="sxs-lookup"><span data-stu-id="f66b4-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="f66b4-155">Visual Studio ile bir veri kaynağı projenize kolayca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f66b4-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="f66b4-156">Bu yordam, kesin türü belirtilmiş veri kümesi projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="f66b4-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="f66b4-157">Seçilen tabloların her biri için tablo bağdaştırıcıları gibi diğer destek sınıfları de eklenir.</span><span class="sxs-lookup"><span data-stu-id="f66b4-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="f66b4-158">Veri kaynağı eklemek için</span><span class="sxs-lookup"><span data-stu-id="f66b4-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="f66b4-159">Gelen **veri** menüsünde, select **yeni veri kaynağı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f66b4-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="f66b4-160">İçinde **veri kaynağı Yapılandırma Sihirbazı**, bir veri kümesini kullanarak Northwind veritabanına bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f66b4-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="f66b4-161">Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span><span class="sxs-lookup"><span data-stu-id="f66b4-161">For more information, see [How to: Connect to Data in a Database](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="f66b4-162">Tarafından istendiğinde **veri kaynağı Yapılandırma Sihirbazı**, bağlantı dizesi olarak Kaydet `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="f66b4-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="f66b4-163">Veritabanı nesnelerinizi seçin istendiğinde seçin `Customers` ve `Orders` tablolar ve üretilen veri kümesi adı `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="f66b4-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="f66b4-164">Veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="f66b4-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="f66b4-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Bileşeni, uygulamanın veri kaynağı için Tekdüzen arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f66b4-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="f66b4-166">Veri kaynağına bağlama arka plan kod dosyasına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f66b4-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="f66b4-167">Veri kaynağına bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="f66b4-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="f66b4-168">MainWindow.xaml.vb veya MainWindow.xaml.cs adlı arka plan kodu dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f66b4-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="f66b4-169">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="f66b4-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="f66b4-170">Bu kod bildirir <xref:System.Windows.Forms.BindingSource> bileşeni ve veritabanına bağlanan ilişkili yardımcı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f66b4-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="f66b4-171">Aşağıdaki kod oluşturucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f66b4-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="f66b4-172">Bu kod oluşturur ve başlatır <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f66b4-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="f66b4-173">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="f66b4-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="f66b4-174">Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="f66b4-175">Özellikler penceresinde **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="f66b4-176">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="f66b4-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="f66b4-177">Aşağıdaki kodu kopyalayın <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f66b4-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="f66b4-178">Bu kodu atar <xref:System.Windows.Forms.BindingSource> veri bağlamı olarak bileşen ve doldurur `Customers` ve `Orders` bağdaştırıcısı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f66b4-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="f66b4-179">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="f66b4-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="f66b4-180">Bu yöntem işleme <xref:System.Windows.Data.CollectionView.CurrentChanged> olay ve veri bağlamanın geçerli öğesini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f66b4-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="f66b4-181">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f66b4-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66b4-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f66b4-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f66b4-183">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="f66b4-183">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="f66b4-184">Veri bağlama karma uygulamalar örneği</span><span class="sxs-lookup"><span data-stu-id="f66b4-184">Data Binding in Hybrid Applications Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="f66b4-185">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f66b4-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="f66b4-186">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="f66b4-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
