---
title: LINQ - DataSet
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3746fb31c66202dc75c6aff3ce69952f25b06931
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="linq-to-dataset"></a><span data-ttu-id="a6d84-102">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="a6d84-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="a6d84-103"> daha kolay ve hızlı sorguya, önbelleğe alınan veriler üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a6d84-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="a6d84-104">Özellikle, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları programlama dili kendisi yerine ayrı sorgu dilini kullanarak yazmak geliştiricilere etkinleştirerek sorgulama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="a6d84-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="a6d84-105">Bu artık, derleme zamanı sözdizimi denetimi, statik yazarak ve IntelliSense desteği sorgularını Visual Studio tarafından sağlanan yararlanabilir Visual Studio geliştiriciler için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a6d84-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="a6d84-106"> Ayrıca kullanılabilir bir veya daha fazla veri kaynaklarından birleştirilmiş veriler üzerinde sorgulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="a6d84-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="a6d84-107">Bu verilerin temsil ve işlenmiş, yerel olarak toplanan verileri ve orta katman Web uygulamalarında önbelleğe alma sorgulama gibi esneklik gerektiren birçok senaryolara olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6d84-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="a6d84-108">Özellikle, genel raporlama, analiz ve business Intelligence uygulamalar bu yöntem işlemlerinde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a6d84-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="a6d84-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevselliği genişletme yöntemleri aracılığıyla gösterilir <xref:System.Data.DataRowExtensions> ve <xref:System.Data.DataTableExtensions> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a6d84-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="a6d84-110"> üzerine kurulur ve varolan kullanır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] mimarisi ve değiştirmek için tasarlanmamıştır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] uygulama kodundaki.</span><span class="sxs-lookup"><span data-stu-id="a6d84-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="a6d84-111">Varolan ADO.NET 2.0 kod içinde çalışmaya devam edecek bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="a6d84-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="a6d84-112">İlişki [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] ve veri depolama alanı aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6d84-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="a6d84-113">![LINQ-DataSet ADO.NET sağlayıcısını temel](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="a6d84-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6d84-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a6d84-114">In This Section</span></span>  
 [<span data-ttu-id="a6d84-115">Başlarken</span><span class="sxs-lookup"><span data-stu-id="a6d84-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="a6d84-116">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6d84-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="a6d84-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a6d84-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="a6d84-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d84-118">See Also</span></span>  
 [<span data-ttu-id="a6d84-119">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="a6d84-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="a6d84-120">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6d84-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="a6d84-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6d84-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
