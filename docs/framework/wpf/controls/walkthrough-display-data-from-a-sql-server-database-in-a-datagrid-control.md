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
ms.openlocfilehash: fc8b35c89e76a415529d76db687bc96767384e11
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452129"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="8fda7-102">İzlenecek yol: DataGrid Denetimindeki SQL Server veritabanından veri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8fda7-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="8fda7-103">Bu kılavuzda, verileri bir SQL Server veritabanından alır ve bu verileri bir <xref:System.Windows.Controls.DataGrid> denetiminde görüntüleriz.</span><span class="sxs-lookup"><span data-stu-id="8fda7-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="8fda7-104">Verileri temsil eden varlık sınıflarını oluşturmak için ADO.NET Entity Framework kullanır ve bir varlık sınıfından belirtilen verileri alan bir sorgu yazmak için LINQ kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8fda7-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8fda7-105">Prerequisites</span></span>

<span data-ttu-id="8fda7-106">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="8fda7-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="8fda7-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8fda7-107">Visual Studio.</span></span>

- <span data-ttu-id="8fda7-108">Üzerinde AdventureWorks örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim.</span><span class="sxs-lookup"><span data-stu-id="8fda7-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="8fda7-109">AdventureWorks veritabanını [GitHub](https://github.com/Microsoft/sql-server-samples/releases)'dan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fda7-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="8fda7-110">Varlık sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fda7-110">Create entity classes</span></span>

1. <span data-ttu-id="8fda7-111">Visual Basic veya C#içinde yenı bir WPF uygulaması projesi oluşturun ve `DataGridSQLExample`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="8fda7-112">Çözüm Gezgini, projenize sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="8fda7-113">Yeni öğe Ekle iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fda7-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="8fda7-114">Yüklü şablonlar bölmesinde, **veriler** ' i seçin ve şablonlar listesinde **ADO.net varlık veri modeli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![ADO.NET Varlık Veri Modeli öğesi şablonu](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="8fda7-116">`AdventureWorksModel.edmx` dosyayı adlandırın ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="8fda7-117">Varlık Veri Modeli Sihirbazı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fda7-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="8fda7-118">Model Içeriğini seçin ekranında, **veritabanından EF Designer** ' ı seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="8fda7-119">Veri bağlantınızı seçin ekranında AdventureWorksLT2008 veritabanınıza bağlantı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="8fda7-120">Daha fazla bilgi için bkz. [veri bağlantınızı seçme Iletişim kutusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8fda7-120">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="8fda7-121">Adın `AdventureWorksLT2008Entities` olduğundan ve **app. config dosyasındaki varlık bağlantı ayarlarını kaydet** onay kutusunun seçili olduğundan emin olun ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="8fda7-122">Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve **Product** ve **ProductCategory** tablolarını seçin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="8fda7-123">Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte yalnızca bu iki tablodan veri alınır.</span><span class="sxs-lookup"><span data-stu-id="8fda7-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="8fda7-124">![Tablolardan Product ve ProductCategory seçin](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="8fda7-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="8fda7-125">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-125">Click **Finish**.</span></span>

     <span data-ttu-id="8fda7-126">Product ve ProductCategory varlıkları Entity Desisgner görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fda7-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="8fda7-127">![Product ve ProductCategory varlık modelleri](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="8fda7-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="8fda7-128">Verileri alma ve sunma</span><span class="sxs-lookup"><span data-stu-id="8fda7-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="8fda7-129">MainWindow. xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="8fda7-130"><xref:System.Windows.Window> <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 450 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="8fda7-131">XAML düzenleyicisinde, `dataGrid1`adlı bir <xref:System.Windows.Controls.DataGrid> eklemek için `<Grid>` ve `</Grid>` etiketleri arasına aşağıdaki <xref:System.Windows.Controls.DataGrid> etiketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="8fda7-132">![DataGrid ile pencere](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="8fda7-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="8fda7-133"><xref:System.Windows.Window>seçin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="8fda7-134">Özellikler penceresi veya XAML düzenleyicisini kullanarak, <xref:System.Windows.FrameworkElement.Loaded> olayı için `Window_Loaded` adlı <xref:System.Windows.Window> bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8fda7-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="8fda7-135">Daha fazla bilgi için bkz. [nasıl yapılır: basit olay Işleyicisi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8fda7-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="8fda7-136">Aşağıda MainWindow. xaml için XAML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8fda7-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8fda7-137">Visual Basic kullanıyorsanız, MainWindow. xaml ' in ilk satırında `x:Class="DataGridSQLExample.MainWindow"` ' yı `x:Class="MainWindow"`ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8fda7-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="8fda7-138"><xref:System.Windows.Window>için arka plan kod dosyasını (MainWindow. xaml. vb veya MainWindow.xaml.cs) açın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="8fda7-139">Birleşik tablolardan yalnızca belirli değerleri almak için aşağıdaki kodu ekleyin ve <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini sorgunun sonuçlarına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="8fda7-140">Örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8fda7-140">Run the example.</span></span>

     <span data-ttu-id="8fda7-141">Verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fda7-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="8fda7-142">![SQL veritabanı 'ndan veri içeren DataGrid](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="8fda7-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="8fda7-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fda7-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
