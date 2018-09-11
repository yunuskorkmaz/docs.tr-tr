---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 0b597cf93cdf249936a34b2c07b38d000c96333f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353008"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="ede8a-102">Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme</span><span class="sxs-lookup"><span data-stu-id="ede8a-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="ede8a-103">Bu belgenin nasıl ayarlanacağı açıklanır <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> bir yürütme veri akışı bloğunun aynı anda birden fazla ileti işlemek üzere etkinleştirmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="ede8a-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="ede8a-104">Uzun süre çalışan bir hesaplama gerçekleştiren bir veri akışı bloğu olan ve paralel ileti işlemesini yararlanabilir, bunun yapılması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ede8a-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="ede8a-105">Bu örnekte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> eşzamanlı olarak; ancak birden çok veri akışı işlemlerini gerçekleştirmek için sınıf, TPL veri akışı kitaplığı sağlayan önceden tanımlanmış yürütme bloğu türü hiçbirinde maksimum paralellik derecesi belirtebilirsiniz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="ede8a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ede8a-106">Example</span></span>  
 <span data-ttu-id="ede8a-107">Aşağıdaki örnek, iki veri akışı hesaplamaları gerçekleştirir ve her hesaplama için gerekli olan süre yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ede8a-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="ede8a-108">İlk hesaplama, varsayılan bir en fazla 1, paralellik derecesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="ede8a-109">Bir en büyük bir paralellik derecesi 1 iletileri seri olarak işlemek veri akışı bloğu neden olur.</span><span class="sxs-lookup"><span data-stu-id="ede8a-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="ede8a-110">İkinci hesaplama ilk benzer bir en fazla kullanılabilir işlemci sayısına eşit olan çalıştırılır. paralellik derecesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="ede8a-111">Bu, paralel olarak birden çok işlemi gerçekleştirmek veri akışı bloğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ede8a-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ede8a-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ede8a-112">Compiling the Code</span></span>  
 <span data-ttu-id="ede8a-113">Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` Visual Basic için), ve ardından bir Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ede8a-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="ede8a-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="ede8a-114">Visual C#</span></span>  
  
 <span data-ttu-id="ede8a-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="ede8a-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="ede8a-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ede8a-116">Visual Basic</span></span>  
  
 <span data-ttu-id="ede8a-117">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="ede8a-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ede8a-118">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ede8a-118">Robust Programming</span></span>  
 <span data-ttu-id="ede8a-119">Varsayılan olarak, iletileri iletilerin alındığı sırada her önceden tanımlı veri akışı bloğu yayar.</span><span class="sxs-lookup"><span data-stu-id="ede8a-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="ede8a-120">Bir en büyük ölçüde 1'den büyük bir paralellik derecesi belirttiğinizde birden çok ileti aynı anda işlenir ancak bunlar yine de kullanıma alındı sıraya yayılır.</span><span class="sxs-lookup"><span data-stu-id="ede8a-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="ede8a-121"><xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> özelliği en büyük paralellik derecesini temsil ettiğinden, veri akışı bloğu belirttiğinizden daha düşük derecede paralellikle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="ede8a-122">Veri akışı bloğu işlevsel gereksinimlerini karşılamak için veya mevcut sistem kaynaklarının yetersizliği için hesap için daha düşük bir paralellik derecesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ede8a-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="ede8a-123">Bir veri akışı bloğu asla belirttiğinizden daha büyük bir paralellik derecesi seçer.</span><span class="sxs-lookup"><span data-stu-id="ede8a-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede8a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ede8a-124">See also</span></span>

- [<span data-ttu-id="ede8a-125">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="ede8a-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
