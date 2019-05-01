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
ms.openlocfilehash: 274ec2e8ef16190da53061bb197bc3b1a1fadcf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024108"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="c1432-102">İzlenecek yol: DataGrid denetimindeki SQL Server veritabanından veri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c1432-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="c1432-103">Bu kılavuzda, bir SQL Server veritabanından veri almak ve bu verileri görüntüleme bir <xref:System.Windows.Controls.DataGrid> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c1432-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="c1432-104">ADO.NET varlık çerçevesi veri temsil eder ve bir varlık sınıfı belirtilen verileri alan bir sorgu yazmak için LINQ kullanma varlık sınıfları oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1432-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1432-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c1432-105">Prerequisites</span></span>

<span data-ttu-id="c1432-106">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="c1432-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="c1432-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1432-107">Visual Studio.</span></span>

- <span data-ttu-id="c1432-108">Çalışan bir SQL Server veya SQL Server bağlı AdventureWorks örnek veritabanı içeren bir Express örneğine erişim.</span><span class="sxs-lookup"><span data-stu-id="c1432-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="c1432-109">AdventureWorks veritabanı indirebileceğiniz [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="c1432-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="c1432-110">Varlık sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1432-110">Create entity classes</span></span>

1. <span data-ttu-id="c1432-111">Visual Basic veya C# içinde yeni bir WPF uygulaması projesi oluşturun ve adlandırın `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="c1432-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="c1432-112">Çözüm Gezgini'nde projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="c1432-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="c1432-113">Yeni Öğe Ekle iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1432-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="c1432-114">Yüklü Şablonlar bölmesinde seçin **veri** şablonları listesinde seçip **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="c1432-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![ADO.NET varlık veri modeli öğe şablonu](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="c1432-116">Dosya adı `AdventureWorksModel.edmx` ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c1432-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="c1432-117">Varlık Veri Modeli Sihirbazı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1432-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="c1432-118">Choose Model Contents ekranında seçin **EF veritabanı Tasarımcısından** ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="c1432-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="c1432-119">Veri bağlantınızı seçin ekranında AdventureWorksLT2008 veritabanınıza bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1432-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="c1432-120">Daha fazla bilgi için [seçin bilgisayarınızı veri bağlantısı iletişim kutusu](https://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="c1432-120">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>

    <span data-ttu-id="c1432-121">Adı olduğundan emin olun `AdventureWorksLT2008Entities` ve **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet** onay kutusunun seçili olduğundan ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="c1432-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="c1432-122">Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve seçin **ürün** ve **ProductCategory** tablolar.</span><span class="sxs-lookup"><span data-stu-id="c1432-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="c1432-123">Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte, yalnızca bu iki tablolarından verileri alın.</span><span class="sxs-lookup"><span data-stu-id="c1432-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="c1432-124">![Product ve ProductCategory tablolarından seçin](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="c1432-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="c1432-125">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1432-125">Click **Finish**.</span></span>

     <span data-ttu-id="c1432-126">Product ve ProductCategory varlıklar, varlık Tasarımcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1432-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="c1432-127">![Product ve ProductCategory varlık modelleri](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="c1432-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="c1432-128">Almak ve verileri sunmak</span><span class="sxs-lookup"><span data-stu-id="c1432-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="c1432-129">MainWindow.xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c1432-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="c1432-130">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliği <xref:System.Windows.Window> 450.</span><span class="sxs-lookup"><span data-stu-id="c1432-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="c1432-131">XAML Düzenleyicisi'nde, aşağıdaki ekleyin <xref:System.Windows.Controls.DataGrid> arasında etiketi `<Grid>` ve `</Grid>` eklenecek etiketleri bir <xref:System.Windows.Controls.DataGrid> adlı `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="c1432-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="c1432-132">![DataGrid penceresiyle](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="c1432-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="c1432-133">Seçin <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="c1432-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="c1432-134">Özellikler penceresinde veya XAML Düzenleyicisi'ni kullanarak oluşturmak için bir olay işleyicisi <xref:System.Windows.Window> adlı `Window_Loaded` için <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="c1432-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="c1432-135">Daha fazla bilgi için [nasıl yapılır: Basit olay işleyicisi oluşturun](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c1432-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="c1432-136">Aşağıdaki XAML MainWindow.xaml için gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1432-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c1432-137">Visual Basic kullanıyorsanız MainWindow.xaml öğesinin ilk satırı değiştirin `x:Class="DataGridSQLExample.MainWindow"` ile `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="c1432-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="c1432-138">Arka plan kod dosyası (MainWindow.xaml.vb veya MainWindow.xaml.cs) açık <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="c1432-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="c1432-139">Yalnızca belirli değerleri birleştirilmiş tablolardaki almak ve ayarlamak için aşağıdaki kodu ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.DataGrid> sorgu sonuçlarını.</span><span class="sxs-lookup"><span data-stu-id="c1432-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="c1432-140">Örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1432-140">Run the example.</span></span>

     <span data-ttu-id="c1432-141">Görmelisiniz bir <xref:System.Windows.Controls.DataGrid> , verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c1432-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="c1432-142">![SQL veritabanındaki verilerle DataGrid](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="c1432-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="c1432-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1432-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="c1432-144">Nasıl Yaparım WPF uygulamalarında Entity Framework ile çalışmaya başlama?</span><span class="sxs-lookup"><span data-stu-id="c1432-144">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)