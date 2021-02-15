---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: LINQ sorgu sonucunu belirli bir tür olarak döndürme (Visual Basic)'
title: 'Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 8abeb3b5f174b1671415cbb55f35952e3bc77e7d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425665"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="45b51-103">Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45b51-103">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>

<span data-ttu-id="45b51-104">Language-Integrated sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="45b51-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="45b51-105">Varsayılan olarak, LINQ sorguları bir nesne listesini anonim bir tür olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b51-105">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="45b51-106">Bir sorgunun yan tümcesini kullanarak belirli bir türün listesini döndürmesini de belirtebilirsiniz `Select` .</span><span class="sxs-lookup"><span data-stu-id="45b51-106">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="45b51-107">Aşağıdaki örnek, SQL Server veritabanına yönelik sorgular gerçekleştiren yeni bir uygulamanın nasıl oluşturulduğunu ve sonuçların belirli bir adlandırılmış tür olarak projede nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45b51-107">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="45b51-108">Daha fazla bilgi için bkz. [anonim türler](../objects-and-classes/anonymous-types.md) ve [seçim tümcesi](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="45b51-108">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="45b51-109">Bu konudaki örneklerde Northwind örnek veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b51-109">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="45b51-110">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b51-110">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="45b51-111">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="45b51-111">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="45b51-112">Bir veritabanına bağlantı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="45b51-112">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="45b51-113">Visual Studio 'da,  /  Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini  açın.</span><span class="sxs-lookup"><span data-stu-id="45b51-113">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="45b51-114">**Sunucu Gezgini** veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın /  ve ardından **bağlantı ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b51-114">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="45b51-115">Northwind örnek veritabanına geçerli bir bağlantı belirtin.</span><span class="sxs-lookup"><span data-stu-id="45b51-115">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="45b51-116">LINQ to SQL dosyası içeren bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="45b51-116">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="45b51-117">Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b51-117">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="45b51-118">Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="45b51-118">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="45b51-119">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b51-119">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="45b51-120">**LINQ to SQL sınıfları** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="45b51-120">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="45b51-121">Dosyayı `northwind.dbml` olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="45b51-121">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="45b51-122">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b51-122">Click **Add**.</span></span> <span data-ttu-id="45b51-123">Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.</span><span class="sxs-lookup"><span data-stu-id="45b51-123">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="45b51-124">O/R tasarımcısına sorguya tablo eklemek için</span><span class="sxs-lookup"><span data-stu-id="45b51-124">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="45b51-125">**Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin.</span><span class="sxs-lookup"><span data-stu-id="45b51-125">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="45b51-126">**Tablolar** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="45b51-126">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="45b51-127">O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b51-127">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="45b51-128">Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="45b51-128">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="45b51-129">Tasarımcı projeniz için yeni bir `Customer` nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45b51-129">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="45b51-130">Bir sorgu sonucunu `Customer` türü veya oluşturduğunuz bir tür olarak proje yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b51-130">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="45b51-131">Bu örnek, sonraki bir yordamda yeni bir tür oluşturacak ve bu tür olarak bir sorgu sonucunu proje oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="45b51-131">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="45b51-132">Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="45b51-132">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="45b51-133">Projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="45b51-133">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="45b51-134">Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="45b51-134">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="45b51-135">**Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.</span><span class="sxs-lookup"><span data-stu-id="45b51-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="45b51-136">Form1 sınıfını değiştirmek için Form1 ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b51-136">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="45b51-137">`End Class`Form1 sınıfının ifadesinden sonra, `CustomerInfo` Bu örneğe ilişkin sorgu sonuçlarını tutacak bir tür oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45b51-137">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="45b51-138">Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projenize bir nesne ekledi.</span><span class="sxs-lookup"><span data-stu-id="45b51-138">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="45b51-139">Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin.</span><span class="sxs-lookup"><span data-stu-id="45b51-139">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="45b51-140"><xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="45b51-140">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="45b51-141">Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="45b51-141">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="45b51-142">Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b51-142">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="45b51-143">`Load`Form1 sınıfının olayında, veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45b51-143">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="45b51-144">`Select`Sorgunun yan tümcesi, `CustomerInfo` Sorgu sonucunun her bir öğesi için anonim bir tür yerine yeni bir tür oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="45b51-144">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="45b51-145">Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="45b51-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b51-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45b51-146">See also</span></span>

- [<span data-ttu-id="45b51-147">LINQ</span><span class="sxs-lookup"><span data-stu-id="45b51-147">LINQ</span></span>](index.md)
- [<span data-ttu-id="45b51-148">Sorgular</span><span class="sxs-lookup"><span data-stu-id="45b51-148">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="45b51-149">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="45b51-149">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="45b51-150">DataContext Metotları (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="45b51-150">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
