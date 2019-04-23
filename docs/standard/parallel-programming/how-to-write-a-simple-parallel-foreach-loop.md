---
title: Parallel.ForEach kullanarak basit bir paralel programı yazma
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427363"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="a40c4-102">Nasıl yapılır: Basit bir Parallel.ForEach döngüsü yazma</span><span class="sxs-lookup"><span data-stu-id="a40c4-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="a40c4-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi birini etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="a40c4-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="a40c4-104">Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a40c4-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="a40c4-105">İle lambda ifadelerine aşina değilseniz C# veya Visual Basic, bkz: [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="a40c4-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="a40c4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a40c4-106">Example</span></span>

<span data-ttu-id="a40c4-107">Bu örnekte birkaç .jpg dosya olduğunu varsayar bir *C:\Users\Public\Pictures\Sample resimleri* klasörü ve yeni bir alt klasör oluşturur *değiştirilen*.</span><span class="sxs-lookup"><span data-stu-id="a40c4-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="a40c4-108">Örneği çalıştırdığınızda, her bir .jpg resim, döndürür. *örnek resimler* ve kaydeder *değiştirilen*.</span><span class="sxs-lookup"><span data-stu-id="a40c4-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="a40c4-109">İki yolu gerektiği gibi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c4-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="a40c4-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü.</span><span class="sxs-lookup"><span data-stu-id="a40c4-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="a40c4-111">Döngü, kaynak koleksiyonu bölümler ve sistem ortamına bağlı olarak, birden çok iş parçacığı üzerinde çalışma zamanlar.</span><span class="sxs-lookup"><span data-stu-id="a40c4-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="a40c4-112">Daha fazla işlemci sistem üzerinde paralel yöntemi daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="a40c4-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="a40c4-113">Bazı kaynak koleksiyonları için hızlı, kaynak ve döngü gerçekleştiren iş türünü boyutuna bağlı olarak sıralı bir döngü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a40c4-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="a40c4-114">Performans hakkında daha fazla bilgi için bkz: [veri ve görev paralelliği olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="a40c4-114">For more information about performance, see [Potential pitfalls in data and task parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>

<span data-ttu-id="a40c4-115">Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="a40c4-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="a40c4-116">Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> kullanabileceğiniz bir genel olmayan koleksiyonu ile <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:</span><span class="sxs-lookup"><span data-stu-id="a40c4-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="a40c4-117">Paralel LINQ (PLINQ) işlenmesini paralel hale getirmek için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları.</span><span class="sxs-lookup"><span data-stu-id="a40c4-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="a40c4-118">PLINQ, döngü davranışı ifade etmek için bildirim temelli bir sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a40c4-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="a40c4-119">Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="a40c4-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="a40c4-120">Derleme ve kod çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a40c4-120">Compile and run the code</span></span>

<span data-ttu-id="a40c4-121">Kodu bir konsol uygulaması için .NET Framework veya .NET Core konsol uygulaması olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c4-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="a40c4-122">Visual Studio'da Visual Basic vardır ve C# Windows Masaüstü ve .NET Core konsol uygulaması şablonları.</span><span class="sxs-lookup"><span data-stu-id="a40c4-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="a40c4-123">Komut satırından .NET Core ve CLI araçlarını da kullanabilirsiniz (örneğin, `dotnet new console` veya `dotnet new console -lang vb`), veya dosyayı oluşturmak ve komut satırı derleyicisi için bir .NET Framework uygulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a40c4-123">From the command line, you can use either .NET Core and its CLI tools (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="a40c4-124">Bir .NET Core projesi için başvuru gerekir **System.Drawing.Common** NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="a40c4-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="a40c4-125">Visual Studio'da NuGet Paket Yöneticisi paketini yüklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a40c4-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="a40c4-126">Alternatif olarak, pakete bir başvuru ekleyebilirsiniz, \*.csproj veya \*.vbproj dosyası:</span><span class="sxs-lookup"><span data-stu-id="a40c4-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="a40c4-127">Komut satırından .NET Core konsol uygulaması çalıştırmak için kullanın `dotnet run` uygulamanızı içeren klasörden.</span><span class="sxs-lookup"><span data-stu-id="a40c4-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="a40c4-128">Konsol uygulamanızı Visual Studio'dan çalıştırmak için basın **F5**.</span><span class="sxs-lookup"><span data-stu-id="a40c4-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a40c4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a40c4-129">See also</span></span>

- [<span data-ttu-id="a40c4-130">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="a40c4-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="a40c4-131">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="a40c4-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="a40c4-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a40c4-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
