---
title: C# Program yapısı-C# dilinin turu
description: C# programının temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141022"
---
# <a name="program-structure"></a><span data-ttu-id="a977f-103">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="a977f-103">Program Structure</span></span>

<span data-ttu-id="a977f-104">C# ' deki temel kurumsal kavramlar ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***.</span><span class="sxs-lookup"><span data-stu-id="a977f-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="a977f-105">C# programları bir veya daha fazla kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="a977f-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="a977f-106">Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="a977f-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="a977f-107">Sınıflar ve arabirimler tür örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="a977f-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="a977f-108">Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="a977f-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="a977f-109">C# programları derlendiğinde, fiziksel olarak derlemeler halinde paketlenir.</span><span class="sxs-lookup"><span data-stu-id="a977f-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="a977f-110">Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp `.dll`uygulamadığına bağlı olarak, genellikle dosya uzantısına `.exe` sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a977f-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="a977f-111">Komutunu kullanarak Acme adlı bir kitaplık projesi oluşturabilirsiniz: *acme* `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="a977f-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```dotnetcli
dotnet new classlib -o acme
```

<span data-ttu-id="a977f-112">Bu projede adlı bir ad alanında adında `Stack` bir sınıf bildirin: `Acme.Collections`</span><span class="sxs-lookup"><span data-stu-id="a977f-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="a977f-113">Bu sınıfın tam adı `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="a977f-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="a977f-114">Sınıf birçok üye `top`içerir: adlı bir alan, `Push` ve `Pop`adlı iki yöntem ve adlı `Entry`bir iç içe sınıf.</span><span class="sxs-lookup"><span data-stu-id="a977f-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="a977f-115">`Entry` Sınıf daha fazla üç üye içerir: adlı `next`alan, adlı `data`alan ve Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="a977f-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="a977f-116">Komut:</span><span class="sxs-lookup"><span data-stu-id="a977f-116">The command:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a977f-117">örneği bir kitaplık (bir `Main` giriş noktası olmayan kod) olarak derler ve adında `acme.dll`bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a977f-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="a977f-118">Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a977f-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="a977f-119">Yürütülmeden önce, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi, bir derlemedeki Il kodunu işlemciye özel koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a977f-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="a977f-120">Bir derleme, hem kodu hem de meta verileri içeren işlevsellikten oluşan bir birim olduğundan, C# dilinde `#include` yönergeler ve başlık dosyaları gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a977f-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="a977f-121">Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye başvurarak bir C# programında kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="a977f-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="a977f-122">Örneğin, bu program `Acme.Collections.Stack` `acme.dll` derlemeden sınıfını kullanır:</span><span class="sxs-lookup"><span data-stu-id="a977f-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="a977f-123">Önceki programın projesi için *csproj* dosyası, `acme.dll` derlemede bulunan sınıflara yönelik başvuruları çözümlemek üzere C# derleyicisi için bir başvuru düğümü içermelidir:</span><span class="sxs-lookup"><span data-stu-id="a977f-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="a977f-124">Bu eklemeyi tamamladıktan sonra `dotnet build` adlı `example.exe`bir çalıştırılabilir derleme oluşturur, bu, çalıştırıldığında çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a977f-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```dotnetcli
100
10
1
```

<span data-ttu-id="a977f-125">C#, bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a977f-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="a977f-126">Çok sayfalı bir C# programı derlendiğinde, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir. kavramsal olarak, tüm kaynak dosyaları işlenmek üzere bir büyük dosyada birleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="a977f-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="a977f-127">Birkaç özel durum dışında, bildirim sırası çok önemli olduğundan, C# ' ta ileri bildirimlere hiçbir şekilde gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="a977f-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="a977f-128">C#, kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adını kaynak dosyada belirtilen bir türle eşleşecek şekilde gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a977f-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a977f-129">[Önceki](index.md)
>[İleri](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="a977f-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
