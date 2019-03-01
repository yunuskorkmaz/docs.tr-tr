---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak sorgu sonuçlarını sıralama'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: 937206c5efeb4767f0c1f3d5a98f58314da105d4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967795"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="49bae-102">Nasıl yapılır: LINQ (Visual Basic) kullanarak sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="49bae-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="49bae-103">Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="49bae-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="49bae-104">Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştirir ve kullanarak birden çok alana göre sonuçları sıralayan yeni bir uygulamanın nasıl oluşturulacağını gösterir `Order By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="49bae-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="49bae-105">Her alan için sıralama düzeni artan veya azalan sırayla düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="49bae-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="49bae-106">Daha fazla bilgi için [Order By yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="49bae-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="49bae-107">Bu konudaki örnekler, Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49bae-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="49bae-108">Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49bae-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="49bae-109">Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="49bae-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="49bae-110">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="49bae-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="49bae-111">Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="49bae-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="49bae-112">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="49bae-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="49bae-113">Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="49bae-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="49bae-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="49bae-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="49bae-115">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="49bae-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="49bae-116">Visual Basic seçin **Windows Forms uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="49bae-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="49bae-117">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="49bae-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="49bae-118">Seçin **LINQ to SQL sınıfları** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="49bae-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="49bae-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="49bae-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="49bae-120">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="49bae-120">Click **Add**.</span></span> <span data-ttu-id="49bae-121">Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="49bae-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="49bae-122">O/R Tasarımcısı için sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="49bae-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="49bae-123">İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="49bae-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="49bae-124">Genişletin **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="49bae-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="49bae-125">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49bae-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="49bae-126">Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="49bae-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="49bae-127">Siparişler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="49bae-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="49bae-128">Tasarımcı yeni oluşturur `Customer` ve `Order` projeniz için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="49bae-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="49bae-129">Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="49bae-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="49bae-130">Örneğin, IntelliSense, gösterilir `Customer` nesnesinin bir `Orders` özelliği için tüm siparişleri o müşteri ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="49bae-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="49bae-131">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="49bae-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="49bae-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="49bae-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="49bae-133">Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="49bae-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="49bae-134">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="49bae-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="49bae-135">Form1 kod eklemek için çift `Load` formun olay.</span><span class="sxs-lookup"><span data-stu-id="49bae-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="49bae-136">Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projenize nesne.</span><span class="sxs-lookup"><span data-stu-id="49bae-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="49bae-137">Bu nesne bu tablolara erişen ve ayrı nesneler ve Koleksiyonlar her tablo için erişmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="49bae-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="49bae-138"><xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı.</span><span class="sxs-lookup"><span data-stu-id="49bae-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="49bae-139">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="49bae-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="49bae-140">Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="49bae-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="49bae-141">Aşağıdaki kodu ekleyin `Load` veri Bağlamınızı özellikleri olarak sunulur ve sonuçları sıralamak tabloları sorgulamak için olay.</span><span class="sxs-lookup"><span data-stu-id="49bae-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="49bae-142">Sorgu sonuçları azalan düzende müşteri siparişleri sayısına göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="49bae-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="49bae-143">Siparişler aynı sayıda olan müşteriler, artan düzende (varsayılan) şirket adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="49bae-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4.  <span data-ttu-id="49bae-144">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="49bae-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bae-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49bae-145">See also</span></span>
- [<span data-ttu-id="49bae-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="49bae-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="49bae-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="49bae-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="49bae-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="49bae-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="49bae-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="49bae-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
