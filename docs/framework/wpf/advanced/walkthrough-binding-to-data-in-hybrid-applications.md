---
title: 'İzlenecek yol: Karma Uygulamalarda Veriye Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: f6fd1f2f5d0a729ee5610b81d4bfdca052a6e01e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300872"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="ba2a9-102">İzlenecek yol: Karma Uygulamalarda Veriye Bağlama</span><span class="sxs-lookup"><span data-stu-id="ba2a9-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="ba2a9-103">Bir veri kaynağı bir denetime bağlama olup, temel alınan verilere erişimi olan kullanıcılar sağlamak için gerekli kullanmakta olduğunuz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba2a9-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="ba2a9-104">Bu izlenecek yol, veri bağlama iki dahil karma uygulamalarda nasıl kullanabileceğinizi gösterir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="ba2a9-105">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ba2a9-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ba2a9-106">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="ba2a9-107">Veri şablonu tanımlama.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="ba2a9-108">Form düzenini belirtme.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="ba2a9-109">Veri bağlamaları belirtme.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="ba2a9-110">Birlikte çalışması kullanarak veri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="ba2a9-111">Veri kaynağı projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="ba2a9-112">Veri kaynağına bağlama.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="ba2a9-113">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [karma uygulamalar için örnek veri bağlama](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="ba2a9-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="ba2a9-114">İşlemi tamamladığınızda, karma uygulamalarda veri bağlama özellikleri bir anlayışa sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba2a9-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ba2a9-115">Prerequisites</span></span>  
 <span data-ttu-id="ba2a9-116">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="ba2a9-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="ba2a9-117">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-117">Visual Studio.</span></span>  
  
-   <span data-ttu-id="ba2a9-118">Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ba2a9-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba2a9-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="ba2a9-120">Oluşturma ve projesi kurun</span><span class="sxs-lookup"><span data-stu-id="ba2a9-120">To create and set up the project</span></span>  
  
