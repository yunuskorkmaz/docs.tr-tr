---
title: "İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8ed596706c8d656842191262c25301db595ee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="606bd-102">İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="606bd-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="606bd-103">Bu kılavuzda, bir SQL Server veritabanından veri almak ve bu verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="606bd-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="606bd-104">ADO.NET Entity Framework verileri temsil eder ve LINQ varlık sınıfından belirtilen verileri alan bir sorgu yazmak için kullanabileceğiniz varlık sınıfları oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="606bd-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="606bd-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="606bd-105">Prerequisites</span></span>  
 <span data-ttu-id="606bd-106">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="606bd-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="606bd-107">.</span><span class="sxs-lookup"><span data-stu-id="606bd-107">.</span></span>  
  
-   <span data-ttu-id="606bd-108">SQL Server ya da ekli AdventureWorks örnek veritabanının bulunduğu SQL Server Express'in çalışan örneğine erişim.</span><span class="sxs-lookup"><span data-stu-id="606bd-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="606bd-109">AdventureWorks veritabanından indirebilirsiniz [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="606bd-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="606bd-110">Varlık sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="606bd-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="606bd-111">Visual Basic veya C# içinde yeni bir WPF uygulama projesi oluşturun ve adlandırın `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="606bd-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="606bd-112">Çözüm Gezgini'nde projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="606bd-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="606bd-113">Yeni Öğe Ekle iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="606bd-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="606bd-114">Yüklü Şablonlar bölmesinde seçin **veri** ve şablonları listesinde seçin **ADO.NET Varlık Veri modu**l.</span><span class="sxs-lookup"><span data-stu-id="606bd-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="606bd-115">![ADO.NET varlık veri modeli seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="606bd-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="606bd-116">Dosya adı `AdventureWorksModel.edmx` ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="606bd-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="606bd-117">Varlık Veri Modeli Sihirbazı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="606bd-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="606bd-118">Model içeriği seçin ekranında şunları seçin **veritabanından Oluştur** ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="606bd-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="606bd-119">![Veritabanı seçeneğinden Oluştur'u seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="606bd-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="606bd-120">Veri bağlantınızı seçin ekranında, AdventureWorksLT2008 veritabanına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="606bd-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="606bd-121">Daha fazla bilgi için bkz: [seçin bilgisayarınızı veri bağlantısı iletişim kutusu](http://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="606bd-121">For more information, see [Choose Your Data Connection Dialog Box](http://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="606bd-122">![Veritabanına bağlantı sağlama](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="606bd-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="606bd-123">Adı olduğundan emin olun `AdventureWorksLT2008Entities` ve **varlık bağlantı ayarlarını App.Config'de şöyle Kaydet** onay kutusu seçilidir ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="606bd-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="606bd-124">Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve seçin **ürün** ve **ProductCategory** tabloları.</span><span class="sxs-lookup"><span data-stu-id="606bd-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="606bd-125">Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte, yalnızca iki bu tablolardaki verileri.</span><span class="sxs-lookup"><span data-stu-id="606bd-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="606bd-126">![Ürün ProductCategory tablolardan seçip](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="606bd-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="606bd-127">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="606bd-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="606bd-128">Ürün ve ProductCategory varlıklar, varlık Tasarımcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="606bd-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="606bd-129">![Ürün ve ProductCategory varlık modelleri](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="606bd-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="606bd-130">Almak ve veri sunmak için</span><span class="sxs-lookup"><span data-stu-id="606bd-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="606bd-131">MainWindow.xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="606bd-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="606bd-132">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özellikte <xref:System.Windows.Window> 450.</span><span class="sxs-lookup"><span data-stu-id="606bd-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="606bd-133">XAML Düzenleyicisi'nde, aşağıdaki ekleyin <xref:System.Windows.Controls.DataGrid> arasında etiketi `<Grid>` ve `</Grid>` ekleme etiketlerle bir <xref:System.Windows.Controls.DataGrid> adlı `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="606bd-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="606bd-134">![DataGrid penceresiyle](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="606bd-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="606bd-135">Seçin <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="606bd-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="606bd-136">Özellikler penceresini veya XAML Düzenleyicisi'ni kullanarak oluşturmak için bir olay işleyicisi <xref:System.Windows.Window> adlı `Window_Loaded` için <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="606bd-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="606bd-137">Daha fazla bilgi için bkz: [nasıl yapılır: basit bir olay işleyicisi oluşturun](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="606bd-137">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="606bd-138">Aşağıdaki XAML için MainWindow.xaml gösterir.</span><span class="sxs-lookup"><span data-stu-id="606bd-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="606bd-139">Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="DataGridSQLExample.MainWindow"` ile `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="606bd-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="606bd-140">Arka plan kod dosyasına (MainWindow.xaml.vb veya MainWindow.xaml.cs) açık <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="606bd-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="606bd-141">Birleştirilmiş tablolardaki yalnızca belirli değerleri almak ve ayarlamak için aşağıdaki kodu ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.DataGrid> sorgu sonuçları.</span><span class="sxs-lookup"><span data-stu-id="606bd-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="606bd-142">Örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="606bd-142">Run the example.</span></span>  
  
     <span data-ttu-id="606bd-143">Görmeniz gerekir bir <xref:System.Windows.Controls.DataGrid> verilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="606bd-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="606bd-144">![SQL veritabanı verileriyle DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="606bd-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="606bd-145">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="606bd-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606bd-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="606bd-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="606bd-147">I: WPF uygulamalarında Entity Framework ile çalışmaya nasıl başlayabilirim?</span><span class="sxs-lookup"><span data-stu-id="606bd-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](http://go.microsoft.com/fwlink/?LinkId=159868)
