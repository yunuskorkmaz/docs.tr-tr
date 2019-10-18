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
ms.openlocfilehash: ebf0ed1be8d74b60b7e626db996e7cefb1c01131
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524516"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="e8efc-102">Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8efc-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="e8efc-103">Dil ile tümleşik sorgu (LINQ) sorguları, veritabanı bilgilerine erişmeyi ve veritabanındaki değerleri değiştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e8efc-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="e8efc-104">Aşağıdaki örnek, SQL Server bir veritabanında bilgi alıp güncelleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8efc-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="e8efc-105">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8efc-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="e8efc-106">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8efc-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="e8efc-107">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e8efc-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="e8efc-108">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e8efc-108">To create a connection to a database</span></span>

1. <span data-ttu-id="e8efc-109">Visual Studio 'da, **Görünüm** menüsüne tıklayarak **Sunucu Gezgini** /**Veritabanı Gezgini** açın ve **Sunucu Gezgini** /**veritabanı Gezgini**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="e8efc-110">**Sunucu Gezgini** / veritabanı Gezgini **veri bağlantıları** ' na sağtıklayın ve **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="e8efc-111">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="e8efc-112">LINQ to SQL dosya içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="e8efc-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="e8efc-113">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="e8efc-114">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="e8efc-115">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="e8efc-116">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="e8efc-117">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="e8efc-118">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-118">Click **Add**.</span></span> <span data-ttu-id="e8efc-119">Nesne İlişkisel Tasarımcısı (O/R Designer) `northwind.dbml` dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="e8efc-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="e8efc-120">Sorguya tablo eklemek ve tasarımcıya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="e8efc-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="e8efc-121">**Sunucu Gezgini** /**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="e8efc-122">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="e8efc-123">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz `northwind.dbml` dosyasına çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8efc-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="e8efc-124">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="e8efc-125">Tasarımcı projeniz için yeni bir müşteri nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8efc-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="e8efc-126">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="e8efc-127">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="e8efc-128">Veritabanını değiştirmek ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="e8efc-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="e8efc-129">**Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="e8efc-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="e8efc-130">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projenize bir <xref:System.Data.Linq.DataContext> nesnesi ekledi.</span><span class="sxs-lookup"><span data-stu-id="e8efc-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="e8efc-131">Bu nesne, Customers tablosuna erişmek için kullanabileceğiniz kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="e8efc-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="e8efc-132">Ayrıca, bir yerel müşteri nesnesini ve tablo için bir müşteriler koleksiyonunu tanımlayan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="e8efc-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="e8efc-133">Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e8efc-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="e8efc-134">Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext` olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8efc-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="e8efc-135">Kodunuzda <xref:System.Data.Linq.DataContext> nesnesinin bir örneğini oluşturabilir ve bu, O/R Tasarımcısı tarafından belirtilen müşteriler koleksiyonunu sorgulayabilir ve değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8efc-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="e8efc-136">Müşteriler koleksiyonunda yaptığınız değişiklikler, <xref:System.Data.Linq.DataContext> nesnesinin <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemini çağırarak, veritabanına yansıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="e8efc-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="e8efc-137">@No__t_1 bir özellik olarak sunulan Customers tablosunu sorgulamak üzere <xref:System.Windows.Forms.Form.Load> olayına kod eklemek için Windows formunu çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="e8efc-138">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e8efc-138">Add the following code:</span></span>

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

3. <span data-ttu-id="e8efc-139">**Araç kutusundan**üç <xref:System.Windows.Forms.Button> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="e8efc-140">İlk `Button` denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="e8efc-140">Select the first `Button` control.</span></span> <span data-ttu-id="e8efc-141">**Özellikler** penceresinde, `Button` denetiminin `Name` `AddButton` ve `Text` `Add` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="e8efc-142">İkinci düğmeyi seçin ve `Name` özelliğini `UpdateButton` ve `Text` özelliğini `Update` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="e8efc-143">Üçüncü düğmesini seçin ve `Name` özelliğini `DeleteButton` ve `Text` özelliğini `Delete` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="e8efc-144">@No__t_1 olayına kod eklemek için **Ekle** düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="e8efc-145">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e8efc-145">Add the following code:</span></span>

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

5. <span data-ttu-id="e8efc-146">@No__t_1 olayına kod eklemek için **Güncelleştir** düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="e8efc-147">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e8efc-147">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="e8efc-148">@No__t_1 olayına kod eklemek için **Sil** düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="e8efc-149">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e8efc-149">Add the following code:</span></span>

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

7. <span data-ttu-id="e8efc-150">Projenizi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-150">Press F5 to run your project.</span></span> <span data-ttu-id="e8efc-151">Yeni bir kayıt eklemek için **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="e8efc-152">Yeni kaydı değiştirmek için **Güncelleştir** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="e8efc-153">Yeni kaydı silmek için **Sil** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8efc-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8efc-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8efc-154">See also</span></span>

- [<span data-ttu-id="e8efc-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="e8efc-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="e8efc-156">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e8efc-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="e8efc-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e8efc-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="e8efc-158">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="e8efc-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="e8efc-159">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="e8efc-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
