---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sorgu sonuçlarını LINQ kullanarak filtreleme (Visual Basic)'
title: 'Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Sıralama'
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
ms.openlocfilehash: b3f861d9a7fb7b601606f190ad3bfbeef054cad7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422813"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="add0c-103">Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="add0c-103">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="add0c-104">Language-Integrated sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="add0c-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="add0c-105">Aşağıdaki örnek, bir SQL Server veritabanına yönelik sorgular gerçekleştiren yeni bir uygulamanın nasıl oluşturulduğunu ve yan tümcesini kullanarak belirli bir değere göre sonuçları filtreleyeceğini gösterir `Where` .</span><span class="sxs-lookup"><span data-stu-id="add0c-105">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="add0c-106">Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="add0c-106">For more information, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="add0c-107">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="add0c-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="add0c-108">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add0c-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="add0c-109">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="add0c-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="add0c-110">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="add0c-110">To create a connection to a database</span></span>

1. <span data-ttu-id="add0c-111">Visual Studio 'da,  /  Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini  açın.</span><span class="sxs-lookup"><span data-stu-id="add0c-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="add0c-112">**Sunucu Gezgini** veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın /  ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add0c-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="add0c-113">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="add0c-113">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="add0c-114">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="add0c-114">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="add0c-115">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add0c-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="add0c-116">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="add0c-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="add0c-117">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add0c-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="add0c-118">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="add0c-118">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="add0c-119">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="add0c-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="add0c-120">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add0c-120">Click **Add**.</span></span> <span data-ttu-id="add0c-121">Northwind. dbml dosyası için Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.</span><span class="sxs-lookup"><span data-stu-id="add0c-121">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="add0c-122">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="add0c-122">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="add0c-123">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="add0c-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="add0c-124">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="add0c-124">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="add0c-125">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add0c-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="add0c-126">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="add0c-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="add0c-127">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="add0c-127">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="add0c-128">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="add0c-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="add0c-129">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="add0c-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="add0c-130">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="add0c-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="add0c-131">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="add0c-131">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="add0c-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="add0c-132">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="add0c-133">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="add0c-133">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="add0c-134">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="add0c-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="add0c-135">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="add0c-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="add0c-136">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="add0c-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="add0c-137">Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="add0c-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="add0c-138"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="add0c-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="add0c-139">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="add0c-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="add0c-140">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add0c-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="add0c-141">`Load`Veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için olaya aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="add0c-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="add0c-142">Sorgu sonuçlara filtre uygular ve yalnızca içinde bulunan müşterileri döndürür `London` .</span><span class="sxs-lookup"><span data-stu-id="add0c-142">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="add0c-143">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="add0c-143">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="add0c-144">Deneyebileceğiniz bazı diğer filtreler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="add0c-144">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="add0c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="add0c-145">See also</span></span>

- [<span data-ttu-id="add0c-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="add0c-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="add0c-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="add0c-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="add0c-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="add0c-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="add0c-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="add0c-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
