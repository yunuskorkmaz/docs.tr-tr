---
title: C# Program Yapısı - C# Dili Turu
description: C# programının temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156837"
---
# <a name="program-structure"></a><span data-ttu-id="2b5fc-103">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="2b5fc-103">Program Structure</span></span>

<span data-ttu-id="2b5fc-104">C#'daki temel kuruluş kavramları ***programlar,*** ***ad alanları,*** ***türleri,*** ***üyeler***ve ***derlemelerdir.***</span><span class="sxs-lookup"><span data-stu-id="2b5fc-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="2b5fc-105">C# programları bir veya daha fazla kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="2b5fc-106">Programlar, üye içeren ve ad boşlukları halinde düzenlenebilecek türleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="2b5fc-107">Sınıflar ve arabirimler türleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="2b5fc-108">Alanlar, yöntemler, özellikler ve olaylar üye örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="2b5fc-109">C# programları derlendiğinde, fiziksel olarak derlemelere paketlenirler.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="2b5fc-110">Derlemeler genellikle dosya uzantısı `.exe` `.dll`na sahip veya ***sırasıyla uygulamaları*** veya ***kitaplıkları***uygulayıp uygulamadıklarına bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="2b5fc-111">Komutu kullanarak acme adlı bir kitaplık projesi oluşturabilirsiniz: *acme* `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="2b5fc-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="2b5fc-112">Bu projede, ad `Stack` alanında adı geçen `Acme.Collections`bir sınıf bildirin:</span><span class="sxs-lookup"><span data-stu-id="2b5fc-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="2b5fc-113">Bu sınıfın tam nitelikli `Acme.Collections.Stack`adı .</span><span class="sxs-lookup"><span data-stu-id="2b5fc-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="2b5fc-114">Sınıf birkaç üye içerir: `top`adlı bir `Push` alan, adlı iki yöntem ve `Pop`, adlı iç içe sınıf `Entry`.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="2b5fc-115">Sınıf `Entry` daha üç üye içerir: `next`adlı bir `data`alan , adlı bir alan , ve bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="2b5fc-116">Komut:</span><span class="sxs-lookup"><span data-stu-id="2b5fc-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="2b5fc-117">örneği kitaplık olarak derler `Main` (giriş noktası olmayan kod) `acme.dll`ve adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="2b5fc-118">Derlemeler, Ara Dil (IL) yönergeleri biçiminde yürütülebilir kod ve meta veri biçiminde sembolik bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="2b5fc-119">Yürütülmeden önce,.NET Ortak Dil Runtime'ın Just-In-Time (JIT) derleyicisi, bir derlemedeki IL kodunu işlemciye özgü koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="2b5fc-120">Derleme, hem kod hem de meta verileri içeren kendi kendini tanımlayan bir `#include` işlevsellik birimi olduğundan, C#'da yönergelere ve üstbilgi dosyalarına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="2b5fc-121">Belirli bir derlemede yer alan genel türler ve üyeler, yalnızca programı derlerken bu derlemeye başvurarak C# programında kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="2b5fc-122">Örneğin, bu program `Acme.Collections.Stack` `acme.dll` derleme den sınıf kullanır:</span><span class="sxs-lookup"><span data-stu-id="2b5fc-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="2b5fc-123">Önceki programın projesiiçin *csproj* `acme.dll` dosyası, derlemedeki sınıflara yapılan başvuruları çözmek için C# derleyicisi için bir başvuru düğümü içermelidir:</span><span class="sxs-lookup"><span data-stu-id="2b5fc-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="2b5fc-124">Bu eklemeden `dotnet build` sonra, çalıştırıldığında `example.exe`çıktıüreten , "çalıştırılabilir" adlı bir yürütülebilir derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2b5fc-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="2b5fc-125">C# bir programın kaynak metninin çeşitli kaynak dosyalarda depolanabına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="2b5fc-126">Çok dosyalı bir C# programı derlendiğinde, tüm kaynak dosyaları birlikte işlendiğinde ve kaynak dosyaları serbestçe birbirlerine referans verebilirsiniz-kavramsal olarak, tüm kaynak dosyaları işlenmeden önce büyük bir dosyaya entegre edilmiş gibidir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="2b5fc-127">Birkaç istisna dışında bildirim sırası önemsiz olduğundan, C#'da iletme bildirimleri hiçbir zaman gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="2b5fc-128">C# bir kaynak dosyayı yalnızca bir ortak türü bildirmekle sınırlamaz veya kaynak dosyada bildirilen bir türle eşleşecek şekilde kaynak dosyanın adını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2b5fc-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b5fc-129">[Önceki](index.md)
>[Sonraki](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="2b5fc-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
