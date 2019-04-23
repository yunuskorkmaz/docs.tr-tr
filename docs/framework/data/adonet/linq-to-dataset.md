---
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 92be418e38039757437e6e673f39a7baef011528
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221788"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="74793-102">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="74793-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="74793-103">daha kolay ve hızlı sorgu için verileri önbelleğe üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesne.</span><span class="sxs-lookup"><span data-stu-id="74793-103">makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="74793-104">Özellikle, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları programlama dilinden kendisi yerine ayrı bir sorgu dilini kullanarak yazma geliştiricilerin etkinleştirerek sorgulama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="74793-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="74793-105">Bu, özellikle artık derleme zamanı söz dizimi denetimini statik yazmaya ve sorguları Visual Studio tarafından sağlanan IntelliSense desteği yararlanabilirsiniz Visual Studio geliştiriciler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="74793-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="74793-106">Ayrıca bir veya daha fazla veri kaynağından birleştirilmiş veriler üzerinde sorgu için.</span><span class="sxs-lookup"><span data-stu-id="74793-106">can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="74793-107">Bu, yerel olarak toplanan verileri ve orta katman Web uygulamalarında önbelleğe alma sorgulama gibi işlenen verilerin nasıl temsil ve esneklik gerektiren birçok senaryolarını olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="74793-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="74793-108">Özellikle, bu yöntem işlemlerinde genel raporlama, analiz ve iş zekası uygulamaları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74793-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="74793-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevi sunulmuştur alanında uzantı yöntemlerini yoluyla <xref:System.Data.DataRowExtensions> ve <xref:System.Data.DataTableExtensions> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74793-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="74793-110">temel alır ve mevcut kullanan [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] mimari ve değiştirmek için tasarlanmamıştır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] uygulama kodunda.</span><span class="sxs-lookup"><span data-stu-id="74793-110">builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="74793-111">Var olan ADO.NET 2.0 kod içinde çalışmaya devam edecek bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="74793-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="74793-112">İlişkiyi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] ve veri deposu Aşağıdaki diyagramda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74793-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 ![LINQ to DataSet ADO.NET sağlayıcısını dayalı olduğunu gösteren diyagram.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="74793-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="74793-114">In This Section</span></span>  
 [<span data-ttu-id="74793-115">Başlarken</span><span class="sxs-lookup"><span data-stu-id="74793-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="74793-116">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74793-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="74793-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="74793-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="74793-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74793-118">See also</span></span>

- [<span data-ttu-id="74793-119">Dil ile tümleşik sorgu (LINQ)-C#</span><span class="sxs-lookup"><span data-stu-id="74793-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="74793-120">Dil ile tümleşik sorgu (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74793-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="74793-121">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="74793-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="74793-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="74793-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
