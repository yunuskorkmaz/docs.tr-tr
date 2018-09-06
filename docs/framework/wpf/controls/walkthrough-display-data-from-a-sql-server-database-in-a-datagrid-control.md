---
title: 'İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 1421d076ff202ec87a9d861ab2c7d1c1cdcdc1b7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798732"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="a7c71-102">İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a7c71-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="a7c71-103">Bu kılavuzda, bir SQL Server veritabanından veri almak ve bu verileri görüntüleme bir <xref:System.Windows.Controls.DataGrid> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a7c71-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="a7c71-104">ADO.NET varlık çerçevesi veri temsil eder ve bir varlık sınıfı belirtilen verileri alan bir sorgu yazmak için LINQ kullanma varlık sınıfları oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7c71-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7c71-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a7c71-105">Prerequisites</span></span>  
 <span data-ttu-id="a7c71-106">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="a7c71-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="a7c71-107">.</span><span class="sxs-lookup"><span data-stu-id="a7c71-107">.</span></span>  
  
-   <span data-ttu-id="a7c71-108">Çalışan bir SQL Server veya SQL Server bağlı AdventureWorks örnek veritabanı içeren bir Express örneğine erişim.</span><span class="sxs-lookup"><span data-stu-id="a7c71-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="a7c71-109">AdventureWorks veritabanı indirebileceğiniz [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="a7c71-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="a7c71-110">Varlık sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a7c71-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="a7c71-111">Visual Basic veya C# içinde yeni bir WPF uygulaması projesi oluşturun ve adlandırın `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="a7c71-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="a7c71-112">Çözüm Gezgini'nde projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a7c71-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="a7c71-113">Yeni Öğe Ekle iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a7c71-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="a7c71-114">Yüklü Şablonlar bölmesinde seçin **veri** şablonları listesinde seçip **ADO.NET Varlık Veri modu**m.</span><span class="sxs-lookup"><span data-stu-id="a7c71-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="a7c71-115">![ADO.NET varlık veri modeli seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="a7c71-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="a7c71-116">Dosya adı `AdventureWorksModel.edmx` ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a7c71-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="a7c71-117">Varlık Veri Modeli Sihirbazı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a7c71-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="a7c71-118">Choose Model Contents ekranında seçin **veritabanından Oluştur** ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a7c71-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="a7c71-119">![Veritabanı seçeneği Oluştur'u seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="a7c71-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="a7c71-120">Veri bağlantınızı seçin ekranında AdventureWorksLT2008 veritabanınıza bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7c71-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="a7c71-121">Daha fazla bilgi için [seçin bilgisayarınızı veri bağlantısı iletişim kutusu](https://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="a7c71-121">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="a7c71-122">![Veritabanına bağlantı sağlama](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="a7c71-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="a7c71-123">Adı olduğundan emin olun `AdventureWorksLT2008Entities` ve **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet** onay kutusunun seçili olduğundan ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a7c71-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="a7c71-124">Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve seçin **ürün** ve **ProductCategory** tablolar.</span><span class="sxs-lookup"><span data-stu-id="a7c71-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="a7c71-125">Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte, yalnızca bu iki tablolarından verileri alın.</span><span class="sxs-lookup"><span data-stu-id="a7c71-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="a7c71-126">![Product ve ProductCategory tablolarından seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="a7c71-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="a7c71-127">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a7c71-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="a7c71-128">Product ve ProductCategory varlıklar, varlık Tasarımcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a7c71-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="a7c71-129">![Product ve ProductCategory varlık modelleri](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="a7c71-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="a7c71-130">Almak ve verileri sunmak için</span><span class="sxs-lookup"><span data-stu-id="a7c71-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="a7c71-131">MainWindow.xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a7c71-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="a7c71-132">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliği <xref:System.Windows.Window> 450.</span><span class="sxs-lookup"><span data-stu-id="a7c71-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="a7c71-133">XAML Düzenleyicisi'nde, aşağıdaki ekleyin <xref:System.Windows.Controls.DataGrid> arasında etiketi `<Grid>` ve `</Grid>` eklenecek etiketleri bir <xref:System.Windows.Controls.DataGrid> adlı `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="a7c71-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="a7c71-134">![DataGrid penceresiyle](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="a7c71-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="a7c71-135">Seçin <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="a7c71-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="a7c71-136">Özellikler penceresinde veya XAML Düzenleyicisi'ni kullanarak oluşturmak için bir olay işleyicisi <xref:System.Windows.Window> adlı `Window_Loaded` için <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="a7c71-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="a7c71-137">Daha fazla bilgi için [nasıl yapılır: basit bir olay işleyicisi oluşturun](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="a7c71-137">For more information, see [How to: Create a Simple Event Handler](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="a7c71-138">Aşağıdaki XAML MainWindow.xaml için gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7c71-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7c71-139">Visual Basic kullanıyorsanız MainWindow.xaml öğesinin ilk satırı değiştirin `x:Class="DataGridSQLExample.MainWindow"` ile `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="a7c71-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="a7c71-140">Arka plan kod dosyası (MainWindow.xaml.vb veya MainWindow.xaml.cs) açık <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="a7c71-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="a7c71-141">Yalnızca belirli değerleri birleştirilmiş tablolardaki almak ve ayarlamak için aşağıdaki kodu ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.DataGrid> sorgu sonuçlarını.</span><span class="sxs-lookup"><span data-stu-id="a7c71-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="a7c71-142">Örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a7c71-142">Run the example.</span></span>  
  
     <span data-ttu-id="a7c71-143">Görmelisiniz bir <xref:System.Windows.Controls.DataGrid> , verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a7c71-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="a7c71-144">![SQL veritabanındaki verilerle DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="a7c71-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7c71-145">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a7c71-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c71-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c71-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="a7c71-147">Nasıl Yaparım: WPF uygulamalarında Entity Framework ile çalışmaya?</span><span class="sxs-lookup"><span data-stu-id="a7c71-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)
