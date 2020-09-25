---
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 1c03cca80de6003a4e49278871983ed7fcb3dc0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200673"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="82260-102">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="82260-102">LINQ to DataSet</span></span>

<span data-ttu-id="82260-103">LINQ to DataSet, bir nesnede önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="82260-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="82260-104">Özellikle LINQ to DataSet, geliştiricilerin ayrı bir sorgu dili yerine programlama dilinin kendisinden sorgu yazmasını sağlayarak sorgulamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="82260-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="82260-105">Bu özellikle Visual Studio geliştiricileri için yararlıdır. artık, derleme zamanı sözdizimi denetimi, statik yazma ve Visual Studio tarafından sorgularda sunulan IntelliSense desteğinden faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="82260-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="82260-106">LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82260-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="82260-107">Bu, yerel olarak toplanmış verileri sorgulama ve Web uygulamalarında orta katman önbelleğe alma gibi, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoyu sağlar.</span><span class="sxs-lookup"><span data-stu-id="82260-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="82260-108">Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="82260-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="82260-109">LINQ to DataSet işlevselliği öncelikle ve sınıflarındaki uzantı yöntemleri aracılığıyla gösterilir <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> .</span><span class="sxs-lookup"><span data-stu-id="82260-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="82260-110">LINQ to DataSet, ve var olan ADO.NET mimarisini kullanır ve uygulama kodundaki ADO.NET 'in yerini almak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="82260-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="82260-111">Mevcut ADO.NET kodu bir LINQ to DataSet uygulamasında çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="82260-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="82260-112">ADO.NET ve veri deposuna LINQ to DataSet ilişkisi aşağıdaki diyagramda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82260-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![LINQ to DataSet, ADO.NET sağlayıcıya bağlı olduğunu gösteren diyagram.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="82260-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="82260-114">In This Section</span></span>  

 [<span data-ttu-id="82260-115">Başlarken</span><span class="sxs-lookup"><span data-stu-id="82260-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="82260-116">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="82260-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="82260-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="82260-117">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="82260-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82260-118">See also</span></span>

- [<span data-ttu-id="82260-119">Dil ile tümleşik sorgu (LINQ)-C #</span><span class="sxs-lookup"><span data-stu-id="82260-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="82260-120">Dil ile tümleşik sorgu (LINQ)-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82260-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="82260-121">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="82260-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="82260-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="82260-122">ADO.NET</span></span>](index.md)
