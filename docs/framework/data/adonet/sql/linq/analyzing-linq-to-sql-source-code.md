---
title: LINQ-SQL kaynak kodunu analiz etme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e1677d8e30b083efe99f916b28672ddb6c3dd99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="8e615-102">LINQ-SQL kaynak kodunu analiz etme</span><span class="sxs-lookup"><span data-stu-id="8e615-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="8e615-103">Aşağıdaki adımları kullanarak, üretebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kaynak Northwind örnek veritabanı koddan.</span><span class="sxs-lookup"><span data-stu-id="8e615-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="8e615-104">Karşılaştırabileceğiniz nesne modeli öğeleri daha iyi nasıl farklı öğeleri görmek için veritabanına öğelerin eşlendi.</span><span class="sxs-lookup"><span data-stu-id="8e615-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e615-105">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] bu kodu oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8e615-105">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="8e615-106">Northwind örnek veritabanı geliştirme bilgisayarınızda zaten yoksa, ücretsiz olarak karşıdan yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e615-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="8e615-107">Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8e615-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="8e615-108">Visual Basic veya C# kaynak dosyası oluşturmak üzere SqlMetal komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e615-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="8e615-109">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8e615-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="8e615-110">Bir komut isteminde aşağıdaki komutları yazarak, saklı yordamları ve işlevleri dahil Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e615-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="8e615-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e615-111">See Also</span></span>  
 [<span data-ttu-id="8e615-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8e615-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="8e615-113">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="8e615-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
