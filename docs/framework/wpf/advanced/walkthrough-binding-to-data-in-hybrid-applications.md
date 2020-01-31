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
ms.openlocfilehash: 1bb38436049e338ab6033ae3b6370732a457d520
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794217"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="1cbea-102">İzlenecek yol: Karma Uygulamalarda Veriye Bağlama</span><span class="sxs-lookup"><span data-stu-id="1cbea-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>

<span data-ttu-id="1cbea-103">Bir veri kaynağını denetime bağlama, kullanıcıların Windows Forms veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıp kullanmadığını temel verilere erişimi sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using Windows Forms or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="1cbea-104">Bu izlenecek yol, hem Windows Forms hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalarda veri bağlamayı nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-104">This walkthrough shows how you can use data binding in hybrid applications that include both Windows Forms and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>

<span data-ttu-id="1cbea-105">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1cbea-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="1cbea-106">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1cbea-106">Creating the project.</span></span>

- <span data-ttu-id="1cbea-107">Veri şablonunu tanımlama.</span><span class="sxs-lookup"><span data-stu-id="1cbea-107">Defining the data template.</span></span>

- <span data-ttu-id="1cbea-108">Form düzeni belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="1cbea-108">Specifying the form layout.</span></span>

- <span data-ttu-id="1cbea-109">Veri bağlamalarını belirtme.</span><span class="sxs-lookup"><span data-stu-id="1cbea-109">Specifying data bindings.</span></span>

- <span data-ttu-id="1cbea-110">Birlikte çalışabilirlik kullanarak verileri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="1cbea-110">Displaying data by using interoperation.</span></span>

- <span data-ttu-id="1cbea-111">Veri kaynağı projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="1cbea-111">Adding the data source to the project.</span></span>

- <span data-ttu-id="1cbea-112">Veri kaynağına bağlanıyor.</span><span class="sxs-lookup"><span data-stu-id="1cbea-112">Binding to the data source.</span></span>

