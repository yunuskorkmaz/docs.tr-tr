---
title: SQL Server Compact ve LINQ-SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9409c17065b0421ec32a61352f9c0b975095ab44
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="99c23-102">SQL Server Compact ve LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="99c23-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="99c23-103">SQL Server Compact Visual Studio ile yüklenen varsayılan veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="99c23-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="99c23-104">Daha fazla bilgi için bkz: [PAVE üzerinden kullanarak SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="99c23-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="99c23-105">Bu konu kullanımı, yapılandırma, özellik kümeleri ve kapsamını temel farklılıkları özetler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="99c23-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="99c23-106">LINQ-SQL ile ilgili SQL Server Compact özellikleri</span><span class="sxs-lookup"><span data-stu-id="99c23-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="99c23-107">Varsayılan olarak, SQL Server Compact tüm yüklü [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] sürümleri ve bu nedenle ile kullanmak için geliştirme bilgisayarındaki kullanılabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99c23-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="99c23-108">Ancak, SQL Server Compact kullanan bir uygulama dağıtımını ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için farklı bir [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="99c23-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="99c23-109">SQL Server Compact .NET Framework'ün bir parçası değil ve bu nedenle uygulama ile paketlenmiş veya gerekir ayrı olarak Microsoft sitesinden indirilen.</span><span class="sxs-lookup"><span data-stu-id="99c23-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="99c23-110">Aşağıdaki özelliklere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="99c23-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="99c23-111">SQL Server Compact veritabanı dosyalarını (.sdf uzantılı) karşı doğrudan kullanılabilen DLL olarak paketlenir.</span><span class="sxs-lookup"><span data-stu-id="99c23-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="99c23-112">İstemci uygulaması ile aynı işlemde SQL Server Compact çalışır.</span><span class="sxs-lookup"><span data-stu-id="99c23-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="99c23-113">SQL Server Compact ile iletişim verimliliğini bu nedenle kurduğu daha önemli ölçüde daha yüksek olabilir [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99c23-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="99c23-114">Diğer taraftan, SQL Server Compact Katılımcısı maliyetleri yönetilen ve yönetilmeyen kod birlikte çalışabilirliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="99c23-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="99c23-115">SQL Server Compact DLL'si boyutu küçüktür.</span><span class="sxs-lookup"><span data-stu-id="99c23-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="99c23-116">Bu özellik genel uygulama boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="99c23-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="99c23-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.</span><span class="sxs-lookup"><span data-stu-id="99c23-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="99c23-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] SQL Server Compact desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="99c23-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="99c23-119">Özellik kümesi</span><span class="sxs-lookup"><span data-stu-id="99c23-119">Feature Set</span></span>  
 <span data-ttu-id="99c23-120">SQL Server Compact özellik kümesi özellik kümesini çok daha kolaydır [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] etkileyebilir aşağıdaki yollarla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar:</span><span class="sxs-lookup"><span data-stu-id="99c23-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="99c23-121">SQL Server Compact saklı yordamları veya görünümleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99c23-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="99c23-122">SQL Server Compact yalnızca bir alt veri türleri ve SQL işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="99c23-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="99c23-123">SQL Server Compact yalnızca bir alt kümesini SQL yapısını destekler.</span><span class="sxs-lookup"><span data-stu-id="99c23-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="99c23-124">SQL Server Compact en az bir iyileştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="99c23-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="99c23-125">Bazı sorgular zaman aşımı olabilir mümkündür.</span><span class="sxs-lookup"><span data-stu-id="99c23-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="99c23-126">SQL Server Compact, kısmi güven desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99c23-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c23-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99c23-127">See Also</span></span>  
 [<span data-ttu-id="99c23-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="99c23-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