1. <span data-ttu-id="ba2a9-121">Adlı bir WPF uygulaması projesi oluşturmak `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2. <span data-ttu-id="ba2a9-122">Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="ba2a9-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="ba2a9-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="ba2a9-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="ba2a9-124">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="ba2a9-125">İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba2a9-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="ba2a9-126">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanlarını eşleme.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="ba2a9-127">Varsayılan ad <xref:System.Windows.Controls.Grid> öğesi `mainGrid` atayarak <xref:System.Windows.FrameworkElement.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="ba2a9-128">Veri şablonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="ba2a9-128">Defining the Data Template</span></span>  
 <span data-ttu-id="ba2a9-129">Müşteriler ana listesinde görüntülenen bir <xref:System.Windows.Controls.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="ba2a9-130">Aşağıdaki kod örneği tanımlayan bir <xref:System.Windows.DataTemplate> adlı nesne `ListItemsTemplate` görsel ağacını denetimleri <xref:System.Windows.Controls.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="ba2a9-131">Bu <xref:System.Windows.DataTemplate> atandığı <xref:System.Windows.Controls.ListBox> denetimin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="ba2a9-132">Veri şablonu tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-132">To define the data template</span></span>  
  
-   <span data-ttu-id="ba2a9-133">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="ba2a9-134">Form düzenini belirtme</span><span class="sxs-lookup"><span data-stu-id="ba2a9-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="ba2a9-135">Formun yerleşimini üç satır ve üç sütun içeren bir kılavuz olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="ba2a9-136"><xref:System.Windows.Controls.Label> denetimleri Müşteriler tablosundaki her bir sütunu tanımlamak için sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="ba2a9-137">Kılavuz düzeni'kurmak için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="ba2a9-138">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="ba2a9-139">Etiket denetimleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="ba2a9-140">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="ba2a9-141">Veri bağlama belirtme</span><span class="sxs-lookup"><span data-stu-id="ba2a9-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="ba2a9-142">Müşteriler ana listesinde görüntülenen bir <xref:System.Windows.Controls.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="ba2a9-143">Ekli `ListItemsTemplate` bağlayan bir <xref:System.Windows.Controls.TextBlock> denetimini `ContactName` veritabanından alan.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="ba2a9-144">Her müşteri kaydın ayrıntılarını çeşitli görüntülenen <xref:System.Windows.Controls.TextBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="ba2a9-145">Veri bağlamaları belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="ba2a9-146">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="ba2a9-147"><xref:System.Windows.Data.Binding> Sınıfı bağlamalar <xref:System.Windows.Controls.TextBox> veritabanında uygun alanlara denetimleri.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="ba2a9-148">Birlikte çalışması kullanarak verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ba2a9-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="ba2a9-149">İse seçili müşterilerle ilgili Siparişler görüntülenen bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="ba2a9-150">`dataGridView1` Denetim arka plan kod dosyası veri kaynağına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="ba2a9-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimidir bu üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="ba2a9-152">DataGridView denetiminde verileri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="ba2a9-153">İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="ba2a9-154">Veri kaynağı projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="ba2a9-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="ba2a9-155">Visual Studio ile kolayca projenize bir veri kaynağı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="ba2a9-156">Bu yordam, kesin türü belirtilmiş veri kümesi projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="ba2a9-157">Seçilen tabloların her biri için tablo bağdaştırıcıları gibi diğer destek sınıfları da eklenir.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="ba2a9-158">Veri kaynağı eklemek için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-158">To add the data source</span></span>  
  
1. <span data-ttu-id="ba2a9-159">Gelen **veri** menüsünde **yeni veri kaynağı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2. <span data-ttu-id="ba2a9-160">İçinde **veri kaynağı Yapılandırma Sihirbazı**, bir veri kümesini kullanarak Northwind veritabanına bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="ba2a9-161">Daha fazla bilgi için [nasıl yapılır: Bir veritabanındaki verilere bağlanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="ba2a9-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>  
  
3. <span data-ttu-id="ba2a9-162">Tarafından istendiğinde **veri kaynağı Yapılandırma Sihirbazı**, bağlantı dizesi olarak Kaydet `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4. <span data-ttu-id="ba2a9-163">Veritabanı nesnelerinizi seçin. sorulduğunda `Customers` ve `Orders` tabloları ve oluşturulan veri kümesi adı `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="ba2a9-164">Veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="ba2a9-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="ba2a9-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Bileşeni, uygulamanın veri kaynağı için tek tip arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="ba2a9-166">Veri kaynağına bağlama arka plan kod dosyasında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="ba2a9-167">Veri kaynağına bağlamak için</span><span class="sxs-lookup"><span data-stu-id="ba2a9-167">To bind to the data source</span></span>  
  
1. <span data-ttu-id="ba2a9-168">MainWindow.xaml.vb veya MainWindow.xaml.cs adlı arka plan kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="ba2a9-169">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="ba2a9-170">Bu kod bildirir <xref:System.Windows.Forms.BindingSource> bileşeni ve veritabanı'na bağlanma ilişkili yardımcı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="ba2a9-171">Aşağıdaki kod oluşturucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="ba2a9-172">Bu kod oluşturur ve başlatır <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="ba2a9-173">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="ba2a9-174">Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="ba2a9-175">Özellikler penceresinde tıklayın **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="ba2a9-176">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="ba2a9-177">Aşağıdaki kodu kopyalayın <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="ba2a9-178">Bu kod atar <xref:System.Windows.Forms.BindingSource> veri bağlamı olarak bileşen ve dolduran `Customers` ve `Orders` bağdaştırıcısı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="ba2a9-179">Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="ba2a9-180">Bu yöntem işleme <xref:System.Windows.Data.CollectionView.CurrentChanged> olay ve geçerli veri bağlama öğesini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="ba2a9-181">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2a9-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba2a9-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ba2a9-183">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="ba2a9-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="ba2a9-184">Veri bağlama karma uygulamaları örneği</span><span class="sxs-lookup"><span data-stu-id="ba2a9-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)
- [<span data-ttu-id="ba2a9-185">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="ba2a9-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="ba2a9-186">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="ba2a9-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