<span data-ttu-id="1cbea-113">Bu izlenecek yolda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulamalar Için veri bağlama örneği](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="1cbea-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>

<span data-ttu-id="1cbea-114">İşiniz bittiğinde, karma uygulamalardaki veri bağlama özelliklerinin anlaşılmasına sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1cbea-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1cbea-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1cbea-115">Prerequisites</span></span>

<span data-ttu-id="1cbea-116">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="1cbea-116">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="1cbea-117">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1cbea-117">Visual Studio.</span></span>

- <span data-ttu-id="1cbea-118">Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="1cbea-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="1cbea-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cbea-119">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="1cbea-120">Projeyi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1cbea-120">To create and set up the project</span></span>

1. <span data-ttu-id="1cbea-121">`WPFWithWFAndDatabinding`adlı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1cbea-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>

2. <span data-ttu-id="1cbea-122">Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1cbea-122">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="1cbea-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="1cbea-123">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="1cbea-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="1cbea-124">System.Windows.Forms</span></span>

3. <span data-ttu-id="1cbea-125">WPF Tasarımcısında MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-125">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="1cbea-126"><xref:System.Windows.Window> öğesinde, aşağıdaki Windows Forms ad alanı eşlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1cbea-126">In the <xref:System.Windows.Window> element, add the following Windows Forms namespaces mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="1cbea-127"><xref:System.Windows.FrameworkElement.Name%2A> özelliğini atayarak varsayılan <xref:System.Windows.Controls.Grid> öğesi `mainGrid` adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a><span data-ttu-id="1cbea-128">Veri şablonunu tanımlama</span><span class="sxs-lookup"><span data-stu-id="1cbea-128">Defining the Data Template</span></span>

<span data-ttu-id="1cbea-129">Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="1cbea-130">Aşağıdaki kod örneği, <xref:System.Windows.Controls.ListBox> denetiminin görsel ağacını denetleyen `ListItemsTemplate` adlı <xref:System.Windows.DataTemplate> nesnesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1cbea-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="1cbea-131">Bu <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBox> denetiminin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>

### <a name="to-define-the-data-template"></a><span data-ttu-id="1cbea-132">Veri şablonunu tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="1cbea-132">To define the data template</span></span>

- <span data-ttu-id="1cbea-133">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a><span data-ttu-id="1cbea-134">Form düzeni belirtme</span><span class="sxs-lookup"><span data-stu-id="1cbea-134">Specifying the Form Layout</span></span>

<span data-ttu-id="1cbea-135">Formun düzeni üç satır ve üç sütunlu bir kılavuz tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="1cbea-136">Müşteriler tablosundaki her sütunu belirlemek için <xref:System.Windows.Controls.Label> denetimleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>

### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="1cbea-137">Kılavuz yerleşimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1cbea-137">To set up the Grid layout</span></span>

- <span data-ttu-id="1cbea-138">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="1cbea-139">Etiket denetimlerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1cbea-139">To set up the Label controls</span></span>

- <span data-ttu-id="1cbea-140">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a><span data-ttu-id="1cbea-141">Veri bağlamalarını belirtme</span><span class="sxs-lookup"><span data-stu-id="1cbea-141">Specifying Data Bindings</span></span>

<span data-ttu-id="1cbea-142">Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="1cbea-143">Eklenen `ListItemsTemplate`, bir <xref:System.Windows.Controls.TextBlock> denetimini veritabanındaki `ContactName` alanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="1cbea-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>

<span data-ttu-id="1cbea-144">Her müşteri kaydının ayrıntıları çeşitli <xref:System.Windows.Controls.TextBox> denetimlerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>

### <a name="to-specify-data-bindings"></a><span data-ttu-id="1cbea-145">Veri bağlamalarını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1cbea-145">To specify data bindings</span></span>

- <span data-ttu-id="1cbea-146">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     <span data-ttu-id="1cbea-147"><xref:System.Windows.Data.Binding> sınıfı, <xref:System.Windows.Controls.TextBox> denetimlerini veritabanındaki uygun alanlara bağlar.</span><span class="sxs-lookup"><span data-stu-id="1cbea-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="1cbea-148">Birlikte çalışabilirlik kullanarak verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1cbea-148">Displaying Data by Using Interoperation</span></span>

<span data-ttu-id="1cbea-149">Seçilen müşteriye karşılık gelen siparişler, `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="1cbea-150">`dataGridView1` denetimi, arka plan kod dosyasındaki veri kaynağına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="1cbea-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi bu Windows Forms denetiminin üst öğesidir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this Windows Forms control.</span></span>

### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="1cbea-152">DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1cbea-152">To display data in the DataGridView control</span></span>

- <span data-ttu-id="1cbea-153">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="1cbea-154">Veri kaynağı projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="1cbea-154">Adding the Data Source to the Project</span></span>

<span data-ttu-id="1cbea-155">Visual Studio ile projenize kolayca veri kaynağı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbea-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="1cbea-156">Bu yordam, projenize kesin olarak belirlenmiş bir veri kümesi ekler.</span><span class="sxs-lookup"><span data-stu-id="1cbea-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="1cbea-157">Seçili tabloların her biri için tablo bağdaştırıcıları gibi diğer çeşitli destek sınıfları da eklenir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="1cbea-158">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="1cbea-158">To add the data source</span></span>

1. <span data-ttu-id="1cbea-159">**Veri** menüsünde **Yeni veri kaynağı Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1cbea-159">From the **Data** menu, select **Add New Data Source**.</span></span>

2. <span data-ttu-id="1cbea-160">**Veri kaynağı Yapılandırma sihirbazında**, bir veri kümesi kullanarak Northwind veritabanına bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1cbea-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="1cbea-161">Daha fazla bilgi için bkz. [nasıl yapılır: veritabanındaki verilere bağlanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="1cbea-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>

3. <span data-ttu-id="1cbea-162">**Veri kaynağı Yapılandırma Sihirbazı**tarafından istendiğinde, bağlantı dizesini `NorthwindConnectionString`olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1cbea-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>

4. <span data-ttu-id="1cbea-163">Veritabanı nesnelerinizi seçmeniz istendiğinde `Customers` ve `Orders` tabloları seçip oluşturulan veri kümesini `NorthwindDataSet`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>

## <a name="binding-to-the-data-source"></a><span data-ttu-id="1cbea-164">Veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="1cbea-164">Binding to the Data Source</span></span>

<span data-ttu-id="1cbea-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> bileşeni, uygulamanın veri kaynağı için tekdüzen arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cbea-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="1cbea-166">Veri kaynağına bağlama, arka plan kod dosyasında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-166">Binding to the data source is implemented in the code-behind file.</span></span>

### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="1cbea-167">Veri kaynağına bağlamak için</span><span class="sxs-lookup"><span data-stu-id="1cbea-167">To bind to the data source</span></span>

1. <span data-ttu-id="1cbea-168">MainWindow. xaml. vb veya MainWindow.xaml.cs adlı arka plan kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="1cbea-169">Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-169">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="1cbea-170">Bu kod, <xref:System.Windows.Forms.BindingSource> bileşenini ve veritabanına bağlanan ilişkili yardımcı sınıfları bildirir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="1cbea-171">Oluşturucuya aşağıdaki kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="1cbea-172">Bu kod <xref:System.Windows.Forms.BindingSource> bileşenini oluşturur ve başlatır.</span><span class="sxs-lookup"><span data-stu-id="1cbea-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="1cbea-173">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="1cbea-174">Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1cbea-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="1cbea-175">Özellikler penceresi, **Olaylar** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="1cbea-176"><xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="1cbea-177">Aşağıdaki kodu <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="1cbea-178">Bu kod, <xref:System.Windows.Forms.BindingSource> bileşenini veri bağlamı olarak atar ve `Customers` ve `Orders` bağdaştırıcı nesnelerini doldurur.</span><span class="sxs-lookup"><span data-stu-id="1cbea-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="1cbea-179">Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="1cbea-180">Bu yöntem <xref:System.Windows.Data.CollectionView.CurrentChanged> olayını işler ve veri bağlamasının geçerli öğesini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cbea-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. <span data-ttu-id="1cbea-181">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1cbea-181">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cbea-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cbea-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1cbea-183">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="1cbea-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="1cbea-184">Karma uygulamalarda veri bağlama örneği</span><span class="sxs-lookup"><span data-stu-id="1cbea-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)
- [<span data-ttu-id="1cbea-185">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1cbea-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="1cbea-186">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="1cbea-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
