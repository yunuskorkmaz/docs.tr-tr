---
title: 'Nasıl yapılır: sorgu sonuçlarını LINQ kullanarak filtreleme'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 2ea8a852a2f012ddb25ec1198c66e09df880ff47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344984"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="3bf82-102">Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bf82-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="3bf82-103">Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3bf82-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="3bf82-104">Aşağıdaki örnek, bir SQL Server veritabanına yönelik sorgular gerçekleştiren ve `Where` yan tümcesini kullanarak sonuçları belirli bir değere filtreleyen yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bf82-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="3bf82-105">Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3bf82-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="3bf82-106">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bf82-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="3bf82-107">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf82-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="3bf82-108">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="3bf82-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="3bf82-109">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3bf82-109">To create a connection to a database</span></span>

1. <span data-ttu-id="3bf82-110">Visual Studio 'da, **Görünüm** menüsünde **Sunucu Gezgini**/**Veritabanı Gezgini** ' a tıklayarak **Sunucu Gezgini**/**veritabanı Gezgini** açın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="3bf82-111">**Sunucu Gezgini**/veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="3bf82-112">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="3bf82-113">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="3bf82-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="3bf82-114">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="3bf82-115">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="3bf82-116">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="3bf82-117">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="3bf82-118">Dosyayı `northwind.dbml`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="3bf82-119">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-119">Click **Add**.</span></span> <span data-ttu-id="3bf82-120">Northwind. dbml dosyası için Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.</span><span class="sxs-lookup"><span data-stu-id="3bf82-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="3bf82-121">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="3bf82-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="3bf82-122">**Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="3bf82-123">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="3bf82-124">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf82-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="3bf82-125">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="3bf82-126">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="3bf82-127">Tasarımcı projeniz için yeni `Customer` ve `Order` nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bf82-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="3bf82-128">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="3bf82-129">Örneğin IntelliSense, `Customer` nesnesinin bu müşteriyle ilgili tüm siparişler için bir `Orders` özelliğine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bf82-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="3bf82-130">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="3bf82-131">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="3bf82-132">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="3bf82-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="3bf82-133">**Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="3bf82-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="3bf82-134">Formun `Load` olayına kod eklemek için Form1 ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="3bf82-135">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projeniz için bir <xref:System.Data.Linq.DataContext> nesnesi ekledi.</span><span class="sxs-lookup"><span data-stu-id="3bf82-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="3bf82-136">Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="3bf82-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="3bf82-137">Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3bf82-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="3bf82-138">Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3bf82-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="3bf82-139">Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf82-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="3bf82-140">Veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için `Load` olayına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3bf82-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="3bf82-141">Sorgu sonuçlara filtre uygular ve yalnızca `London`bulunan müşterileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3bf82-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="3bf82-142">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3bf82-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="3bf82-143">Deneyebileceğiniz bazı diğer filtreler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3bf82-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="3bf82-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf82-144">See also</span></span>

- [<span data-ttu-id="3bf82-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="3bf82-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3bf82-146">Sorgular</span><span class="sxs-lookup"><span data-stu-id="3bf82-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3bf82-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3bf82-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="3bf82-148">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="3bf82-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
