---
title: 'Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 02aaf2924c6230615d7d1cbcceac72265419b541
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402902"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="0617a-102">Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0617a-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="0617a-103">Dil ile tümleşik sorgu (LINQ) sorguları Veritabanı bilgilerine erişmek ve veritabanını değerleri değiştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0617a-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="0617a-104">Aşağıdaki örnek, bir SQL Server veritabanında alır, yeni bir uygulama oluşturma ve güncelleştirme bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0617a-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="0617a-105">Bu konudaki örnekler, Northwind örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0617a-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="0617a-106">Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0617a-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="0617a-107">Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="0617a-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="0617a-108">Bir veritabanına bir bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0617a-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="0617a-109">Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **görünümü** menüsüne ve ardından **SunucuGezgini** / **Veritabanı Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0617a-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="0617a-110">Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini**, tıklatıp **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="0617a-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="0617a-111">Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="0617a-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="0617a-112">Bir proje ile LINQ to SQL dosyası eklemek için</span><span class="sxs-lookup"><span data-stu-id="0617a-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="0617a-113">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="0617a-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="0617a-114">Visual Basic seçin **Windows Forms uygulaması** proje türü.</span><span class="sxs-lookup"><span data-stu-id="0617a-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="0617a-115">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="0617a-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="0617a-116">Seçin **LINQ to SQL sınıfları** öğe şablonu.</span><span class="sxs-lookup"><span data-stu-id="0617a-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="0617a-117">Dosya adı `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="0617a-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="0617a-118">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0617a-118">Click **Add**.</span></span> <span data-ttu-id="0617a-119">Object Relational Designer (O/R Tasarımcısı) için açıldığında `northwind.dbml` dosya.</span><span class="sxs-lookup"><span data-stu-id="0617a-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="0617a-120">Sorgu ve tasarımcıya değiştirmek için tablolar eklemek için</span><span class="sxs-lookup"><span data-stu-id="0617a-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="0617a-121">İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin.</span><span class="sxs-lookup"><span data-stu-id="0617a-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="0617a-122">Genişletin **tabloları** klasör.</span><span class="sxs-lookup"><span data-stu-id="0617a-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="0617a-123">O/R Tasarımcısı kapattıysanız, onu çift tıklayarak açabilirsiniz `northwind.dbml` daha önce eklediğiniz dosya.</span><span class="sxs-lookup"><span data-stu-id="0617a-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="0617a-124">Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0617a-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="0617a-125">Tasarımcı, projeniz için yeni bir müşteri nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0617a-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="0617a-126">Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="0617a-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="0617a-127">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0617a-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="0617a-128">Veritabanını değiştirme ve sonuçları görüntülemek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="0617a-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="0617a-129">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.</span><span class="sxs-lookup"><span data-stu-id="0617a-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="0617a-130">Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projenize nesne.</span><span class="sxs-lookup"><span data-stu-id="0617a-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="0617a-131">Bu nesne, Müşteriler tablosunu erişmek için kullanabileceğiniz kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="0617a-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="0617a-132">Ayrıca, yerel bir müşteri nesnesi ve bir tablo için müşteri koleksiyonunun tanımlayan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="0617a-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="0617a-133"><xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı.</span><span class="sxs-lookup"><span data-stu-id="0617a-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="0617a-134">Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="0617a-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="0617a-135">Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> kodunuz ve sorgu nesnesi ve O/R tasarımcısı tarafından belirtilen müşteri koleksiyonunun değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0617a-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="0617a-136">Müşteriler koleksiyona yaptığınız değişiklikler değil yansıtılır veritabanında bunları çağırarak göndermek kadar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi <xref:System.Data.Linq.DataContext> nesne.</span><span class="sxs-lookup"><span data-stu-id="0617a-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="0617a-137">Windows için kod eklemek için Form1, formu <xref:System.Windows.Forms.Form.Load> sorgu Müşteriler tablosu için olay özelliği olarak sunulan, <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="0617a-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="0617a-138">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0617a-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="0617a-139">Gelen **araç kutusu**, üç sürükleyin <xref:System.Windows.Forms.Button> form üzerine denetimler.</span><span class="sxs-lookup"><span data-stu-id="0617a-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="0617a-140">İlk seçin `Button` denetimi.</span><span class="sxs-lookup"><span data-stu-id="0617a-140">Select the first `Button` control.</span></span> <span data-ttu-id="0617a-141">İçinde **özellikleri** penceresinde `Name` , `Button` denetimini `AddButton` ve `Text` için `Add`.</span><span class="sxs-lookup"><span data-stu-id="0617a-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="0617a-142">İkinci bir düğme seçip ayarlayın `Name` özelliğini `UpdateButton` ve `Text` özelliğini `Update`.</span><span class="sxs-lookup"><span data-stu-id="0617a-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="0617a-143">Üçüncü düğmeyi seçin ve ayarlayın `Name` özelliğini `DeleteButton` ve `Text` özelliğini `Delete`.</span><span class="sxs-lookup"><span data-stu-id="0617a-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="0617a-144">Çift **Ekle** kodu eklemek için Ekle düğmesine kendi `Click` olay.</span><span class="sxs-lookup"><span data-stu-id="0617a-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="0617a-145">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0617a-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="0617a-146">Çift **güncelleştirme** kodu eklemek için Ekle düğmesine kendi `Click` olay.</span><span class="sxs-lookup"><span data-stu-id="0617a-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="0617a-147">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0617a-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="0617a-148">Çift **Sil** kodu eklemek için Ekle düğmesine kendi `Click` olay.</span><span class="sxs-lookup"><span data-stu-id="0617a-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="0617a-149">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0617a-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="0617a-150">Projenizi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0617a-150">Press F5 to run your project.</span></span> <span data-ttu-id="0617a-151">Tıklayın **Ekle** yeni bir kayıt eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0617a-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="0617a-152">Tıklayın **güncelleştirme** yeni bir kaydı değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0617a-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="0617a-153">Tıklayın **Sil** yeni kaydı silinemedi.</span><span class="sxs-lookup"><span data-stu-id="0617a-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0617a-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0617a-154">See Also</span></span>  
 [<span data-ttu-id="0617a-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="0617a-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="0617a-156">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0617a-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="0617a-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0617a-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="0617a-158">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="0617a-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="0617a-159">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="0617a-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
