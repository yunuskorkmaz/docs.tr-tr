---
title: 'Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338429"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="b820b-102">Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b820b-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="b820b-103">Visual Basic oluşturabilir veya C# kaynak koddan bir veritabanı işaretleme dili (.dbml) meta veri dosyası.</span><span class="sxs-lookup"><span data-stu-id="b820b-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="b820b-104">Bu yaklaşım, varsayılan .dbml dosyası uygulama eşlemesi kodu oluşturmadan önce özelleştirmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="b820b-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="b820b-105">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b820b-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="b820b-106">Bu işlemdeki adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b820b-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="b820b-107">Bir .dbml dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b820b-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="b820b-108">Bir .dbml dosyası değiştirmek için bir düzenleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="b820b-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="b820b-109">Bir .dbml dosyası için şema tanımı (.xsd) dosyası karşı doğrulamalıdır Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="b820b-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="b820b-110">Daha fazla bilgi için [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b820b-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="b820b-111">Visual Basic oluşturmak veya C# kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="b820b-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="b820b-112">Aşağıdaki örnekler SQLMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b820b-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="b820b-113">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b820b-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b820b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b820b-114">Example</span></span>  
 <span data-ttu-id="b820b-115">Aşağıdaki kod, Northwind örnek veritabanındaki bir .dbml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b820b-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="b820b-116">Veritabanı meta veri kaynağı olarak veritabanı adını veya .mdf dosyası adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b820b-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="b820b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b820b-117">Example</span></span>  
 <span data-ttu-id="b820b-118">Aşağıdaki kod Visual Basic oluşturur veya C# bir .dbml dosyasından kaynak kodu dosyası.</span><span class="sxs-lookup"><span data-stu-id="b820b-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="b820b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b820b-119">See also</span></span>

- [<span data-ttu-id="b820b-120">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b820b-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="b820b-121">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="b820b-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="b820b-122">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b820b-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
