---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma #"
title: 'Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: d842a646f9f6186d252d10297618ddc2cb137e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785971"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="a7ce6-103">Nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="a7ce6-103">How to: Generate the Object Model in Visual Basic or C\#</span></span>

<span data-ttu-id="a7ce6-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, kendi programlama dilinizdeki bir nesne modeli, ilişkisel bir veritabanıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="a7ce6-105">Varolan bir veritabanının meta verilerinden otomatik olarak bir Visual Basic veya C# modeli oluşturmak için iki araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-105">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="a7ce6-106">Visual Studio kullanıyorsanız, bir nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-106">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="a7ce6-107">O/R Tasarımcısı, nesne modeli oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a7ce6-107">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="a7ce6-108">Daha fazla bilgi için bkz. [Visual Studio 'Da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="a7ce6-108">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="a7ce6-109">SQLMetal komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-109">The SQLMetal command-line tool.</span></span> <span data-ttu-id="a7ce6-110">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a7ce6-110">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a7ce6-111">Mevcut bir veritabanınız yoksa ve bir nesne modelinden bir tane oluşturmak istiyorsanız, kod düzenleyicinizi ve ' yi kullanarak nesne modelinizi oluşturabilirsiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A> .</span><span class="sxs-lookup"><span data-stu-id="a7ce6-111">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="a7ce6-112">Daha fazla bilgi için bkz. [nasıl yapılır: dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="a7ce6-112">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="a7ce6-113">O/R tasarımcısına yönelik belgeler, u/R tasarımcısını kullanarak Visual Basic veya C# nesne modeli oluşturma örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-113">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="a7ce6-114">Aşağıdaki bilgiler, SQLMetal komut satırı aracının nasıl kullanılacağına ilişkin örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-114">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="a7ce6-115">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a7ce6-115">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7ce6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7ce6-116">Example</span></span>  

 <span data-ttu-id="a7ce6-117">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak Visual Basic kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-117">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a7ce6-118">Saklı yordamlar ve işlevler de işlenir.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-118">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="a7ce6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7ce6-119">Example</span></span>  

 <span data-ttu-id="a7ce6-120">Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak C# kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-120">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a7ce6-121">Saklı yordamlar ve işlevler de işlenir ve tablo adları otomatik olarak plurar.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-121">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7ce6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ce6-122">See also</span></span>

- [<span data-ttu-id="a7ce6-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a7ce6-123">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="a7ce6-124">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="a7ce6-124">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a7ce6-125">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="a7ce6-125">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="a7ce6-126">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a7ce6-126">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="a7ce6-127">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="a7ce6-127">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="a7ce6-128">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="a7ce6-128">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="a7ce6-129">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="a7ce6-129">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="a7ce6-130">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="a7ce6-130">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="a7ce6-131">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7ce6-131">Creating the Object Model</span></span>](creating-the-object-model.md)
