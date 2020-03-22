---
title: 'Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma'
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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112368"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="6a14d-102">Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a14d-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="6a14d-103">Dil-Tümleşik Sorgu (LINQ), veritabanı bilgilerine erişmemi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6a14d-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="6a14d-104">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacagını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a14d-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="6a14d-105">Örnek, sonuçlar için en küçük ve maksimum `Aggregate` değerleri `Group By` ve yan tümceleri kullanarak belirler.</span><span class="sxs-lookup"><span data-stu-id="6a14d-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="6a14d-106">Daha fazla bilgi için [Bkz. Toplu Yan Tümce](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Grup Yan Tümcesi.](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="6a14d-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="6a14d-107">Bu konudaki örnekler Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a14d-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="6a14d-108">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft İndirme Merkezi'nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a14d-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="6a14d-109">Talimatlar için [bkz.](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)</span><span class="sxs-lookup"><span data-stu-id="6a14d-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="6a14d-110">Veritabanına bağlantı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a14d-110">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="6a14d-111">Visual Studio'da, **Görünüm** menüsünde **Server Explorer**/**Database Explorer'ı** tıklatarak Server **Explorer**/**Database Explorer'ı** açın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="6a14d-112">**Server Explorer**/**Database Explorer'da** **Veri Bağlantıları'nı** sağ tıklatın ve ardından **Bağlantı Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="6a14d-113">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="6a14d-114">SQL dosyasına LINQ içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="6a14d-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="6a14d-115">Visual Studio'da, **Dosya** menüsünde **Yeni'yi** işaret edin ve **Project'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="6a14d-116">Proje türü olarak Visual Basic **Windows Forms Application'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="6a14d-117">**Proje** menüsünde **Yeni Öğe Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="6a14d-118">**LINQ 'dan SQL Sınıflara** öğe şablonu seçin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="6a14d-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="6a14d-120">**Ekle**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-120">Click **Add**.</span></span> <span data-ttu-id="6a14d-121">Object Relational Designer (O/R Designer) northwind.dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="6a14d-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="6a14d-122">O/R Tasarımcısına sorgu için tablo ekleme</span><span class="sxs-lookup"><span data-stu-id="6a14d-122">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="6a14d-123">**Server Explorer**/**Database Explorer'da,** Northwind veritabanına bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="6a14d-124">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="6a14d-125">O/R Tasarımcısı'nı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a14d-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="6a14d-126">Müşteriler tablosunu tıklatın ve tasarımcının sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="6a14d-127">Siparişler tablosunu tıklatın ve tasarımcının sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="6a14d-128">Tasarımcı, projeniz `Customer` `Order` için yeni ve nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a14d-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="6a14d-129">Tasarımcının tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="6a14d-130">Örneğin, IntelliSense nesnenin `Customer` o müşteriyle ilgili tüm siparişler için bir `Orders` özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a14d-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="6a14d-131">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="6a14d-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-132">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="6a14d-133">Veritabanını sorgulamak ve sonuçları görüntülemek için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="6a14d-133">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="6a14d-134">Araç **Kutusundan,** projeniz için varsayılan Windows Formu'na bir <xref:System.Windows.Forms.DataGridView> denetim sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="6a14d-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="6a14d-135">Formun `Load` olayına kod eklemek için Form1'i çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="6a14d-136">O/R Tasarımcısı'na tablo eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="6a14d-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="6a14d-137">Bu nesne, her tablo için tek tek nesneler ve koleksiyonlar ek olarak, bu tablolara erişmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="6a14d-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="6a14d-138">Projenizin <xref:System.Data.Linq.DataContext> nesnesi .dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6a14d-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="6a14d-139">Bu proje için <xref:System.Data.Linq.DataContext> nesne `northwindDataContext`adı verilir.</span><span class="sxs-lookup"><span data-stu-id="6a14d-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="6a14d-140">Kodunuzdakinin <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a14d-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="6a14d-141">`Load` Olaya aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6a14d-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="6a14d-142">Bu kod, veri bağlamınızın özellikleri olarak ortaya çıkarılan tabloları sorgular ve sonuçlar için en küçük ve maksimum değerleri belirler.</span><span class="sxs-lookup"><span data-stu-id="6a14d-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="6a14d-143">Örnek, tek `Aggregate` bir sonuç için sorgu yapmak `Group By` için yan tümceyi ve gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a14d-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="6a14d-144">Projenizi çalıştırmak ve sonuçları görüntülemek için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6a14d-144">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a14d-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a14d-145">See also</span></span>

- [<span data-ttu-id="6a14d-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="6a14d-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="6a14d-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="6a14d-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="6a14d-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6a14d-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="6a14d-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="6a14d-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
