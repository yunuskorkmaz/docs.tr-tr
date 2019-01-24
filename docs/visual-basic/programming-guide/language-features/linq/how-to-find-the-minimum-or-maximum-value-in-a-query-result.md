---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak bir sorgu sonucunda en düşük ve en fazla değeri bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: e4a7215afdfbfc7653247ad0286a36dd2ab50ba2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514276"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="4d5e0-102">Nasıl yapılır: LINQ (Visual Basic) kullanarak bir sorgu sonucunda en düşük ve en fazla değeri bulma</span><span class="sxs-lookup"><span data-stu-id="4d5e0-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="4d5e0-103">Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="4d5e0-104">Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştiren yeni bir uygulama oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="4d5e0-105">Örnek sonuçlar için minimum ve maksimum değerleri kullanarak belirler `Aggregate` ve `Group By` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="4d5e0-106">Daha fazla bilgi için [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4d5e0-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="4d5e0-107">Bu konudaki örnekler, Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4d5e0-108">Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="4d5e0-109">Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4d5e0-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4d5e0-110">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4d5e0-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="4d5e0-111">Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="4d5e0-112">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="4d5e0-113">Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4d5e0-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d5e0-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="4d5e0-115">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4d5e0-116">Visual Basic seçin **Windows Forms uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="4d5e0-117">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4d5e0-118">Seçin **LINQ to SQL sınıfları** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="4d5e0-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4d5e0-120">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-120">Click **Add**.</span></span> <span data-ttu-id="4d5e0-121">Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="4d5e0-122">O/R Tasarımcısı için sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d5e0-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="4d5e0-123">İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4d5e0-124">Genişletin **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4d5e0-125">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="4d5e0-126">Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="4d5e0-127">Siparişler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4d5e0-128">Tasarımcı yeni oluşturur `Customer` ve `Order` projeniz için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="4d5e0-129">Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="4d5e0-130">Örneğin, IntelliSense, gösterilir `Customer` nesnesinin bir `Orders` özelliği için tüm siparişleri o müşteri ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="4d5e0-131">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="4d5e0-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="4d5e0-133">Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d5e0-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="4d5e0-134">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="4d5e0-135">Form1 kod eklemek için çift `Load` formun olay.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="4d5e0-136">Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="4d5e0-137">Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="4d5e0-138"><xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4d5e0-139">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4d5e0-140">Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="4d5e0-141">Aşağıdaki kodu ekleyin `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="4d5e0-142">Bu kod, veri bağlamının özellikleri olarak sunulur ve sonuçlar için minimum ve maksimum değerleri belirler tabloları sorgular.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="4d5e0-143">Örnek kullanır kendisinin `Aggregate` tek bir sonuç için sorgu yan tümcesinin ve `Group By` yan tümcesi için ortalama gösterilecek gruplandırılmış sonuçları.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  <span data-ttu-id="4d5e0-144">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5e0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d5e0-145">See also</span></span>
- [<span data-ttu-id="4d5e0-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="4d5e0-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="4d5e0-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="4d5e0-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4d5e0-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4d5e0-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="4d5e0-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="4d5e0-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
