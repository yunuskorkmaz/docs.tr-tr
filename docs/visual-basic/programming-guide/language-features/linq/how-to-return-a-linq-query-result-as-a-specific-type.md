---
title: "Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c46799dea71a727b47a79f9fc108d676b253513
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="afa77-102">Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa77-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="afa77-103">Dil ile tümleşik sorgu (LINQ) Veritabanı bilgilerine erişmek ve sorguları yürütün daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="afa77-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="afa77-104">Varsayılan olarak, LINQ sorguları anonim bir tür olarak nesnelerin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="afa77-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="afa77-105">Bir sorgu kullanarak belirli bir tür listesini döndürmek belirtebilirsiniz `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="afa77-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="afa77-106">Aşağıdaki örnek, bir SQL Server veritabanı sorguları gerçekleştirir ve sonuçları belirli bir adlandırılmış tür olarak projeleri yeni bir uygulama oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="afa77-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="afa77-107">Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afa77-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="afa77-108">Bu konudaki örnekler Northwind örnek veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="afa77-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="afa77-109">Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="afa77-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="afa77-110">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="afa77-110">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="afa77-111">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="afa77-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="afa77-112">Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="afa77-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="afa77-113">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="afa77-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="afa77-114">Northwind örnek veritabanı için geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="afa77-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="afa77-115">Bir LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="afa77-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="afa77-116">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="afa77-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="afa77-117">Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.</span><span class="sxs-lookup"><span data-stu-id="afa77-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="afa77-118">Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="afa77-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="afa77-119">Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="afa77-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="afa77-120">Dosya adı `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="afa77-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="afa77-121">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="afa77-121">Click **Add**.</span></span> <span data-ttu-id="afa77-122">Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) northwind.dbml dosyası için açıldı.</span><span class="sxs-lookup"><span data-stu-id="afa77-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="afa77-123">O/R Tasarımcısı sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="afa77-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="afa77-124">İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="afa77-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="afa77-125">Genişletme **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="afa77-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="afa77-126">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afa77-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="afa77-127">Müşteriler tablosunu tıklayın ve tasarımcı sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="afa77-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="afa77-128">Yeni bir tasarımcı oluşturur `Customer` projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="afa77-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="afa77-129">Sorgu sonucu olarak proje `Customer` türü veya oluşturduğunuz bir türü olarak.</span><span class="sxs-lookup"><span data-stu-id="afa77-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="afa77-130">Bu örnek daha sonraki bir yordamda yeni türü oluşturun ve bir sorgu sonucunun türü olarak proje.</span><span class="sxs-lookup"><span data-stu-id="afa77-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="afa77-131">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="afa77-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="afa77-132">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="afa77-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="afa77-133">Veritabanını sorgulamak ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="afa77-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="afa77-134">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="afa77-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="afa77-135">Form1 Form1 sınıfı değiştirmek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="afa77-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="afa77-136">Sonra `End Class` deyimine Form1 sınıfının oluşturmak için aşağıdaki kodu bir `CustomerInfo` Bu örnek için sorgu sonuçları tutacak türü.</span><span class="sxs-lookup"><span data-stu-id="afa77-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  <span data-ttu-id="afa77-137">O/R Tasarımcısı tabloları eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projenize nesnesi.</span><span class="sxs-lookup"><span data-stu-id="afa77-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="afa77-138">Bu nesne bu tablolar erişmek ve ayrı ayrı nesneleri ve koleksiyonları her tablo için erişim için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="afa77-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="afa77-139"><xref:System.Data.Linq.DataContext> Nesne projenizi adlı için .dbml dosyanızı adına dayalı.</span><span class="sxs-lookup"><span data-stu-id="afa77-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="afa77-140">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="afa77-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="afa77-141">Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="afa77-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="afa77-142">İçinde `Load` Form1 sınıfının olay verileri içeriğiniz özellikleri olarak sunulur tabloları sorgulamak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afa77-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="afa77-143">`Select` Sorgu yan tümcesinde yeni bir oluşturacak `CustomerInfo` sorgu sonucunun her öğe için anonim bir tür yerine türü.</span><span class="sxs-lookup"><span data-stu-id="afa77-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  <span data-ttu-id="afa77-144">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="afa77-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa77-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afa77-145">See Also</span></span>  
 [<span data-ttu-id="afa77-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="afa77-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="afa77-147">Sorguları</span><span class="sxs-lookup"><span data-stu-id="afa77-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="afa77-148">LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="afa77-148">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="afa77-149">DataContext yöntemleri (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="afa77-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
