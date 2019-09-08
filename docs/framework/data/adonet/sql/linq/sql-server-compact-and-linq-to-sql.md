---
title: SQL Server Compact ve LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792539"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="e9748-102">SQL Server Compact ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e9748-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="e9748-103">SQL Server Compact, Visual Studio ile yüklenen varsayılan veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="e9748-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="e9748-104">Daha fazla bilgi için bkz. [SQL Server Compact kullanma (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="e9748-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="e9748-105">Bu konuda kullanım, yapılandırma, özellik kümeleri ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destek kapsamındaki önemli farklılıklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9748-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="e9748-106">LINQ to SQL göre SQL Server Compact özellikleri</span><span class="sxs-lookup"><span data-stu-id="e9748-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="e9748-107">Varsayılan olarak, tüm Visual Studio sürümleri için SQL Server Compact yüklenir ve bu nedenle geliştirme bilgisayarında ile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanım için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9748-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e9748-108">Ancak SQL Server Compact kullanan ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server bir uygulama için bundan farklı bir uygulama dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="e9748-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="e9748-109">SQL Server Compact, .NET Framework bir parçası değildir ve bu nedenle uygulamayla paketlenmesi veya Microsoft sitesinden ayrı olarak indirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9748-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="e9748-110">Aşağıdaki özelliklere göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="e9748-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="e9748-111">SQL Server Compact, veritabanı dosyalarında (. sdf uzantısı) doğrudan kullanılabilecek bir DLL olarak paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9748-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="e9748-112">SQL Server Compact, istemci uygulamasıyla aynı işlemde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9748-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="e9748-113">SQL Server Compact ile iletişimin verimliliği, SQL Server iletişim kurmaktan önemli ölçüde yüksek olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9748-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="e9748-114">Diğer yandan SQL Server Compact, yönetilen ve yönetilmeyen kod arasında ortak maliyetleriyle birlikte çalışabilirlik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e9748-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="e9748-115">SQL Server Compact DLL boyutu küçüktür.</span><span class="sxs-lookup"><span data-stu-id="e9748-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="e9748-116">Bu özellik, uygulamanın boyutunun tamamını azaltır.</span><span class="sxs-lookup"><span data-stu-id="e9748-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="e9748-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.</span><span class="sxs-lookup"><span data-stu-id="e9748-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="e9748-118">Nesne İlişkisel Tasarımcısı SQL Server Compact desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e9748-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="e9748-119">Özellik kümesi</span><span class="sxs-lookup"><span data-stu-id="e9748-119">Feature Set</span></span>  
 <span data-ttu-id="e9748-120">SQL Server Compact özellik kümesi, uygulamaları etkileyebilecek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki yollarla SQL Server Özellik kümesinden çok daha basittir:</span><span class="sxs-lookup"><span data-stu-id="e9748-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="e9748-121">SQL Server Compact, saklı yordamları veya görünümleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e9748-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="e9748-122">SQL Server Compact, veri türleri ve SQL işlevlerinin yalnızca bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="e9748-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="e9748-123">SQL Server Compact, SQL yapılarının yalnızca bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="e9748-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="e9748-124">SQL Server Compact yalnızca en az bir iyileştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9748-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="e9748-125">Bazı sorgular zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="e9748-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="e9748-126">SQL Server Compact kısmi güveni desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e9748-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9748-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9748-127">See also</span></span>

- [<span data-ttu-id="e9748-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e9748-128">Reference</span></span>](reference.md)
