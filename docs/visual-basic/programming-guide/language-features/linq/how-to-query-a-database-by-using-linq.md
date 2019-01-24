---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak veritabanını sorgulama'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: a76eb5a010c8c5f750336935f0044e8dcc4322f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514861"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="35ced-102">Nasıl yapılır: LINQ (Visual Basic) kullanarak veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="35ced-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="35ced-103">Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="35ced-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="35ced-104">Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştiren yeni bir uygulama oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35ced-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="35ced-105">Bu konudaki örnekler, Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="35ced-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="35ced-106">Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ced-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="35ced-107">Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="35ced-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="35ced-108">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="35ced-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="35ced-109">Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="35ced-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="35ced-110">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="35ced-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="35ced-111">Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="35ced-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="35ced-112">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="35ced-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="35ced-113">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="35ced-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="35ced-114">Visual Basic seçin **Windows Forms uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="35ced-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="35ced-115">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="35ced-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="35ced-116">Seçin **LINQ to SQL sınıfları** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="35ced-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="35ced-117">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="35ced-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="35ced-118">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="35ced-118">Click **Add**.</span></span> <span data-ttu-id="35ced-119">Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="35ced-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="35ced-120">O/R Tasarımcısı için sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="35ced-120">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="35ced-121">İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="35ced-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="35ced-122">Genişletin **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="35ced-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="35ced-123">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ced-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="35ced-124">Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="35ced-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="35ced-125">Siparişler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="35ced-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="35ced-126">Tasarımcı yeni oluşturur `Customer` ve `Order` projeniz için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="35ced-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="35ced-127">Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="35ced-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="35ced-128">Örneğin, IntelliSense, gösterilir `Customer` nesnesinin bir `Orders` özelliği için tüm siparişleri o müşteri ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="35ced-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="35ced-129">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="35ced-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="35ced-130">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="35ced-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="35ced-131">Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="35ced-131">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="35ced-132">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="35ced-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="35ced-133">Form1 kod eklemek için çift `Load` formun olay.</span><span class="sxs-lookup"><span data-stu-id="35ced-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="35ced-134">Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="35ced-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="35ced-135">Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="35ced-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="35ced-136"><xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı.</span><span class="sxs-lookup"><span data-stu-id="35ced-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="35ced-137">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="35ced-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="35ced-138">Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="35ced-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="35ced-139">Aşağıdaki kodu ekleyin `Load` veri Bağlamınızı özellikleri olarak gösterilen tablolarını sorgulamak için olay.</span><span class="sxs-lookup"><span data-stu-id="35ced-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="35ced-140">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="35ced-140">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="35ced-141">Deneyebileceğiniz bazı ek sorgular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="35ced-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="35ced-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35ced-142">See also</span></span>
- [<span data-ttu-id="35ced-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="35ced-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="35ced-144">Sorgular</span><span class="sxs-lookup"><span data-stu-id="35ced-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="35ced-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="35ced-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="35ced-146">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="35ced-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
