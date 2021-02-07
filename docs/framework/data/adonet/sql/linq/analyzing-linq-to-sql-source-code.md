---
description: 'Hakkında daha fazla bilgi edinin: LINQ to SQL kaynak kodu analiz etme'
title: LINQ to SQL Kaynak Kodunu Analiz Etme
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: acf80b10c3bb817cf3fd87876da75a47e2fe271c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712798"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="582ab-103">LINQ to SQL Kaynak Kodunu Analiz Etme</span><span class="sxs-lookup"><span data-stu-id="582ab-103">Analyzing LINQ to SQL Source Code</span></span>

<span data-ttu-id="582ab-104">Aşağıdaki adımları kullanarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Northwind örnek veritabanından kaynak kodu üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="582ab-104">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="582ab-105">Farklı öğelerin nasıl eşleştirildiğini daha iyi görmek için nesne modeli öğelerini veritabanı öğeleriyle karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="582ab-105">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="582ab-106">Visual Studio kullanan geliştiriciler, bu kodu oluşturmak için O/R tasarımcısını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="582ab-106">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="582ab-107">Geliştirme bilgisayarınızda zaten Northwind örnek veritabanınız yoksa ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="582ab-107">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="582ab-108">Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="582ab-108">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="582ab-109">Visual Basic veya C# kaynak dosyası oluşturmak için SqlMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="582ab-109">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="582ab-110">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="582ab-110">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="582ab-111">Komut istemine aşağıdaki komutları yazarak, saklı yordamları ve işlevleri içeren Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="582ab-111">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="582ab-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="582ab-112">See also</span></span>

- [<span data-ttu-id="582ab-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="582ab-113">Reference</span></span>](reference.md)
- [<span data-ttu-id="582ab-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="582ab-114">Background Information</span></span>](background-information.md)
