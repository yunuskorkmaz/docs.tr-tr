---
title: "Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74a8148ad9572ee217921697e620791c85ff93f7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="1e15e-102">Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e15e-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="1e15e-103">Dil ile tümleşik sorgu (LINQ) Veritabanı bilgilerine erişmek ve sorguları yürütün daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1e15e-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="1e15e-104">Aşağıdaki örnek, bir SQL Server veritabanı sorguları gerçekleştirir yeni bir uygulama oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e15e-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="1e15e-105">Örnek sonuçlar için minimum ve maksimum değerleri kullanarak belirler `Aggregate` ve `Group By` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="1e15e-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="1e15e-106">Daha fazla bilgi için bkz: [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Grup By yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1e15e-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="1e15e-107">Bu konudaki örnekler Northwind örnek veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e15e-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1e15e-108">Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="1e15e-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="1e15e-109">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1e15e-109">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1e15e-110">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e15e-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="1e15e-111">Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1e15e-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="1e15e-112">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1e15e-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="1e15e-113">Northwind örnek veritabanı için geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="1e15e-114">Bir LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="1e15e-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="1e15e-115">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="1e15e-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1e15e-116">Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.</span><span class="sxs-lookup"><span data-stu-id="1e15e-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="1e15e-117">Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1e15e-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1e15e-118">Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="1e15e-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="1e15e-119">Dosya adı `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1e15e-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1e15e-120">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1e15e-120">Click **Add**.</span></span> <span data-ttu-id="1e15e-121">Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) northwind.dbml dosyası için açıldı.</span><span class="sxs-lookup"><span data-stu-id="1e15e-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="1e15e-122">O/R Tasarımcısı sorgulamak için tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="1e15e-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="1e15e-123">İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1e15e-124">Genişletme **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="1e15e-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1e15e-125">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e15e-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="1e15e-126">Müşteriler tablosunu tıklayın ve tasarımcı sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="1e15e-127">Siparişler tablosundaki tıklayın ve tasarımcı sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1e15e-128">Tasarımcı oluşturur Yeni `Customer` ve `Order` projeniz için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1e15e-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="1e15e-129">Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="1e15e-130">IntelliSense, örneğin, gösterecektir `Customer` nesnesi bir `Orders` özelliği tüm siparişler için o müşteri ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="1e15e-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="1e15e-131">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="1e15e-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="1e15e-132">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1e15e-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="1e15e-133">Veritabanını sorgulamak ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="1e15e-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="1e15e-134">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="1e15e-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="1e15e-135">Kodu eklemek için Form1 çift `Load` olay formunun.</span><span class="sxs-lookup"><span data-stu-id="1e15e-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="1e15e-136">O/R Tasarımcısı tabloları eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="1e15e-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="1e15e-137">Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek zorunda kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1e15e-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="1e15e-138"><xref:System.Data.Linq.DataContext> Nesne projenizi adlı için .dbml dosyanızı adına dayalı.</span><span class="sxs-lookup"><span data-stu-id="1e15e-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1e15e-139">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="1e15e-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1e15e-140">Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="1e15e-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="1e15e-141">Aşağıdaki kodu ekleyin `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="1e15e-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="1e15e-142">Bu kod, veri bağlamı özellikleri olarak sunulur ve sonuçları için minimum ve maksimum değerleri belirleyen tabloları sorgular.</span><span class="sxs-lookup"><span data-stu-id="1e15e-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="1e15e-143">Örnek kullanır kendisinin `Aggregate` yan tümcesi sorgulamak için tek bir sonuç ve `Group By` için ortalama göstermek için yan tümcesi gruplandırılmış sonuçları.</span><span class="sxs-lookup"><span data-stu-id="1e15e-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  <span data-ttu-id="1e15e-144">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e15e-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e15e-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e15e-145">See Also</span></span>  
 [<span data-ttu-id="1e15e-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="1e15e-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="1e15e-147">Sorguları</span><span class="sxs-lookup"><span data-stu-id="1e15e-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1e15e-148">LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="1e15e-148">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="1e15e-149">DataContext yöntemleri (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="1e15e-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
