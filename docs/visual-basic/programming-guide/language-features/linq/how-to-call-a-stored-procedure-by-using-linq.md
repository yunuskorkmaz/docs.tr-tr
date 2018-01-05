---
title: "Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bb7b970d42a44ad925883b7a935aae386b1f1d5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="61b60-102">Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b60-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="61b60-103">Dil ile tümleşik sorgu (LINQ) veritabanı gibi depolanan nesneler yordamlarını içeren veritabanı bilgileri erişimi kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="61b60-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="61b60-104">Aşağıdaki örnek bir SQL Server veritabanı içinde saklı yordamı çağıran bir uygulamasının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61b60-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="61b60-105">Örnek veritabanında iki farklı saklı yordam çağrısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61b60-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="61b60-106">Her bir yordam bir sorgunun sonuçlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="61b60-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="61b60-107">Bir yordam giriş parametreleri alır ve diğer yordamı parametre almaz.</span><span class="sxs-lookup"><span data-stu-id="61b60-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="61b60-108">Bu konudaki örnekler Northwind örnek veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="61b60-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="61b60-109">Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="61b60-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="61b60-110">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="61b60-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="61b60-111">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="61b60-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="61b60-112">Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="61b60-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="61b60-113">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer** ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="61b60-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="61b60-114">Northwind örnek veritabanı için geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="61b60-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="61b60-115">Bir LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="61b60-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="61b60-116">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="61b60-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="61b60-117">Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.</span><span class="sxs-lookup"><span data-stu-id="61b60-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="61b60-118">Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="61b60-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="61b60-119">Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="61b60-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="61b60-120">Dosya adı `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="61b60-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="61b60-121">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="61b60-121">Click **Add**.</span></span> <span data-ttu-id="61b60-122">Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) northwind.dbml dosyası için açıldı.</span><span class="sxs-lookup"><span data-stu-id="61b60-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="61b60-123">Saklı yordamlar için O/R Tasarımcısı eklemek için</span><span class="sxs-lookup"><span data-stu-id="61b60-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="61b60-124">İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="61b60-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="61b60-125">Genişletme **saklı yordamlar** klasör.</span><span class="sxs-lookup"><span data-stu-id="61b60-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="61b60-126">O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61b60-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="61b60-127">Tıklatın **yıla göre satış** saklı yordamı ve tasarımcı sağ bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="61b60-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="61b60-128">Tıklatın **on en pahalı ürün** saklı yordam, Tasarımcı sağ bölmesinde sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="61b60-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="61b60-129">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="61b60-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="61b60-130">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="61b60-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="61b60-131">Saklı yordamlar sonuçlarını görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="61b60-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="61b60-132">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="61b60-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="61b60-133">Form1 kodu eklemek için çift tıklayın, `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="61b60-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="61b60-134">O/R Tasarımcısı saklı yordamlar eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne.</span><span class="sxs-lookup"><span data-stu-id="61b60-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="61b60-135">Bu nesne, bu yordamlar erişmek için gerekli kod içerir.</span><span class="sxs-lookup"><span data-stu-id="61b60-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="61b60-136"><xref:System.Data.Linq.DataContext> Nesne proje adlı için .dbml dosya adına dayalı.</span><span class="sxs-lookup"><span data-stu-id="61b60-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="61b60-137">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="61b60-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="61b60-138">Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> kod ve çağrı de O/R tasarımcısı tarafından belirtilen saklı yordam yöntemlerinin.</span><span class="sxs-lookup"><span data-stu-id="61b60-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="61b60-139">Bağlamak için <xref:System.Windows.Forms.DataGridView> nesne çağırarak hemen çalıştırılacak sorgu zorlamak yaptığınız <xref:System.Linq.Enumerable.ToList%2A> saklı yordamı sonuçlarını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61b60-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="61b60-140">Aşağıdaki kodu ekleyin `Load` veri içeriğiniz için yöntemleri olarak sunulan saklı yordamlardan birini çağrılacak olay.</span><span class="sxs-lookup"><span data-stu-id="61b60-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  <span data-ttu-id="61b60-141">Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="61b60-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b60-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61b60-142">See Also</span></span>  
 [<span data-ttu-id="61b60-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="61b60-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="61b60-144">Sorgular</span><span class="sxs-lookup"><span data-stu-id="61b60-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="61b60-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="61b60-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="61b60-146">DataContext yöntemleri (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="61b60-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="61b60-147">Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın</span><span class="sxs-lookup"><span data-stu-id="61b60-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
