---
description: 'Daha fazla bilgi edinin: nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma'
title: 'Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 0dd4024b3f6a0ca0583de6bfbdb7463fab14d969
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786010"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="0721b-103">Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0721b-103">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="0721b-104">Veritabanı biçimlendirme dili (. dbml) meta veri dosyasından Visual Basic veya C# kaynak kodu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0721b-104">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="0721b-105">Bu yaklaşım, uygulama eşleme kodunu oluşturmadan önce default. dbml dosyasını özelleştirmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="0721b-105">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="0721b-106">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0721b-106">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="0721b-107">Bu işlemdeki adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0721b-107">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="0721b-108">Bir. dbml dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0721b-108">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="0721b-109">. Dbml dosyasını değiştirmek için bir düzenleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="0721b-109">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="0721b-110">. Dbml dosyasının. dbml dosyaları için şema tanımı (. xsd) dosyasına göre doğrulanması gerektiğini unutmayın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0721b-110">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="0721b-111">Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0721b-111">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="0721b-112">Visual Basic veya C# kaynak kodu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0721b-112">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="0721b-113">Aşağıdaki örneklerde SQLMetal komut satırı aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0721b-113">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="0721b-114">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="0721b-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0721b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0721b-115">Example</span></span>  

 <span data-ttu-id="0721b-116">Aşağıdaki kod, Northwind örnek veritabanından bir. dbml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0721b-116">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="0721b-117">Veritabanı meta verileri için kaynak olarak, veritabanının adını veya. mdf dosyasının adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0721b-117">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="0721b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0721b-118">Example</span></span>  

 <span data-ttu-id="0721b-119">Aşağıdaki kod, bir. dbml dosyasından Visual Basic veya C# kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0721b-119">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="0721b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0721b-120">See also</span></span>

- [<span data-ttu-id="0721b-121">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0721b-121">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="0721b-122">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="0721b-122">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="0721b-123">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0721b-123">Creating the Object Model</span></span>](creating-the-object-model.md)
