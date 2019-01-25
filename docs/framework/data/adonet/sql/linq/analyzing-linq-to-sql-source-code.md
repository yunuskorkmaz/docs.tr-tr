---
title: LINQ to SQL kaynak kodunu analiz etme
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b1d2d2c54ae99a65f60c96b6330e3f94db6beb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696860"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="deff1-102">LINQ to SQL kaynak kodunu analiz etme</span><span class="sxs-lookup"><span data-stu-id="deff1-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="deff1-103">Aşağıdaki adımları kullanarak, üretebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kaynak kodu Northwind örnek veritabanından.</span><span class="sxs-lookup"><span data-stu-id="deff1-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="deff1-104">Karşılaştırabileceğiniz daha iyi nasıl farklı olan öğeleri görmek için veritabanı öğelerini nesne modeline öğeleriyle eşlendi.</span><span class="sxs-lookup"><span data-stu-id="deff1-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="deff1-105">Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Bu kod üretmek için.</span><span class="sxs-lookup"><span data-stu-id="deff1-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="deff1-106">Geliştirme bilgisayarınızda Northwind örnek veritabanı yoksa, ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="deff1-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="deff1-107">Daha fazla bilgi için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="deff1-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="deff1-108">Bir Visual Basic oluşturmak üzere SqlMetal komut satırı aracını kullanın veya C# kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="deff1-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="deff1-109">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="deff1-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="deff1-110">Bir komut isteminde aşağıdaki komutları yazarak, Visual Basic oluşturabilir ve C# kaynak saklı yordamları ve işlevleri içeren dosyaları:</span><span class="sxs-lookup"><span data-stu-id="deff1-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="deff1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deff1-111">See also</span></span>
- [<span data-ttu-id="deff1-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="deff1-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="deff1-113">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="deff1-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
