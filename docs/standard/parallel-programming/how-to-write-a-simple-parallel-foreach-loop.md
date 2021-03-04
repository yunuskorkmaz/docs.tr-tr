---
title: Parallel. ForEach kullanarak basit bir paralel program yazın
description: Bu makalede, .NET 'te veri paralelliğini nasıl etkinleştireceğinizi öğrenin. Herhangi bir IEnumerable veya IEnumerable veri kaynağı üzerinde bir Parallel. ForEach Döngüsü yazın <T> .
ms.date: 02/23/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 50c60d730fbf930ea369b014e2f8f971e9c1f239
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106689"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="561b2-104">Nasıl yapılır: basit bir Parallel. ForEach Döngüsü Yazma</span><span class="sxs-lookup"><span data-stu-id="561b2-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="561b2-105">Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> herhangi bir <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya veri kaynağı üzerinde veri paralelliğini etkinleştirmek için döngüsünün nasıl kullanılacağını gösterir <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="561b2-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="561b2-106">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="561b2-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="561b2-107">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="561b2-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="561b2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="561b2-108">Example</span></span>

<span data-ttu-id="561b2-109">Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> CPU yoğun işlemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="561b2-109">This example demonstrates <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> for CPU intensive operations.</span></span> <span data-ttu-id="561b2-110">Örneği çalıştırdığınızda rastgele 2.000.000 sayı üretir ve asal sayılara filtre uygulamayı dener.</span><span class="sxs-lookup"><span data-stu-id="561b2-110">When you run the example, it randomly generates 2 million numbers and tries to filter to prime numbers.</span></span> <span data-ttu-id="561b2-111">İlk durum, bir döngü aracılığıyla koleksiyonu yineler `for` .</span><span class="sxs-lookup"><span data-stu-id="561b2-111">The first case iterates over the collection via a `for` loop.</span></span> <span data-ttu-id="561b2-112">İkinci durum, ile koleksiyonun üzerinde yinelenir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="561b2-112">The second case iterates over the collection via <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="561b2-113">Her yineleme tarafından alınan sonuç süresi, uygulama tamamlandığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="561b2-113">The resulting time taken by each iteration is displayed when the application is finished.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="561b2-114"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Döngü bir döngü gibi çalışmaktadır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="561b2-114">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="561b2-115">Döngü, kaynak koleksiyonu bölümler ve sistem ortamına göre birden çok iş parçacığında çalışmayı zamanlar.</span><span class="sxs-lookup"><span data-stu-id="561b2-115">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="561b2-116">Sistemde daha fazla işlemci varsa, paralel yöntem daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="561b2-116">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="561b2-117">Bazı kaynak koleksiyonlarında, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="561b2-117">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="561b2-118">Performans hakkında daha fazla bilgi için bkz. [veri ve görev paralelliği Içindeki olası](potential-pitfalls-in-data-and-task-parallelism.md)bilgiler.</span><span class="sxs-lookup"><span data-stu-id="561b2-118">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="561b2-119">Paralel döngüler hakkında daha fazla bilgi için bkz. [nasıl yapılır: basit bir Parallel. for döngüsü yazma](how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="561b2-119">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="561b2-120"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Genel olmayan bir koleksiyonla birlikte kullanmak için, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, koleksiyonu genel bir koleksiyona dönüştürmek için genişletme yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="561b2-120">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="561b2-121">Ayrıca, veri kaynaklarının işlenmesini paralel hale getirmek için paralel LINQ (PLıNQ) kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="561b2-121">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="561b2-122">PLıNQ, döngü davranışını ifade etmek için bildirime dayalı sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="561b2-122">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="561b2-123">Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](introduction-to-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="561b2-123">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="561b2-124">Kodu derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="561b2-124">Compile and run the code</span></span>

<span data-ttu-id="561b2-125">Kodu, .NET Framework için bir konsol uygulaması olarak veya .NET Core için bir konsol uygulaması olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="561b2-125">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="561b2-126">Visual Studio 'da, Windows Masaüstü ve .NET Core için Visual Basic ve C# konsol uygulaması şablonları vardır.</span><span class="sxs-lookup"><span data-stu-id="561b2-126">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="561b2-127">Komut satırından .NET Core CLI komutlarını (örneğin, `dotnet new console` veya `dotnet new console -lang vb` ) kullanabilir ya da dosyayı oluşturabilir ve komut satırı derleyicisini .NET Framework bir uygulama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="561b2-127">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="561b2-128">Bir .NET Core konsol uygulamasını komut satırından çalıştırmak için `dotnet run` uygulamanızı içeren klasörden kullanın.</span><span class="sxs-lookup"><span data-stu-id="561b2-128">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="561b2-129">Konsol uygulamanızı Visual Studio 'dan çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="561b2-129">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="561b2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="561b2-130">See also</span></span>

- [<span data-ttu-id="561b2-131">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="561b2-131">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="561b2-132">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="561b2-132">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="561b2-133">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="561b2-133">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
