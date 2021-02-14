---
description: 'Daha fazla bilgi edinin: nasıl yapılır: LINQ kullanarak veritabanındaki verileri değiştirme (Visual Basic)'
title: 'Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme'
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
ms.openlocfilehash: b58ca542fbc6f4d63705e45b53edc8ded83ab88b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422776"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="15ef8-103">Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15ef8-103">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="15ef8-104">Language-Integrated Query (LINQ) sorguları, veritabanı bilgilerine erişmeyi ve veritabanındaki değerleri değiştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="15ef8-104">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="15ef8-105">Aşağıdaki örnek, SQL Server bir veritabanında bilgi alıp güncelleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="15ef8-105">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="15ef8-106">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15ef8-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="15ef8-107">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15ef8-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="15ef8-108">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="15ef8-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="15ef8-109">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="15ef8-109">To create a connection to a database</span></span>

1. <span data-ttu-id="15ef8-110">Visual Studio 'da,  / **Görünüm** menüsüne tıklayarak Sunucu Gezgini **veritabanı Gezgini** açın ve **Sunucu Gezgini** / **veritabanı Gezgini**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="15ef8-111">**Sunucu Gezgini** veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / ve **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="15ef8-112">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-112">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="15ef8-113">LINQ to SQL dosya içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="15ef8-113">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="15ef8-114">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="15ef8-115">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="15ef8-116">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="15ef8-117">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="15ef8-118">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="15ef8-119">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-119">Click **Add**.</span></span> <span data-ttu-id="15ef8-120">Dosya için Nesne İlişkisel Tasarımcısı (O/R Designer) açılır `northwind.dbml` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-120">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="15ef8-121">Sorguya tablo eklemek ve tasarımcıya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="15ef8-121">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="15ef8-122">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="15ef8-123">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="15ef8-124">O/R tasarımcısını kapattıysanız, `northwind.dbml` daha önce eklediğiniz dosyaya çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15ef8-124">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="15ef8-125">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-125">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="15ef8-126">Tasarımcı projeniz için yeni bir müşteri nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15ef8-126">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="15ef8-127">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-127">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="15ef8-128">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-128">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="15ef8-129">Veritabanını değiştirmek ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="15ef8-129">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="15ef8-130">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="15ef8-130">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="15ef8-131">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projenize bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="15ef8-131">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="15ef8-132">Bu nesne, Customers tablosuna erişmek için kullanabileceğiniz kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="15ef8-132">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="15ef8-133">Ayrıca, bir yerel müşteri nesnesini ve tablo için bir müşteriler koleksiyonunu tanımlayan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="15ef8-133">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="15ef8-134"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="15ef8-134">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="15ef8-135">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-135">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="15ef8-136">Kodunuzda nesnenin bir örneğini oluşturabilir ve, <xref:System.Data.Linq.DataContext> O/R Tasarımcısı tarafından belirtilen müşteriler koleksiyonunu sorgulayabilir ve değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15ef8-136">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="15ef8-137">Müşteriler koleksiyonunda yaptığınız değişiklikler, nesne yöntemini çağırarak gönderene kadar veritabanına yansıtılmaz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="15ef8-137">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="15ef8-138">' <xref:System.Windows.Forms.Form.Load> In bir özelliği olarak sunulan Customers tablosunu sorgulamak üzere olaya kod eklemek Için Windows formunu çift tıklayın <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="15ef8-138">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="15ef8-139">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="15ef8-139">Add the following code:</span></span>

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

3. <span data-ttu-id="15ef8-140">**Araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimi form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="15ef8-140">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="15ef8-141">İlk denetimi seçin `Button` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-141">Select the first `Button` control.</span></span> <span data-ttu-id="15ef8-142">**Özellikler** penceresinde, denetiminin öğesini ile `Name` olarak ayarlayın `Button` `AddButton` `Text` `Add` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-142">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="15ef8-143">İkinci düğmeyi seçin ve `Name` özelliğini `UpdateButton` ve `Text` özelliğini olarak ayarlayın `Update` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-143">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="15ef8-144">Üçüncü düğmesini seçin ve `Name` özelliğini `DeleteButton` ve `Text` özelliğini olarak ayarlayın `Delete` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-144">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="15ef8-145">Olayına kod eklemek için **Ekle** düğmesine çift tıklayın `Click` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-145">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="15ef8-146">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="15ef8-146">Add the following code:</span></span>

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

5. <span data-ttu-id="15ef8-147">Olayına kod eklemek için **Güncelleştir** düğmesine çift tıklayın `Click` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-147">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="15ef8-148">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="15ef8-148">Add the following code:</span></span>

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

6. <span data-ttu-id="15ef8-149">Olayına kod eklemek için **Sil** düğmesine çift tıklayın `Click` .</span><span class="sxs-lookup"><span data-stu-id="15ef8-149">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="15ef8-150">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="15ef8-150">Add the following code:</span></span>

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

7. <span data-ttu-id="15ef8-151">Projenizi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-151">Press F5 to run your project.</span></span> <span data-ttu-id="15ef8-152">Yeni bir kayıt eklemek için **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-152">Click **Add** to add a new record.</span></span> <span data-ttu-id="15ef8-153">Yeni kaydı değiştirmek için **Güncelleştir** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-153">Click **Update** to modify the new record.</span></span> <span data-ttu-id="15ef8-154">Yeni kaydı silmek için **Sil** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="15ef8-154">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="15ef8-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ef8-155">See also</span></span>

- [<span data-ttu-id="15ef8-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="15ef8-156">LINQ</span></span>](index.md)
- [<span data-ttu-id="15ef8-157">Sorgular</span><span class="sxs-lookup"><span data-stu-id="15ef8-157">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="15ef8-158">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="15ef8-158">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="15ef8-159">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="15ef8-159">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="15ef8-160">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="15ef8-160">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
