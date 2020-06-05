---
title: Parallel. ForEach kullanarak basit bir paralel program yazın
description: Bu makalede, .NET 'te veri paralelliğini nasıl etkinleştireceğinizi öğrenin. Herhangi bir IEnumerable veya IEnumerable veri kaynağı üzerinde bir Parallel. ForEach Döngüsü yazın <T> .
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 59c8710a8e3fc878b2ceded8595f7f3319d4c953
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447205"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="7bc96-104">Nasıl yapılır: basit bir Parallel. ForEach Döngüsü Yazma</span><span class="sxs-lookup"><span data-stu-id="7bc96-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="7bc96-105">Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> herhangi bir <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya veri kaynağı üzerinde veri paralelliğini etkinleştirmek için döngüsünün nasıl kullanılacağını gösterir <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7bc96-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc96-106">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bc96-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="7bc96-107">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="7bc96-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="7bc96-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bc96-108">Example</span></span>

<span data-ttu-id="7bc96-109">Bu örnek, *C:\users\public\resim\sample resimler* klasöründe birkaç. jpg dosyası olduğunu varsayar ve *değiştirilmiş*adlı yeni bir alt klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bc96-109">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="7bc96-110">Örneği çalıştırdığınızda, *örnek resimlerde* her. jpg görüntüsünü döndürür ve *Değiştirilecek*şekilde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7bc96-110">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="7bc96-111">Gerektiğinde iki yolu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bc96-111">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="7bc96-112"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Döngü bir döngü gibi çalışmaktadır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7bc96-112">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="7bc96-113">Döngü, kaynak koleksiyonu bölümler ve sistem ortamına göre birden çok iş parçacığında çalışmayı zamanlar.</span><span class="sxs-lookup"><span data-stu-id="7bc96-113">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="7bc96-114">Sistemde daha fazla işlemci varsa, paralel yöntem daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="7bc96-114">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="7bc96-115">Bazı kaynak koleksiyonlarında, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bc96-115">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="7bc96-116">Performans hakkında daha fazla bilgi için bkz. [veri ve görev paralelliği Içindeki olası](potential-pitfalls-in-data-and-task-parallelism.md)bilgiler.</span><span class="sxs-lookup"><span data-stu-id="7bc96-116">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="7bc96-117">Paralel döngüler hakkında daha fazla bilgi için bkz. [nasıl yapılır: basit bir Parallel. for döngüsü yazma](how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="7bc96-117">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="7bc96-118"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Genel olmayan bir koleksiyonla birlikte kullanmak için, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, koleksiyonu genel bir koleksiyona dönüştürmek için genişletme yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7bc96-118">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="7bc96-119">Ayrıca, veri kaynaklarının işlenmesini paralel hale getirmek için paralel LINQ (PLıNQ) kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="7bc96-119">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="7bc96-120">PLıNQ, döngü davranışını ifade etmek için bildirime dayalı sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bc96-120">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="7bc96-121">Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](introduction-to-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="7bc96-121">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="7bc96-122">Kodu derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7bc96-122">Compile and run the code</span></span>

<span data-ttu-id="7bc96-123">Kodu, .NET Framework için bir konsol uygulaması olarak veya .NET Core için bir konsol uygulaması olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bc96-123">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="7bc96-124">Visual Studio 'da, Windows Masaüstü ve .NET Core için Visual Basic ve C# konsol uygulaması şablonları vardır.</span><span class="sxs-lookup"><span data-stu-id="7bc96-124">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="7bc96-125">Komut satırından .NET Core CLI komutlarını (örneğin, `dotnet new console` veya `dotnet new console -lang vb` ) kullanabilir ya da dosyayı oluşturabilir ve komut satırı derleyicisini .NET Framework bir uygulama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bc96-125">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="7bc96-126">Bir .NET Core projesi için **System. Drawing. Common** NuGet paketine başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bc96-126">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="7bc96-127">Visual Studio 'da, paketi yüklemek için NuGet Paket Yöneticisi ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bc96-127">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="7bc96-128">Alternatif olarak, \* . csproj veya \* . vbproj dosyanızdaki paketin başvurusunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7bc96-128">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="7bc96-129">Bir .NET Core konsol uygulamasını komut satırından çalıştırmak için `dotnet run` uygulamanızı içeren klasörden kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bc96-129">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="7bc96-130">Konsol uygulamanızı Visual Studio 'dan çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="7bc96-130">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bc96-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc96-131">See also</span></span>

- [<span data-ttu-id="7bc96-132">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="7bc96-132">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="7bc96-133">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="7bc96-133">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="7bc96-134">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7bc96-134">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
