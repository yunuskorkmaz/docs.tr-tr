---
title: C#Program yapısı- C# dilin turu
description: Bir C# programın temel yapı taşlarını öğrenin
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5102c72d68108f698a0456b9c14e6713778f4325
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834165"
---
# <a name="program-structure"></a><span data-ttu-id="cd873-103">Program yapısı</span><span class="sxs-lookup"><span data-stu-id="cd873-103">Program Structure</span></span>

<span data-ttu-id="cd873-104">' Deki C# temel kurumsal kavramlar, ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***.</span><span class="sxs-lookup"><span data-stu-id="cd873-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="cd873-105">C#programlar bir veya daha fazla kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="cd873-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="cd873-106">Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="cd873-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="cd873-107">Sınıflar ve arabirimler tür örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="cd873-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="cd873-108">Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="cd873-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="cd873-109">C# Programlar derlendiğinde, fiziksel olarak derlemeler halinde paketlenir.</span><span class="sxs-lookup"><span data-stu-id="cd873-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="cd873-110">Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp uygulamadığına bağlı olarak `.exe` veya `.dll` dosya uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd873-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="cd873-111">Örnek, `Acme.Collections` adlı bir ad alanında `Stack` adlı bir sınıf bildirir:</span><span class="sxs-lookup"><span data-stu-id="cd873-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="cd873-112">Bu sınıfın tam adı `Acme.Collections.Stack` ' dır.</span><span class="sxs-lookup"><span data-stu-id="cd873-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="cd873-113">Sınıf birçok üye içerir: `top` adlı bir alan, `Push` ve `Pop` adlı iki yöntem ve `Entry` adlı bir iç içe sınıf.</span><span class="sxs-lookup"><span data-stu-id="cd873-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="cd873-114">@No__t-0 sınıfı üç üye içerir: `next` adlı bir alan, `data` adlı alan ve bir Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="cd873-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="cd873-115">Örneğin kaynak kodunun dosyada depolandığını varsayarak `acme.cs`, komut satırı</span><span class="sxs-lookup"><span data-stu-id="cd873-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```console
csc /t:library acme.cs
```

<span data-ttu-id="cd873-116">örneği bir kitaplık (`Main` giriş noktası olmadan) olarak derler ve `acme.dll` adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd873-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd873-117">Yukarıdaki örnekler, komut satırı C# derleyicisi olarak `csc` kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd873-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="cd873-118">Bu derleyici bir Windows yürütülebiliridir.</span><span class="sxs-lookup"><span data-stu-id="cd873-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="cd873-119">Diğer platformlarda C# kullanmak Için .NET Core araçlarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd873-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="cd873-120">.NET Core ekosistemi, komut satırı yapılarını yönetmek için `dotnet` CLı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd873-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="cd873-121">Buna bağımlılıkları yönetme ve C# derleyicinin çağrılması dahildir.</span><span class="sxs-lookup"><span data-stu-id="cd873-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="cd873-122">.NET Core tarafından desteklenen platformlarda bu araçların tam açıklaması için [Bu öğreticiye](../../core/tutorials/using-with-xplat-cli.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="cd873-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="cd873-123">Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd873-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="cd873-124">Yürütülmeden önce, bir derlemedeki IL kodu, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi tarafından otomatik olarak işlemciye özgü koda dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="cd873-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="cd873-125">Bir derleme, hem kodu hem de meta verileri içeren bir dizi işlevin kendine açıklayıcı bir birimi olduğundan, içinde C#`#include` yönergeleri ve üst bilgi dosyaları gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cd873-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="cd873-126">Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye C# başvurarak bir programda kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="cd873-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="cd873-127">Örneğin, bu program `acme.dll` derlemesinden `Acme.Collections.Stack` sınıfını kullanır:</span><span class="sxs-lookup"><span data-stu-id="cd873-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="cd873-128">Program dosyada depolanıyorsa `example.cs` `example.cs` derlendiğinde, Acme. dll derlemesine derleyicinin/r seçeneği kullanılarak başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="cd873-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```console
csc /r:acme.dll example.cs
```

<span data-ttu-id="cd873-129">Bu, çalıştırıldığında, çıktıyı üreten `example.exe` adlı bir çalıştırılabilir derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cd873-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="cd873-130">C#bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd873-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="cd873-131">Birden çok dosya C# programı derlendiğinde, tüm kaynak dosyalar birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir — kavramsal olarak, tüm kaynak dosyaları işlenmeden önce bir büyük dosyada birleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="cd873-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="cd873-132">Bildirim sırası çok önemli olduğundan, C# bazı durumlarda ileri bildirimlere hiçbir şekilde gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd873-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="cd873-133">C#kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adının kaynak dosyada belirtilen bir türle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd873-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cd873-134">[Önceki](index.md)
>[İleri](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="cd873-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
