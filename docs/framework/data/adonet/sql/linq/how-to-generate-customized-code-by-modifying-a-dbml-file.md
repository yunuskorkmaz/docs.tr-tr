---
title: 'Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod üretme'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 6619f4b8c0a47b36a0b84fa21bab4109d26ef895
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002947"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="12bd1-102">Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod üretme</span><span class="sxs-lookup"><span data-stu-id="12bd1-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="12bd1-103">Bir veritabanı biçimlendirme dili ( C# . dbml) meta veri dosyasından Visual Basic veya kaynak kodu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12bd1-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="12bd1-104">Bu yaklaşım, uygulama eşleme kodunu oluşturmadan önce default. dbml dosyasını özelleştirmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="12bd1-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="12bd1-105">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="12bd1-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="12bd1-106">Bu işlemdeki adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="12bd1-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="12bd1-107">Bir. dbml dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12bd1-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="12bd1-108">. Dbml dosyasını değiştirmek için bir düzenleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="12bd1-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="12bd1-109">. Dbml dosyasının [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. dbml dosyaları için şema tanımı (. xsd) dosyasında doğrulanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12bd1-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="12bd1-110">Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="12bd1-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="12bd1-111">Visual Basic veya C# kaynak kodu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12bd1-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="12bd1-112">Aşağıdaki örneklerde SQLMetal komut satırı aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12bd1-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="12bd1-113">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="12bd1-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12bd1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="12bd1-114">Example</span></span>  
 <span data-ttu-id="12bd1-115">Aşağıdaki kod, Northwind örnek veritabanından bir. dbml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12bd1-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="12bd1-116">Veritabanı meta verileri için kaynak olarak, veritabanının adını veya. mdf dosyasının adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12bd1-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="12bd1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="12bd1-117">Example</span></span>  
 <span data-ttu-id="12bd1-118">Aşağıdaki kod, bir. dbml dosyasından Visual Basic veya C# kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12bd1-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="12bd1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12bd1-119">See also</span></span>

- [<span data-ttu-id="12bd1-120">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12bd1-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="12bd1-121">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="12bd1-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="12bd1-122">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12bd1-122">Creating the Object Model</span></span>](creating-the-object-model.md)
