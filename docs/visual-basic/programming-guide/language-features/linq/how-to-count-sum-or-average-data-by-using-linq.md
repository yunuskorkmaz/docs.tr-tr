---
title: 'Nasıl yapılır: LINQ kullanarak sayma, toplama veya ortalama veri'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345016"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="b820f-102">Nasıl yapılır: LINQ Kullanarak Count, Sum veya Average Verisi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b820f-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="b820f-103">Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b820f-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="b820f-104">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b820f-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="b820f-105">Örnek, `Aggregate` ve `Group By` yan tümcelerini kullanarak sonuçların sayısını sayar, toplar ve ortalamasını alır.</span><span class="sxs-lookup"><span data-stu-id="b820f-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="b820f-106">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b820f-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="b820f-107">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b820f-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="b820f-108">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b820f-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="b820f-109">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b820f-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="b820f-110">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b820f-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="b820f-111">Visual Studio 'da, **Görünüm** menüsünde **Sunucu Gezgini**/**Veritabanı Gezgini** ' a tıklayarak **Sunucu Gezgini**/**veritabanı Gezgini** açın.</span><span class="sxs-lookup"><span data-stu-id="b820f-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="b820f-112">**Sunucu Gezgini**/veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b820f-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="b820f-113">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="b820f-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="b820f-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="b820f-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="b820f-115">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b820f-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="b820f-116">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b820f-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="b820f-117">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b820f-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="b820f-118">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b820f-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="b820f-119">Dosyayı `northwind.dbml`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b820f-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="b820f-120">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b820f-120">Click **Add**.</span></span> <span data-ttu-id="b820f-121">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="b820f-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="b820f-122">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="b820f-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="b820f-123">**Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="b820f-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="b820f-124">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="b820f-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="b820f-125">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b820f-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="b820f-126">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b820f-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="b820f-127">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b820f-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="b820f-128">Tasarımcı projeniz için yeni `Customer` ve `Order` nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b820f-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="b820f-129">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b820f-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="b820f-130">Örneğin IntelliSense, `Customer` nesnesinin bu müşteriyle ilgili tüm siparişler için bir `Orders` özelliğine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b820f-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="b820f-131">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b820f-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="b820f-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b820f-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="b820f-133">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="b820f-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="b820f-134">**Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="b820f-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="b820f-135">Formun `Load` olayına kod eklemek için Form1 ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b820f-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="b820f-136">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projeniz için bir <xref:System.Data.Linq.DataContext> nesnesi ekledi.</span><span class="sxs-lookup"><span data-stu-id="b820f-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="b820f-137">Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin.</span><span class="sxs-lookup"><span data-stu-id="b820f-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="b820f-138">Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b820f-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="b820f-139">Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b820f-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="b820f-140">Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b820f-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="b820f-141"><xref:System.Data.Linq.DataContext> özellikleri olarak gösterilen tabloları sorgulamak için `Load` olayına aşağıdaki kodu ekleyin ve sonuçların sayımını yapın, toplayın ve ortalamasını yapın.</span><span class="sxs-lookup"><span data-stu-id="b820f-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="b820f-142">Örnek, tek bir sonuç sorgulamak için `Aggregate` yan tümcesini ve gruplanmış sonuçlara yönelik bir ortalama göstermek için `Group By` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b820f-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="b820f-143">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b820f-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b820f-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b820f-144">See also</span></span>

- [<span data-ttu-id="b820f-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="b820f-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="b820f-146">Sorgular</span><span class="sxs-lookup"><span data-stu-id="b820f-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b820f-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b820f-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="b820f-148">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="b820f-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="b820f-149">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="b820f-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="b820f-150">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="b820f-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
