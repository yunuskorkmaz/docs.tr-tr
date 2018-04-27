---
title: 'Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: dccef2af3d13099b71d3ea8418242e5a5cc16ae5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="fbc96-102">Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbc96-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="fbc96-103">Bir veritabanı işaretleme dili (.dbml) meta veri dosyasından Visual Basic veya C# kaynak kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="fbc96-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="fbc96-104">Bu yaklaşım uygulama eşleme kodu oluşturmadan önce varsayılan .dbml dosyasını özelleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="fbc96-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="fbc96-105">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="fbc96-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="fbc96-106">Bu işlemdeki adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fbc96-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="fbc96-107">Bir .dbml dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbc96-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="fbc96-108">.Dbml dosyasını değiştirmek için bir düzenleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbc96-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="fbc96-109">.Dbml dosyanın şema tanımını (.xsd) dosyası için karşı doğrulamalısınız Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="fbc96-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="fbc96-110">Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fbc96-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="fbc96-111">Visual Basic veya C# kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbc96-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="fbc96-112">Aşağıdaki örnekler SQLMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbc96-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="fbc96-113">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fbc96-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbc96-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbc96-114">Example</span></span>  
 <span data-ttu-id="fbc96-115">Aşağıdaki kod, Northwind örnek veritabanından .dbml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbc96-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="fbc96-116">Veritabanı meta veriler için kaynak olarak veritabanının adını veya .mdf dosyasının adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbc96-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="fbc96-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbc96-117">Example</span></span>  
 <span data-ttu-id="fbc96-118">Aşağıdaki kod, Visual Basic veya C# kaynak kodu dosyasının .dbml dosyasından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbc96-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbc96-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbc96-119">See Also</span></span>  
 [<span data-ttu-id="fbc96-120">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbc96-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="fbc96-121">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="fbc96-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="fbc96-122">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbc96-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
