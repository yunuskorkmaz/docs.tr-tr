---
title: C#Program yapısı- C# dilin turu
description: Bir C# programın temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159123"
---
# <a name="program-structure"></a><span data-ttu-id="df861-103">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="df861-103">Program Structure</span></span>

<span data-ttu-id="df861-104">' Deki C# temel kurumsal kavramlar, ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***.</span><span class="sxs-lookup"><span data-stu-id="df861-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="df861-105">C#programlar bir veya daha fazla kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="df861-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="df861-106">Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="df861-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="df861-107">Sınıflar ve arabirimler tür örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="df861-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="df861-108">Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="df861-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="df861-109">C# Programlar derlendiğinde, fiziksel olarak derlemeler halinde paketlenir.</span><span class="sxs-lookup"><span data-stu-id="df861-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="df861-110">Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp uygulamadığına bağlı olarak dosya uzantısına `.exe` veya `.dll`sahiptir.</span><span class="sxs-lookup"><span data-stu-id="df861-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="df861-111">`dotnet new` komutunu kullanarak *Acme* adlı bir kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df861-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="df861-112">Bu projede, `Acme.Collections`adlı bir ad alanında `Stack` adlı bir sınıf bildirin:</span><span class="sxs-lookup"><span data-stu-id="df861-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="df861-113">Bu sınıfın tam nitelikli adı `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="df861-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="df861-114">Sınıf birçok üye içerir: `top`adlı bir alan, `Push` ve `Pop`adlı iki yöntem ve `Entry`adlı bir iç içe sınıf.</span><span class="sxs-lookup"><span data-stu-id="df861-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="df861-115">`Entry` sınıfı üç üye içerir: `next`adlı bir alan, `data`adlı bir alan ve bir Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="df861-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="df861-116">Komut:</span><span class="sxs-lookup"><span data-stu-id="df861-116">The command:</span></span>

```console
dotnet build 
```

<span data-ttu-id="df861-117">örneği bir kitaplık (`Main` giriş noktası olmayan kod) olarak derler ve `acme.dll`adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df861-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="df861-118">Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="df861-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="df861-119">Yürütülmeden önce, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi, bir derlemedeki Il kodunu işlemciye özel koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="df861-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="df861-120">Bir derleme, hem kodu hem de meta verileri içeren bir işlevsellik birimi olduğundan, içinde C#`#include` yönergeler ve başlık dosyaları gerekmez.</span><span class="sxs-lookup"><span data-stu-id="df861-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="df861-121">Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye C# başvurarak bir programda kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="df861-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="df861-122">Örneğin, bu program `acme.dll` derlemesinden `Acme.Collections.Stack` sınıfını kullanır:</span><span class="sxs-lookup"><span data-stu-id="df861-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="df861-123">Önceki programın projesi için *csproj* dosyası, `acme.dll` derlemesindeki sınıfların başvurularını çözümlemek için C# derleyicinin başvuru düğümünü içermelidir:</span><span class="sxs-lookup"><span data-stu-id="df861-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="df861-124">Bu eklendikten sonra, `dotnet build` `example.exe`adında bir çalıştırılabilir derleme oluşturur ve bu, çalıştırıldığında çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="df861-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="df861-125">C#bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="df861-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="df861-126">Birden çok dosya C# programı derlendiğinde, tüm kaynak dosyalar birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir — kavramsal olarak, tüm kaynak dosyaları işlenmeden önce bir büyük dosyada birleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="df861-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="df861-127">Bildirim sırası çok önemli olduğundan, C# bazı özel durumlarla birlikte iletme bildirimlerine hiçbir şekilde gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="df861-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="df861-128">C#kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adının kaynak dosyada belirtilen bir türle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="df861-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="df861-129">[Önceki](index.md)
>[İleri](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="df861-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
