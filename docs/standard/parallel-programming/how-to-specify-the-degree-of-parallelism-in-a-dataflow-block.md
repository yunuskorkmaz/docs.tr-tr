---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0631603e3426a08cc1f3abb07bc0f9ecc73adb21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="16b73-102">Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme</span><span class="sxs-lookup"><span data-stu-id="16b73-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="16b73-103">Bu belge nasıl ayarlanacağını açıklar <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> aynı anda birden fazla iletiyi işlemek için bir yürütme veri akışı bloğu etkinleştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="16b73-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="16b73-104">Uzun süre çalışan hesaplama gerçekleştirir bir veri akışı bloğu varsa ve iletileri paralel işleme yararlanabilir Bunun yapılması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="16b73-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="16b73-105">Bu örnekte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> eşzamanlı olarak; ancak birden çok veri akışı işlemlerini gerçekleştirmek için sınıf, maksimum paralellik derecesi TPL veri akışı kitaplığı sağlar, önceden tanımlanmış yürütme blok türlerinden birini belirtebilirsiniz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16b73-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="16b73-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="16b73-106">Example</span></span>  
 <span data-ttu-id="16b73-107">Aşağıdaki örnekte, iki veri akışı hesaplamalar gerçekleştirir ve her işlem için gereken süre yazdırır.</span><span class="sxs-lookup"><span data-stu-id="16b73-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="16b73-108">İlk hesaplama varsayılan olan bir maksimum paralellik derecesi 1 ' in belirtir.</span><span class="sxs-lookup"><span data-stu-id="16b73-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="16b73-109">Bir maksimum paralellik derecesi 1 iletileri seri olarak işlemek veri akışı bloğu neden olur.</span><span class="sxs-lookup"><span data-stu-id="16b73-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="16b73-110">İkinci hesaplama ilk benzer bir en fazla kullanılabilir işlemci sayısına eşittir paralellik derecesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16b73-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="16b73-111">Bu paralel olarak birden çok işlemlerini gerçekleştirmek veri akışı bloğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b73-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="16b73-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="16b73-112">Compiling the Code</span></span>  
 <span data-ttu-id="16b73-113">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` Visual Basic), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16b73-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="16b73-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="16b73-114">Visual C#</span></span>  
  
 <span data-ttu-id="16b73-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="16b73-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="16b73-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16b73-116">Visual Basic</span></span>  
  
 <span data-ttu-id="16b73-117">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="16b73-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="16b73-118">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="16b73-118">Robust Programming</span></span>  
 <span data-ttu-id="16b73-119">Varsayılan olarak, her önceden tanımlanmış veri akışı bloğu iletileri alındığı sırada ileti yayar.</span><span class="sxs-lookup"><span data-stu-id="16b73-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="16b73-120">Maksimum paralellik 1'den büyük olan derecesi belirttiğinizde birden fazla ileti aynı anda işlenir ancak bunlar hala çıkışı bunlar alındığı sırada yayılır.</span><span class="sxs-lookup"><span data-stu-id="16b73-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="16b73-121"><xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> özelliği en büyük paralellik derecesini temsil ettiğinden, veri akışı bloğu belirttiğinizden daha düşük derecede paralellikle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="16b73-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="16b73-122">Veri akışı bloğu küçük paralellik derecesi işlevsel gereksinimlerini karşılamak için veya mevcut sistem kaynaklarının yetersizliği için hesap için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b73-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="16b73-123">Bir veri akışı bloğu, belirttiğiniz daha büyük bir paralellik derecesi hiçbir zaman seçer.</span><span class="sxs-lookup"><span data-stu-id="16b73-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b73-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16b73-124">See Also</span></span>  
 [<span data-ttu-id="16b73-125">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="16b73-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
