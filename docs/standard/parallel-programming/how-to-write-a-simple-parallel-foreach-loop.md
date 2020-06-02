---
title: Parallel. ForEach kullanarak basit bir paralel program yazın
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 717a04790de27c5ae2aade44d29e4e9ff3fd93cc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290726"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="f3216-102">Nasıl yapılır: basit bir Parallel. ForEach Döngüsü Yazma</span><span class="sxs-lookup"><span data-stu-id="f3216-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="f3216-103">Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> herhangi bir <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya veri kaynağı üzerinde veri paralelliğini etkinleştirmek için döngüsünün nasıl kullanılacağını gösterir <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f3216-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="f3216-104">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3216-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="f3216-105">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="f3216-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="f3216-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3216-106">Example</span></span>

<span data-ttu-id="f3216-107">Bu örnek, *C:\users\public\resim\sample resimler* klasöründe birkaç. jpg dosyası olduğunu varsayar ve *değiştirilmiş*adlı yeni bir alt klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3216-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="f3216-108">Örneği çalıştırdığınızda, *örnek resimlerde* her. jpg görüntüsünü döndürür ve *Değiştirilecek*şekilde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f3216-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="f3216-109">Gerektiğinde iki yolu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3216-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="f3216-110"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Döngü bir döngü gibi çalışmaktadır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f3216-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="f3216-111">Döngü, kaynak koleksiyonu bölümler ve sistem ortamına göre birden çok iş parçacığında çalışmayı zamanlar.</span><span class="sxs-lookup"><span data-stu-id="f3216-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="f3216-112">Sistemde daha fazla işlemci varsa, paralel yöntem daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="f3216-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="f3216-113">Bazı kaynak koleksiyonlarında, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3216-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="f3216-114">Performans hakkında daha fazla bilgi için bkz. [veri ve görev paralelliği Içindeki olası](potential-pitfalls-in-data-and-task-parallelism.md)bilgiler.</span><span class="sxs-lookup"><span data-stu-id="f3216-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="f3216-115">Paralel döngüler hakkında daha fazla bilgi için bkz. [nasıl yapılır: basit bir Parallel. for döngüsü yazma](how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="f3216-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="f3216-116"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Genel olmayan bir koleksiyonla birlikte kullanmak için, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, koleksiyonu genel bir koleksiyona dönüştürmek için genişletme yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3216-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="f3216-117">Ayrıca, veri kaynaklarının işlenmesini paralel hale getirmek için paralel LINQ (PLıNQ) kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f3216-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="f3216-118">PLıNQ, döngü davranışını ifade etmek için bildirime dayalı sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3216-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="f3216-119">Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](introduction-to-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f3216-119">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="f3216-120">Kodu derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f3216-120">Compile and run the code</span></span>

<span data-ttu-id="f3216-121">Kodu, .NET Framework için bir konsol uygulaması olarak veya .NET Core için bir konsol uygulaması olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3216-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="f3216-122">Visual Studio 'da, Windows Masaüstü ve .NET Core için Visual Basic ve C# konsol uygulaması şablonları vardır.</span><span class="sxs-lookup"><span data-stu-id="f3216-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="f3216-123">Komut satırından .NET Core CLI komutlarını (örneğin, `dotnet new console` veya `dotnet new console -lang vb` ) kullanabilir ya da dosyayı oluşturabilir ve komut satırı derleyicisini .NET Framework bir uygulama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3216-123">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="f3216-124">Bir .NET Core projesi için **System. Drawing. Common** NuGet paketine başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3216-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="f3216-125">Visual Studio 'da, paketi yüklemek için NuGet Paket Yöneticisi ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3216-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="f3216-126">Alternatif olarak, \* . csproj veya \* . vbproj dosyanızdaki paketin başvurusunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3216-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="f3216-127">Bir .NET Core konsol uygulamasını komut satırından çalıştırmak için `dotnet run` uygulamanızı içeren klasörden kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3216-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="f3216-128">Konsol uygulamanızı Visual Studio 'dan çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="f3216-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3216-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3216-129">See also</span></span>

- [<span data-ttu-id="f3216-130">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="f3216-130">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="f3216-131">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="f3216-131">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="f3216-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f3216-132">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
