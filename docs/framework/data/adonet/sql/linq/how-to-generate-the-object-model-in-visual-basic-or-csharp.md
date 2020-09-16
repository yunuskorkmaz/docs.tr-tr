---
title: 'Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546620"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="07139-102">Nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="07139-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="07139-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, kendi programlama dilinizdeki bir nesne modeli, ilişkisel bir veritabanıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="07139-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="07139-104">Varolan bir veritabanının meta verilerinden otomatik olarak bir Visual Basic veya C# modeli oluşturmak için iki araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="07139-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="07139-105">Visual Studio kullanıyorsanız, bir nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07139-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="07139-106">O/R Tasarımcısı, nesne modeli oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="07139-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="07139-107">Daha fazla bilgi için bkz. [Visual Studio 'Da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="07139-107">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="07139-108">SQLMetal komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="07139-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="07139-109">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="07139-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="07139-110">Mevcut bir veritabanınız yoksa ve bir nesne modelinden bir tane oluşturmak istiyorsanız, kod düzenleyicinizi ve ' yi kullanarak nesne modelinizi oluşturabilirsiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A> .</span><span class="sxs-lookup"><span data-stu-id="07139-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="07139-111">Daha fazla bilgi için bkz. [nasıl yapılır: dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="07139-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="07139-112">O/R tasarımcısına yönelik belgeler, u/R tasarımcısını kullanarak Visual Basic veya C# nesne modeli oluşturma örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07139-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="07139-113">Aşağıdaki bilgiler, SQLMetal komut satırı aracının nasıl kullanılacağına ilişkin örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07139-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="07139-114">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="07139-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07139-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="07139-115">Example</span></span>  
 <span data-ttu-id="07139-116">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak Visual Basic kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="07139-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="07139-117">Saklı yordamlar ve işlevler de işlenir.</span><span class="sxs-lookup"><span data-stu-id="07139-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="07139-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="07139-118">Example</span></span>  
 <span data-ttu-id="07139-119">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak C# kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="07139-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="07139-120">Saklı yordamlar ve işlevler de işlenir ve tablo adları otomatik olarak plurar.</span><span class="sxs-lookup"><span data-stu-id="07139-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="07139-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07139-121">See also</span></span>

- [<span data-ttu-id="07139-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="07139-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="07139-123">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="07139-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="07139-124">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="07139-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="07139-125">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="07139-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="07139-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="07139-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="07139-127">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="07139-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="07139-128">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="07139-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="07139-129">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="07139-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="07139-130">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07139-130">Creating the Object Model</span></span>](creating-the-object-model.md)
