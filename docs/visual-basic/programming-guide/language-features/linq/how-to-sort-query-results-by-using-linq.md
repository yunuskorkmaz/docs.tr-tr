---
title: 'Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Sıralama'
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
ms.openlocfilehash: 94c2907f05aa9b5b2bc8659cef6f523187f1ef6b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071800"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="c39ea-102">Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Sıralama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c39ea-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="c39ea-103">Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c39ea-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="c39ea-104">Aşağıdaki örnek, bir SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir ve yan tümcesini kullanarak sonuçları birden çok alana göre sıralar `Order By` .</span><span class="sxs-lookup"><span data-stu-id="c39ea-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="c39ea-105">Her bir alan için sıralama düzeni artan sıra veya azalan sırada olabilir.</span><span class="sxs-lookup"><span data-stu-id="c39ea-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="c39ea-106">Daha fazla bilgi için bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c39ea-106">For more information, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="c39ea-107">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c39ea-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="c39ea-108">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c39ea-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="c39ea-109">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c39ea-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="c39ea-110">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c39ea-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="c39ea-111">Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="c39ea-112">**Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="c39ea-113">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="c39ea-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="c39ea-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="c39ea-115">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="c39ea-116">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="c39ea-117">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="c39ea-118">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="c39ea-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="c39ea-120">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-120">Click **Add**.</span></span> <span data-ttu-id="c39ea-121">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="c39ea-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="c39ea-122">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="c39ea-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="c39ea-123">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="c39ea-124">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="c39ea-125">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c39ea-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="c39ea-126">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="c39ea-127">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="c39ea-128">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c39ea-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="c39ea-129">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="c39ea-130">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39ea-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="c39ea-131">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="c39ea-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="c39ea-133">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="c39ea-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="c39ea-134">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="c39ea-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="c39ea-135">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="c39ea-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="c39ea-136">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projenize bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="c39ea-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="c39ea-137">Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin.</span><span class="sxs-lookup"><span data-stu-id="c39ea-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="c39ea-138"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c39ea-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="c39ea-139">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="c39ea-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="c39ea-140">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c39ea-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="c39ea-141">`Load`Veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için olaya aşağıdaki kodu ekleyin ve sonuçları sıralayın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="c39ea-142">Sorgu sonuçları, müşteri siparişlerinin sayısına göre azalan sırayla sıralar.</span><span class="sxs-lookup"><span data-stu-id="c39ea-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="c39ea-143">Aynı sayıda siparişi olan müşteriler, şirket adına göre artan sırada (varsayılan) sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c39ea-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="c39ea-144">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c39ea-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39ea-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39ea-145">See also</span></span>

- [<span data-ttu-id="c39ea-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="c39ea-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="c39ea-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c39ea-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="c39ea-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c39ea-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c39ea-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="c39ea-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
