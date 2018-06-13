---
title: 'Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354578"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="c1d5a-102">Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1d5a-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="c1d5a-103">Bir veritabanı işaretleme dili (.dbml) meta veri dosyasından Visual Basic veya C# kaynak kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="c1d5a-104">Bu yaklaşım uygulama eşleme kodu oluşturmadan önce varsayılan .dbml dosyasını özelleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="c1d5a-105">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="c1d5a-106">Bu işlemdeki adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c1d5a-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="c1d5a-107">Bir .dbml dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="c1d5a-108">.Dbml dosyasını değiştirmek için bir düzenleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="c1d5a-109">.Dbml dosyanın şema tanımını (.xsd) dosyası için karşı doğrulamalısınız Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="c1d5a-110">Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c1d5a-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="c1d5a-111">Visual Basic veya C# kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="c1d5a-112">Aşağıdaki örnekler SQLMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="c1d5a-113">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c1d5a-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d5a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1d5a-114">Example</span></span>  
 <span data-ttu-id="c1d5a-115">Aşağıdaki kod, Northwind örnek veritabanından .dbml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="c1d5a-116">Veritabanı meta veriler için kaynak olarak veritabanının adını veya .mdf dosyasının adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="c1d5a-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1d5a-117">Example</span></span>  
 <span data-ttu-id="c1d5a-118">Aşağıdaki kod, Visual Basic veya C# kaynak kodu dosyasının .dbml dosyasından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1d5a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1d5a-119">See Also</span></span>  
 [<span data-ttu-id="c1d5a-120">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1d5a-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="c1d5a-121">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="c1d5a-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="c1d5a-122">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1d5a-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
