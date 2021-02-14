---
description: 'Daha fazla bilgi edinin: nasıl yapılır: LINQ kullanarak sayma, toplama veya ortalama veri (Visual Basic)'
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
ms.openlocfilehash: 1759a2f990c2e61a862d032f2a09f29f65a05103
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422814"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="c2822-103">Nasıl yapılır: LINQ Kullanarak Count, Sum veya Average Verisi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2822-103">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="c2822-104">Language-Integrated sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c2822-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="c2822-105">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2822-105">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="c2822-106">Örnek, `Aggregate` ve yan tümceleri kullanılarak sonuçların sayımlarını, toplamlarını ve ortalamasını verir `Group By` .</span><span class="sxs-lookup"><span data-stu-id="c2822-106">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="c2822-107">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c2822-107">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="c2822-108">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2822-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="c2822-109">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2822-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="c2822-110">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c2822-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="c2822-111">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c2822-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="c2822-112">Visual Studio 'da,  /  Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini  açın.</span><span class="sxs-lookup"><span data-stu-id="c2822-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="c2822-113">**Sunucu Gezgini** veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın /  ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="c2822-114">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="c2822-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="c2822-115">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="c2822-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="c2822-116">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="c2822-117">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2822-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="c2822-118">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="c2822-119">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c2822-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="c2822-120">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c2822-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="c2822-121">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-121">Click **Add**.</span></span> <span data-ttu-id="c2822-122">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="c2822-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="c2822-123">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="c2822-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="c2822-124">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="c2822-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="c2822-125">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c2822-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="c2822-126">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2822-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="c2822-127">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c2822-127">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="c2822-128">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c2822-128">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="c2822-129">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2822-129">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="c2822-130">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-130">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="c2822-131">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2822-131">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="c2822-132">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="c2822-132">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="c2822-133">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c2822-133">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="c2822-134">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="c2822-134">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="c2822-135">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="c2822-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="c2822-136">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="c2822-136">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="c2822-137">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="c2822-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="c2822-138">Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin.</span><span class="sxs-lookup"><span data-stu-id="c2822-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="c2822-139"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c2822-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="c2822-140">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="c2822-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="c2822-141">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2822-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="c2822-142">Aşağıdaki kodu olayına ekleyerek, ' `Load` ın özellikleri olarak gösterilen tabloları <xref:System.Data.Linq.DataContext> ve sayı, toplam değerini ve sonuçların ortalamasını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="c2822-142">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="c2822-143">Örnek, `Aggregate` tek bir sonuç sorgulamak için yan tümcesini ve `Group By` gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2822-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="c2822-144">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c2822-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2822-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2822-145">See also</span></span>

- [<span data-ttu-id="c2822-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="c2822-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="c2822-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c2822-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="c2822-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c2822-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c2822-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="c2822-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="c2822-150">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c2822-150">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="c2822-151">Group by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c2822-151">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
