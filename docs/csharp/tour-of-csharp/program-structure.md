---
title: C#Program yapısı - Turu C# dil
description: Temel yapı taşları hakkında bilgi edinin bir C# programı
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: de10cd000b4028a66ce6dd6f21e39c013e38ecd2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675955"
---
# <a name="program-structure"></a><span data-ttu-id="580c2-103">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="580c2-103">Program Structure</span></span>

<span data-ttu-id="580c2-104">C# anahtar kuruluş kavramlar ***programlar***, ***ad alanları***, ***türleri***, ***üyeleri***, ve ***derlemeleri***.</span><span class="sxs-lookup"><span data-stu-id="580c2-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="580c2-105">C# programları, bir veya daha fazla kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="580c2-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="580c2-106">Programları üyeleri içerir ve ad alanları olarak düzenlenmiş türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="580c2-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="580c2-107">Sınıflar ve arabirimler türleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="580c2-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="580c2-108">Alanlar, yöntemler, özellikler ve olaylar üyeleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="580c2-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="580c2-109">C# programları derlendiğinde, bunlar derlemelerine fiziksel olarak paketlenir.</span><span class="sxs-lookup"><span data-stu-id="580c2-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="580c2-110">Derlemeler genellikle dosya uzantısına sahip `.exe` veya `.dll`uyguladıkları mi bağlı olarak ***uygulamaları*** veya ***kitaplıkları***sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="580c2-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="580c2-111">Örnek adlı bir sınıfı bildirir `Stack` adlı bir ad alanında `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="580c2-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="580c2-112">Bu sınıfın tam adı `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="580c2-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="580c2-113">Sınıf bazı üyeler içerir: adlı bir alan `top`, adlı iki yöntem `Push` ve `Pop`ve bir iç içe geçmiş sınıf adlı `Entry`.</span><span class="sxs-lookup"><span data-stu-id="580c2-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="580c2-114">`Entry` Sınıfı daha da içeren üç üye: adlı bir alan `next`, adında bir alan `data`ve bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="580c2-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="580c2-115">Örnek kaynak kodu dosyasında depolanan varsayarak `acme.cs`, komut satırı</span><span class="sxs-lookup"><span data-stu-id="580c2-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="580c2-116">Örnek bir kitaplık olarak derler (olmadan kod bir `Main` giriş noktası) adlı bir derleme oluşturur `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="580c2-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="580c2-117">Kullanım Yukarıdaki örneklerde `csc` komut satırı olarak C# derleyici.</span><span class="sxs-lookup"><span data-stu-id="580c2-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="580c2-118">Bir Windows yürütülebilir derleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="580c2-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="580c2-119">Kullanılacak C# diğer platformlarda için .NET Core Araçları'nı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="580c2-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="580c2-120">.NET Core ekosistemi kullanan `dotnet` komut satırı yapıları yönetmek için CLI.</span><span class="sxs-lookup"><span data-stu-id="580c2-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="580c2-121">Bu bağımlılıkları yönetmek ve çağırma içerir C# derleyici.</span><span class="sxs-lookup"><span data-stu-id="580c2-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="580c2-122">Bkz: [Bu öğreticide](../../core/tutorials/using-with-xplat-cli.md) .NET Core tarafından desteklenen platformlarda, araçlarda tam bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="580c2-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="580c2-123">Derlemeleri yürütülebilir kod biçiminde Ara dil (IL) yönergeleri ve simgesel bilgiler meta veri biçiminde içerir.</span><span class="sxs-lookup"><span data-stu-id="580c2-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="580c2-124">Çalıştırılmadan önce bir derlemede IL kodu işlemciye özgü kodu .NET ortak dil çalışma zamanı tam zamanında (JIT) derleyici tarafından otomatik olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="580c2-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="580c2-125">Bir derleme kendiliğinden açıklayıcı bir işlevsellik hem kod hem de meta verileri içeren birimi olduğundan için gerek yoktur `#include` yönergeleri ve C# üst bilgi dosyaları.</span><span class="sxs-lookup"><span data-stu-id="580c2-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="580c2-126">Genel türler ve üyeler belirli bir derlemede bulunan program derlerken bu derlemeye yalnızca başvurarak bir C# programı içinde kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="580c2-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="580c2-127">Örneğin, bu programın kullandığı `Acme.Collections.Stack` gelen sınıfı `acme.dll` derleme:</span><span class="sxs-lookup"><span data-stu-id="580c2-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="580c2-128">Program dosyada saklanıyorsa `example.cs`, `example.cs` olduğundan derlenemiyor; acme.dll derleme derleyicinin /r seçeneği kullanılarak başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="580c2-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="580c2-129">Bu adında bir yürütülebilir bir derleme oluşturur `example.exe`, çalıştırdığınızda, çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="580c2-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="580c2-130">C# kaynak metni bir programın çeşitli kaynak dosyalarında depolanan izin verir.</span><span class="sxs-lookup"><span data-stu-id="580c2-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="580c2-131">Çok dosyalı C# programı derlenir, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyaları serbestçe birbirlerine başvurabilir — kavramsal olarak, tüm kaynak dosyalarını tek bir büyük dosyaya işlenmeden önce art arda eklenmiş gibi öyledir.</span><span class="sxs-lookup"><span data-stu-id="580c2-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="580c2-132">Çok az sayıda özel durum dışında bildirim sırasında Önemsiz olduğundan, iletme bildirimleri hiçbir zaman C# ' de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="580c2-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="580c2-133">C#, yalnızca bir genel türü bildirmek için bir kaynak dosyası sınırlamaz veya kaynak dosyada bildirilen bir tür ile eşleştirilecek kaynak dosyasının adı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="580c2-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="580c2-134">[Önceki](index.md)
>[İleri](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="580c2-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>