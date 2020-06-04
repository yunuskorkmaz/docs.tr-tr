---
title: 'Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: b451642a16f36c4f7fd19c853fdfd2282f5bede5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405036"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="2b428-102">Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b428-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="2b428-103">Dil ile tümleşik sorgu (LINQ), saklı yordamlar gibi veritabanı nesneleri dahil olmak üzere veritabanı bilgilerine erişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2b428-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="2b428-104">Aşağıdaki örnek, bir SQL Server veritabanında saklı yordam çağıran bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b428-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="2b428-105">Örnek, veritabanında iki farklı saklı yordamın nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b428-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="2b428-106">Her yordam bir sorgunun sonuçlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b428-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="2b428-107">Bir yordam giriş parametrelerini alır ve diğer yordam parametre almaz.</span><span class="sxs-lookup"><span data-stu-id="2b428-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="2b428-108">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b428-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="2b428-109">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b428-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="2b428-110">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="2b428-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="2b428-111">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2b428-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="2b428-112">Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.</span><span class="sxs-lookup"><span data-stu-id="2b428-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="2b428-113">**Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b428-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="2b428-114">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="2b428-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="2b428-115">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="2b428-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="2b428-116">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b428-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="2b428-117">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="2b428-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="2b428-118">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b428-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="2b428-119">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="2b428-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="2b428-120">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2b428-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="2b428-121">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b428-121">Click **Add**.</span></span> <span data-ttu-id="2b428-122">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="2b428-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="2b428-123">O/R tasarımcısına saklı yordamlar eklemek için</span><span class="sxs-lookup"><span data-stu-id="2b428-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="2b428-124">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="2b428-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="2b428-125">**Saklı yordamlar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="2b428-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="2b428-126">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b428-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="2b428-127">**Yıla göre satışlar** saklı yordamına tıklayın ve tasarımcı 'nın sağ bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2b428-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="2b428-128">**En pahalı on ürün** saklı yordamına tıklayın, tasarımcı 'nın sağ bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2b428-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="2b428-129">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="2b428-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="2b428-130">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2b428-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="2b428-131">Saklı yordamların sonuçlarını görüntüleyecek kodu eklemek için</span><span class="sxs-lookup"><span data-stu-id="2b428-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="2b428-132">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="2b428-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="2b428-133">Olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="2b428-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="2b428-134">O/R tasarımcısına saklı yordamlar eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="2b428-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="2b428-135">Bu nesne, bu yordamlara erişmeniz için sahip olmanız gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2b428-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="2b428-136"><xref:System.Data.Linq.DataContext>Projenin nesnesi. dbml dosyasının adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2b428-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="2b428-137">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="2b428-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="2b428-138">Kodunuzda bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen saklı yordam yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b428-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="2b428-139">Nesnesine bağlamak için <xref:System.Windows.Forms.DataGridView> , <xref:System.Linq.Enumerable.ToList%2A> saklı yordamın sonuçlarında yöntemi çağırarak sorguyu hemen yürütmeye zorlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2b428-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="2b428-140">`Load`Veri içeriğiniz için yöntemler olarak sunulan saklı yordamlardan birini çağırmak üzere olaya aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b428-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="2b428-141">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2b428-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b428-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b428-142">See also</span></span>

- [<span data-ttu-id="2b428-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="2b428-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="2b428-144">Sorgular</span><span class="sxs-lookup"><span data-stu-id="2b428-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="2b428-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2b428-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="2b428-146">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="2b428-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="2b428-147">Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="2b428-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
