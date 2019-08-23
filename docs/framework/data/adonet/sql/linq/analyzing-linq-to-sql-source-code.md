---
title: LINQ to SQL Kaynak Kodunu Analiz Etme
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b23e0df1ee762dd22d43cd1be050db70481db50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964103"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="86d84-102">LINQ to SQL Kaynak Kodunu Analiz Etme</span><span class="sxs-lookup"><span data-stu-id="86d84-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="86d84-103">Aşağıdaki adımları kullanarak, Northwind örnek veritabanından kaynak kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d84-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="86d84-104">Farklı öğelerin nasıl eşleştirildiğini daha iyi görmek için nesne modeli öğelerini veritabanı öğeleriyle karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d84-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86d84-105">Visual Studio kullanan geliştiriciler, bu kodu oluşturmak için O/R tasarımcısını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="86d84-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="86d84-106">Geliştirme bilgisayarınızda zaten Northwind örnek veritabanınız yoksa ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d84-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="86d84-107">Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="86d84-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="86d84-108">Visual Basic veya C# kaynak dosyası oluşturmak Için SQLMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="86d84-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="86d84-109">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="86d84-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="86d84-110">Komut istemine aşağıdaki komutları yazarak, saklı yordamları ve işlevleri içeren Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86d84-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="86d84-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86d84-111">See also</span></span>

- [<span data-ttu-id="86d84-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="86d84-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="86d84-113">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="86d84-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
