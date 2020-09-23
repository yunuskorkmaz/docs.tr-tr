---
title: 'Nasıl yapılır: LINQ Kullanarak Verileri Sayma, Toplama veya Ortalamasını Alma'
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
ms.openlocfilehash: 617c6959e2d3add6d36266b0827ef7281b0c77a9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059255"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="7a9d4-102">Nasıl yapılır: LINQ Kullanarak Count, Sum veya Average Verisi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a9d4-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="7a9d4-103">Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="7a9d4-104">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="7a9d4-105">Örnek, `Aggregate` ve yan tümceleri kullanılarak sonuçların sayımlarını, toplamlarını ve ortalamasını verir `Group By` .</span><span class="sxs-lookup"><span data-stu-id="7a9d4-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="7a9d4-106">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7a9d4-106">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="7a9d4-107">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="7a9d4-108">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="7a9d4-109">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="7a9d4-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="7a9d4-110">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7a9d4-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="7a9d4-111">Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="7a9d4-112">**Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="7a9d4-113">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="7a9d4-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="7a9d4-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="7a9d4-115">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="7a9d4-116">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="7a9d4-117">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7a9d4-118">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="7a9d4-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="7a9d4-120">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-120">Click **Add**.</span></span> <span data-ttu-id="7a9d4-121">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="7a9d4-122">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="7a9d4-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="7a9d4-123">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="7a9d4-124">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="7a9d4-125">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="7a9d4-126">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="7a9d4-127">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="7a9d4-128">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="7a9d4-129">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="7a9d4-130">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="7a9d4-131">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="7a9d4-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="7a9d4-133">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="7a9d4-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="7a9d4-134">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="7a9d4-135">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="7a9d4-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="7a9d4-136">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="7a9d4-137">Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="7a9d4-138"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="7a9d4-139">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="7a9d4-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="7a9d4-140">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="7a9d4-141">Aşağıdaki kodu olayına ekleyerek, ' `Load` ın özellikleri olarak gösterilen tabloları <xref:System.Data.Linq.DataContext> ve sayı, toplam değerini ve sonuçların ortalamasını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="7a9d4-142">Örnek, `Aggregate` tek bir sonuç sorgulamak için yan tümcesini ve `Group By` gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="7a9d4-143">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9d4-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a9d4-144">See also</span></span>

- [<span data-ttu-id="7a9d4-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="7a9d4-145">LINQ</span></span>](index.md)
- [<span data-ttu-id="7a9d4-146">Sorgular</span><span class="sxs-lookup"><span data-stu-id="7a9d4-146">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="7a9d4-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7a9d4-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="7a9d4-148">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="7a9d4-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="7a9d4-149">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="7a9d4-149">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="7a9d4-150">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="7a9d4-150">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
