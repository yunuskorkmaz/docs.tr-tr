---
title: SQL Server Compact ve LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: db3f7aef082d965dc27b69f5a966ff038c0ffac0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145723"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="98ae5-102">SQL Server Compact ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="98ae5-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="98ae5-103">SQL Server Compact ile Visual Studio yüklü varsayılan bir veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="98ae5-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="98ae5-104">Daha fazla bilgi için [kullanarak SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="98ae5-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="98ae5-105">Bu konuda kullanımı, yapılandırma, özellik kümeleri ve kapsamı temel farklılıklar özetlenmiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="98ae5-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="98ae5-106">SQL Server Compact LINQ to SQL ile ilgili özellikleri</span><span class="sxs-lookup"><span data-stu-id="98ae5-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="98ae5-107">Varsayılan olarak, SQL Server Compact için tüm Visual Studio sürümleri yüklenir ve bu nedenle ile kullanmak için geliştirme bilgisayarında kullanılabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98ae5-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="98ae5-108">Ancak SQL Server Compact kullanan bir uygulama dağıtımını ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , SQL Server uygulama için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="98ae5-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="98ae5-109">SQL Server Compact .NET Framework'ün bir parçası değil ve bu nedenle uygulamayla paketlenmiş veya gerekir Microsoft sitesinden ayrı olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="98ae5-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="98ae5-110">Aşağıdaki özelliklere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="98ae5-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="98ae5-111">SQL Server Compact veritabanı dosyaları (.sdf uzantısına) karşı doğrudan kullanılabilen bir DLL paketlenir.</span><span class="sxs-lookup"><span data-stu-id="98ae5-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="98ae5-112">SQL Server Compact istemci uygulama ile aynı işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="98ae5-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="98ae5-113">SQL Server Compact ile iletişimi verimliliğini, bu nedenle SQL Server ile iletişim kurarken daha önemli ölçüde daha yüksek olabilir.</span><span class="sxs-lookup"><span data-stu-id="98ae5-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="98ae5-114">Öte yandan, SQL Server Compact Katılımcısı giderlerini ile yönetilen ve yönetilmeyen kod arasındaki birlikte çalışabilirlik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="98ae5-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="98ae5-115">SQL Server Compact DLL'si boyutu küçüktür.</span><span class="sxs-lookup"><span data-stu-id="98ae5-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="98ae5-116">Bu özellik, genel uygulama boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="98ae5-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="98ae5-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.</span><span class="sxs-lookup"><span data-stu-id="98ae5-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="98ae5-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] SQL Server Compact desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98ae5-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="98ae5-119">Özellik kümesi</span><span class="sxs-lookup"><span data-stu-id="98ae5-119">Feature Set</span></span>  
 <span data-ttu-id="98ae5-120">SQL Server Compact özellik kümesini etkileyen aşağıdaki yollarla SQL Server özellik kümesini çok daha kolay [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar:</span><span class="sxs-lookup"><span data-stu-id="98ae5-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="98ae5-121">SQL Server Compact saklı yordamları veya görünümleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98ae5-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="98ae5-122">SQL Server Compact, yalnızca bir alt kümesini veri türleri ve SQL işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="98ae5-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="98ae5-123">SQL Server Compact, SQL yapıları yalnızca bir kısmını destekler.</span><span class="sxs-lookup"><span data-stu-id="98ae5-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="98ae5-124">SQL Server Compact, en az bir iyileştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="98ae5-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="98ae5-125">Bazı sorgular zaman aşımına uğrayabilir mümkündür.</span><span class="sxs-lookup"><span data-stu-id="98ae5-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="98ae5-126">SQL Server Compact, kısmi güven desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98ae5-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ae5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98ae5-127">See also</span></span>

- [<span data-ttu-id="98ae5-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="98ae5-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
