---
title: 'Nasıl yapılır: LINQ Kullanarak Veritabanını Sorgulama'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: 60dbe3b4e164e266202cac4abaea009869d08cc4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075271"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="91044-102">Nasıl yapılır: LINQ Kullanarak Veritabanını Sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91044-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="91044-103">Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="91044-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="91044-104">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91044-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="91044-105">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91044-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="91044-106">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91044-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="91044-107">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="91044-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="91044-108">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="91044-108">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="91044-109">Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.</span><span class="sxs-lookup"><span data-stu-id="91044-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="91044-110">**Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91044-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="91044-111">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="91044-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="91044-112">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="91044-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="91044-113">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91044-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="91044-114">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="91044-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="91044-115">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91044-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="91044-116">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="91044-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="91044-117">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="91044-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="91044-118">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91044-118">Click **Add**.</span></span> <span data-ttu-id="91044-119">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="91044-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="91044-120">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="91044-120">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="91044-121">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="91044-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="91044-122">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="91044-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="91044-123">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91044-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="91044-124">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="91044-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="91044-125">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="91044-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="91044-126">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91044-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="91044-127">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="91044-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="91044-128">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="91044-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="91044-129">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="91044-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="91044-130">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="91044-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="91044-131">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="91044-131">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="91044-132">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="91044-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="91044-133">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="91044-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="91044-134">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="91044-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="91044-135">Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="91044-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="91044-136"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91044-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="91044-137">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="91044-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="91044-138">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91044-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="91044-139">`Load`Veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için olaya aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="91044-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#3)]  
  
4. <span data-ttu-id="91044-140">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91044-140">Press F5 to run your project and view the results.</span></span>  
  
5. <span data-ttu-id="91044-141">Deneyebileceğiniz bazı ek sorgular aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="91044-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="91044-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91044-142">See also</span></span>

- [<span data-ttu-id="91044-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="91044-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="91044-144">Sorgular</span><span class="sxs-lookup"><span data-stu-id="91044-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="91044-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="91044-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="91044-146">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="91044-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
