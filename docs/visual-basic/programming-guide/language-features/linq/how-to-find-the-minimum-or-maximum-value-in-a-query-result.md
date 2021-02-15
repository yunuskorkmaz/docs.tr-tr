---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: LINQ kullanarak bir sorgu sonucunda en küçük veya en büyük değeri bulma (Visual Basic)'
title: 'Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma'
ms.date: 07/20/2015
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
ms.openlocfilehash: e6337b61b01d720bd37390f61e4e285aa150ec3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422815"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="d39be-103">Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d39be-103">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="d39be-104">Language-Integrated sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d39be-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="d39be-105">Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d39be-105">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="d39be-106">Örnek, `Aggregate` ve yan tümceleri kullanılarak sonuçlar için en düşük ve en büyük değerleri belirler `Group By` .</span><span class="sxs-lookup"><span data-stu-id="d39be-106">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="d39be-107">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d39be-107">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="d39be-108">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d39be-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d39be-109">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d39be-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d39be-110">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d39be-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="d39be-111">Veritabanına bağlantı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d39be-111">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="d39be-112">Visual Studio 'da,  /  Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini  açın.</span><span class="sxs-lookup"><span data-stu-id="d39be-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="d39be-113">**Sunucu Gezgini** veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın /  ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d39be-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="d39be-114">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="d39be-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d39be-115">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="d39be-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="d39be-116">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d39be-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d39be-117">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d39be-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="d39be-118">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d39be-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d39be-119">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d39be-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="d39be-120">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d39be-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d39be-121">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d39be-121">Click **Add**.</span></span> <span data-ttu-id="d39be-122">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="d39be-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="d39be-123">O/R tasarımcısına sorguya tablo ekleme</span><span class="sxs-lookup"><span data-stu-id="d39be-123">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="d39be-124">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d39be-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d39be-125">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="d39be-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="d39be-126">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d39be-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="d39be-127">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d39be-127">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="d39be-128">Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d39be-128">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="d39be-129">Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d39be-129">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="d39be-130">Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d39be-130">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="d39be-131">Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d39be-131">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="d39be-132">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="d39be-132">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="d39be-133">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d39be-133">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="d39be-134">Veritabanını sorgulamak ve sonuçları göstermek için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="d39be-134">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="d39be-135">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="d39be-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="d39be-136">Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .</span><span class="sxs-lookup"><span data-stu-id="d39be-136">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="d39be-137">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="d39be-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="d39be-138">Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d39be-138">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="d39be-139"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d39be-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="d39be-140">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="d39be-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d39be-141">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d39be-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="d39be-142">Olayına aşağıdaki kodu ekleyin `Load` .</span><span class="sxs-lookup"><span data-stu-id="d39be-142">Add the following code to the `Load` event.</span></span> <span data-ttu-id="d39be-143">Bu kod, veri bağlamınızın özellikleri olarak gösterilen tabloları sorgular ve sonuçlar için en düşük ve en yüksek değerleri belirler.</span><span class="sxs-lookup"><span data-stu-id="d39be-143">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="d39be-144">Örnek, `Aggregate` tek bir sonuç sorgulamak için yan tümcesini ve `Group By` gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d39be-144">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="d39be-145">Projenizi çalıştırmak ve sonuçları görüntülemek için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d39be-145">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39be-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d39be-146">See also</span></span>

- [<span data-ttu-id="d39be-147">LINQ</span><span class="sxs-lookup"><span data-stu-id="d39be-147">LINQ</span></span>](index.md)
- [<span data-ttu-id="d39be-148">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d39be-148">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="d39be-149">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d39be-149">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d39be-150">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="d39be-150">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
