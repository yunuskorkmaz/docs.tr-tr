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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec28b175dddb98eb035061363dd6581e796280b3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="9be9f-102">Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="9be9f-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="9be9f-103">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], programlama diliniz nesne modelinde ilişkisel bir veritabanına eşlendi.</span><span class="sxs-lookup"><span data-stu-id="9be9f-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="9be9f-104">İki araçları otomatik olarak oluşturmak için kullanılabilir bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya varolan bir veritabanını meta verilerden model C#.</span><span class="sxs-lookup"><span data-stu-id="9be9f-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="9be9f-105">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9be9f-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="9be9f-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlayan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="9be9f-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="9be9f-107">Daha fazla bilgi için [LINQ-SQL Visual Studio Araçları](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="9be9f-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="9be9f-108">SQLMetal komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="9be9f-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="9be9f-109">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9be9f-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9be9f-110">Var olan veritabanı ve bir nesne modeli oluşturmak için istediğiniz yoksa, nesne modeli kodunuzu kullanarak Düzenleyicisi oluşturabilirsiniz ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="9be9f-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="9be9f-111">Daha fazla bilgi için bkz: [nasıl yapılır: dinamik olarak bir veritabanı oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="9be9f-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="9be9f-112">Belgelerine [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] nasıl oluşturacağını örnekleri sağlar bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya kullanarak C# nesne modeli [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9be9f-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="9be9f-113">Aşağıdaki bilgileri SQLMetal komut satırı aracını kullanma örnekleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9be9f-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="9be9f-114">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9be9f-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be9f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9be9f-115">Example</span></span>  
 <span data-ttu-id="9be9f-116">Aşağıdaki örnekte gösterildiği SQLMetal komut satırı üreten [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kodu Northwind örnek veritabanı öznitelik tabanlı nesne modelini olarak.</span><span class="sxs-lookup"><span data-stu-id="9be9f-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="9be9f-117">Saklı yordamları ve işlevleri de işlenir.</span><span class="sxs-lookup"><span data-stu-id="9be9f-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="9be9f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9be9f-118">Example</span></span>  
 <span data-ttu-id="9be9f-119">Aşağıdaki örnekte gösterildiği SQLMetal komut satırında C# kod Northwind örnek veritabanı öznitelik tabanlı nesne modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9be9f-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="9be9f-120">Saklı yordamları ve işlevleri de işlenir ve tablo adları otomatik olarak pluralized.</span><span class="sxs-lookup"><span data-stu-id="9be9f-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="9be9f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9be9f-121">See Also</span></span>  
 [<span data-ttu-id="9be9f-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9be9f-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="9be9f-123">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="9be9f-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="9be9f-124">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="9be9f-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="9be9f-125">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9be9f-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="9be9f-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="9be9f-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="9be9f-127">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="9be9f-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="9be9f-128">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="9be9f-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="9be9f-129">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="9be9f-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="9be9f-130">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9be9f-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
