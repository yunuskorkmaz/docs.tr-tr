---
title: 'Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 5f2c2f99a5efeb3463ecf5bf401a6cf654845bb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911975"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="e3db4-102">Nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="e3db4-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="e3db4-103">' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, kendi programlama dilinizdeki bir nesne modeli, ilişkisel bir veritabanıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e3db4-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="e3db4-104">Varolan bir veritabanının meta verilerinden otomatik olarak bir Visual Basic veya C# model oluşturmak için iki araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e3db4-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="e3db4-105">Visual Studio kullanıyorsanız, bir nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3db4-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="e3db4-106">O/R Tasarımcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3db4-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="e3db4-107">Daha fazla bilgi için bkz. [Visual Studio 'Da LINQ to SQL araçları](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="e3db4-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="e3db4-108">SQLMetal komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="e3db4-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="e3db4-109">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e3db4-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e3db4-110">Mevcut bir veritabanınız yoksa ve bir nesne modelinden bir tane oluşturmak istiyorsanız, kod düzenleyicinizi ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>' yi kullanarak nesne modelinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3db4-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="e3db4-111">Daha fazla bilgi için [nasıl yapılır: Dinamik olarak bir veritabanı](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3db4-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="e3db4-112">O/R tasarımcısına yönelik belgeler, u/R tasarımcısını kullanarak bir Visual Basic veya C# nesne modeli oluşturma örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3db4-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="e3db4-113">Aşağıdaki bilgiler, SQLMetal komut satırı aracının nasıl kullanılacağına ilişkin örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3db4-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="e3db4-114">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e3db4-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3db4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3db4-115">Example</span></span>  
 <span data-ttu-id="e3db4-116">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak Visual Basic kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="e3db4-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="e3db4-117">Saklı yordamlar ve işlevler de işlenir.</span><span class="sxs-lookup"><span data-stu-id="e3db4-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="e3db4-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3db4-118">Example</span></span>  
 <span data-ttu-id="e3db4-119">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının C# öznitelik tabanlı nesne modeli olarak kod üretir.</span><span class="sxs-lookup"><span data-stu-id="e3db4-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="e3db4-120">Saklı yordamlar ve işlevler de işlenir ve tablo adları otomatik olarak plurar.</span><span class="sxs-lookup"><span data-stu-id="e3db4-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3db4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3db4-121">See also</span></span>

- [<span data-ttu-id="e3db4-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e3db4-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="e3db4-123">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="e3db4-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e3db4-124">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="e3db4-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="e3db4-125">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e3db4-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="e3db4-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="e3db4-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="e3db4-127">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="e3db4-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="e3db4-128">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="e3db4-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="e3db4-129">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="e3db4-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="e3db4-130">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3db4-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
