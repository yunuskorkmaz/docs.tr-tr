---
title: "Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="ca2b1-102">Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca2b1-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="ca2b1-103">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], programlama diliniz nesne modelinde ilişkisel bir veritabanına eşlendi.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="ca2b1-104">İki araçları otomatik olarak oluşturmak için kullanılabilir bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya varolan bir veritabanını meta verilerden model C#.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="ca2b1-105">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="ca2b1-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlayan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="ca2b1-107">Daha fazla bilgi için [LINQ-SQL Visual Studio Araçları](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="ca2b1-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="ca2b1-108">SQLMetal komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="ca2b1-109">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ca2b1-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca2b1-110">Var olan veritabanı ve bir nesne modeli oluşturmak için istediğiniz yoksa, nesne modeli kodunuzu kullanarak Düzenleyicisi oluşturabilirsiniz ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="ca2b1-111">Daha fazla bilgi için bkz: [nasıl yapılır: dinamik olarak bir veritabanı oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="ca2b1-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="ca2b1-112">Belgelerine [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] nasıl oluşturacağını örnekleri sağlar bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya kullanarak C# nesne modeli [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca2b1-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="ca2b1-113">Aşağıdaki bilgileri SQLMetal komut satırı aracını kullanma örnekleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="ca2b1-114">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ca2b1-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca2b1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca2b1-115">Example</span></span>  
 <span data-ttu-id="ca2b1-116">Aşağıdaki örnekte gösterildiği SQLMetal komut satırı üreten [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kodu Northwind örnek veritabanı öznitelik tabanlı nesne modelini olarak.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="ca2b1-117">Saklı yordamları ve işlevleri de işlenir.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="ca2b1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca2b1-118">Example</span></span>  
 <span data-ttu-id="ca2b1-119">Aşağıdaki örnekte gösterildiği SQLMetal komut satırında C# kod Northwind örnek veritabanı öznitelik tabanlı nesne modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="ca2b1-120">Saklı yordamları ve işlevleri de işlenir ve tablo adları otomatik olarak pluralized.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca2b1-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca2b1-121">See Also</span></span>  
 [<span data-ttu-id="ca2b1-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ca2b1-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="ca2b1-123">LINQ to SQL nesne modeli</span><span class="sxs-lookup"><span data-stu-id="ca2b1-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="ca2b1-124">Öğrenme tarafından izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="ca2b1-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="ca2b1-125">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ca2b1-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="ca2b1-126">Öznitelik tabanlı eşleme</span><span class="sxs-lookup"><span data-stu-id="ca2b1-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="ca2b1-127">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="ca2b1-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="ca2b1-128">Dış eşleme</span><span class="sxs-lookup"><span data-stu-id="ca2b1-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="ca2b1-129">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="ca2b1-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="ca2b1-130">Nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca2b1-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
