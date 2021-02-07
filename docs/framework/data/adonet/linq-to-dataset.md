---
description: 'Hakkında daha fazla bilgi edinin: LINQ to DataSet'
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 74b5f97d9fecb05b1fd13e986dd0cbcc10fa1456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681675"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="95e93-103">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="95e93-103">LINQ to DataSet</span></span>

<span data-ttu-id="95e93-104">LINQ to DataSet, bir nesnede önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="95e93-104">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="95e93-105">Özellikle LINQ to DataSet, geliştiricilerin ayrı bir sorgu dili yerine programlama dilinin kendisinden sorgu yazmasını sağlayarak sorgulamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="95e93-105">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="95e93-106">Bu özellikle Visual Studio geliştiricileri için yararlıdır. artık, derleme zamanı sözdizimi denetimi, statik yazma ve Visual Studio tarafından sorgularda sunulan IntelliSense desteğinden faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="95e93-106">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="95e93-107">LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95e93-107">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="95e93-108">Bu, yerel olarak toplanmış verileri sorgulama ve Web uygulamalarında orta katman önbelleğe alma gibi, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoyu sağlar.</span><span class="sxs-lookup"><span data-stu-id="95e93-108">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="95e93-109">Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="95e93-109">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="95e93-110">LINQ to DataSet işlevselliği öncelikle ve sınıflarındaki uzantı yöntemleri aracılığıyla gösterilir <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> .</span><span class="sxs-lookup"><span data-stu-id="95e93-110">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="95e93-111">LINQ to DataSet, ve var olan ADO.NET mimarisini kullanır ve uygulama kodundaki ADO.NET 'in yerini almak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="95e93-111">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="95e93-112">Mevcut ADO.NET kodu bir LINQ to DataSet uygulamasında çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="95e93-112">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="95e93-113">ADO.NET ve veri deposuna LINQ to DataSet ilişkisi aşağıdaki diyagramda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="95e93-113">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![LINQ to DataSet, ADO.NET sağlayıcıya bağlı olduğunu gösteren diyagram.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="95e93-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="95e93-115">In This Section</span></span>  

 [<span data-ttu-id="95e93-116">Başlarken</span><span class="sxs-lookup"><span data-stu-id="95e93-116">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="95e93-117">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95e93-117">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="95e93-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="95e93-118">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="95e93-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95e93-119">See also</span></span>

- [<span data-ttu-id="95e93-120">Dil ile tümleşik sorgu (LINQ)-C #</span><span class="sxs-lookup"><span data-stu-id="95e93-120">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="95e93-121">Dil ile tümleşik sorgu (LINQ)-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95e93-121">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="95e93-122">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="95e93-122">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="95e93-123">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="95e93-123">ADO.NET</span></span>](index.md)
