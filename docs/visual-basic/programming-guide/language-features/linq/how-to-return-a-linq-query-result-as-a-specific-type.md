---
title: 'Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 720660153cb357c11168ab45ebf8343559faf82a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393252"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="a0747-102">Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0747-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="a0747-103">Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a0747-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="a0747-104">Varsayılan olarak, LINQ sorguları anonim bir tür nesnelerin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0747-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="a0747-105">Sorgu kullanarak belirli bir türün bir liste döndürme belirtebilirsiniz `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a0747-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="a0747-106">Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştirir ve sonuçları belirli bir adlandırılmış tür olarak projelerde yeni bir uygulama oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0747-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="a0747-107">Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a0747-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="a0747-108">Bu konudaki örnekler, Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0747-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="a0747-109">Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0747-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="a0747-110">Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a0747-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="a0747-111">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a0747-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="a0747-112">Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a0747-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="a0747-113">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a0747-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="a0747-114">Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0747-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="a0747-115">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="a0747-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="a0747-116">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="a0747-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="a0747-117">Visual Basic seçin **Windows Forms uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="a0747-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="a0747-118">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a0747-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="a0747-119">Seçin **LINQ to SQL sınıfları** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="a0747-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="a0747-120">Dosya adı `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="a0747-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="a0747-121">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a0747-121">Click **Add**.</span></span> <span data-ttu-id="a0747-122">Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="a0747-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="a0747-123">O/R Tasarımcısı için sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="a0747-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="a0747-124">İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="a0747-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="a0747-125">Genişletin **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="a0747-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="a0747-126">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0747-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="a0747-127">Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="a0747-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="a0747-128">Tasarımcı yeni bir oluşturur `Customer` projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="a0747-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="a0747-129">Sorgu sonucu olarak yansıtabilirsiniz `Customer` türü veya oluşturduğunuz bir tür.</span><span class="sxs-lookup"><span data-stu-id="a0747-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="a0747-130">Bu örnek, daha sonraki bir yordamda yeni türü oluşturun ve bu tür bir sorgu sonucunda proje.</span><span class="sxs-lookup"><span data-stu-id="a0747-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="a0747-131">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="a0747-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="a0747-132">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a0747-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="a0747-133">Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="a0747-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="a0747-134">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0747-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="a0747-135">Form1 Form1 sınıfını değiştirmek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0747-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="a0747-136">Sonra `End Class` deyimine Form1 sınıfı oluşturmak için aşağıdaki kodu bir `CustomerInfo` Bu örnek için sorgu sonuçlarını tutmak için türü.</span><span class="sxs-lookup"><span data-stu-id="a0747-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  <span data-ttu-id="a0747-137">Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projenize nesne.</span><span class="sxs-lookup"><span data-stu-id="a0747-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="a0747-138">Bu nesne bu tablolara erişen ve ayrı nesneler ve Koleksiyonlar her tablo için erişmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="a0747-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="a0747-139"><xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı.</span><span class="sxs-lookup"><span data-stu-id="a0747-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="a0747-140">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a0747-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="a0747-141">Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="a0747-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="a0747-142">İçinde `Load` olay Form1 sınıfın veri Bağlamınızı özellikleri olarak gösterilen tablolarını sorgulamak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0747-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="a0747-143">`Select` Sorgu yan tümcesinde yeni bir oluşturur `CustomerInfo` sorgu sonucunun her öğe için anonim bir tür yerine türü.</span><span class="sxs-lookup"><span data-stu-id="a0747-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  <span data-ttu-id="a0747-144">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a0747-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0747-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0747-145">See Also</span></span>  
 [<span data-ttu-id="a0747-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="a0747-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="a0747-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="a0747-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="a0747-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a0747-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="a0747-149">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="a0747-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
