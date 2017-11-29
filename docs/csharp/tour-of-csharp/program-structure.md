---
title: "C# programı yapısı - C# dili turu"
description: "C# programının temel yapı taşlarının öğrenin"
keywords: .NET .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a><span data-ttu-id="3cda1-104">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="3cda1-104">Program Structure</span></span>

<span data-ttu-id="3cda1-105">C# anahtar kuruluş kavramlar ***programları***, ***ad alanları***, ***türleri***, ***üyeleri***, ve ***derlemeleri***.</span><span class="sxs-lookup"><span data-stu-id="3cda1-105">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="3cda1-106">C# programları bir veya daha fazla kaynak dosyalarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="3cda1-106">C# programs consist of one or more source files.</span></span> <span data-ttu-id="3cda1-107">Programları üyeleri içerir ve ad alanında düzenlenebilir türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="3cda1-107">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="3cda1-108">Sınıflar ve arabirimler türlerine örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-108">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="3cda1-109">Alanlar, yöntemleri, özellikleri ve olayları üyeleri gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-109">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="3cda1-110">C# programları derlendiğinde fiziksel olarak derlemelerine paketlenir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-110">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="3cda1-111">Derlemeler, genellikle dosya uzantısına sahip `.exe` veya `.dll`olup uyguladıkları bağlı olarak ***uygulamaları*** veya ***kitaplıkları***sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="3cda1-111">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="3cda1-112">Adlı bir sınıf örneği bildirir `Stack` adlı bir ad alanındaki `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="3cda1-112">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="3cda1-113">Bu sınıf tam adı `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="3cda1-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="3cda1-114">Sınıf birkaç üyeler içerir: adında bir alan `top`, adlı iki yöntem `Push` ve `Pop`ve adlı bir iç içe geçmiş sınıf `Entry`.</span><span class="sxs-lookup"><span data-stu-id="3cda1-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="3cda1-115">`Entry` Daha fazla sınıf içerir üç üye: adında bir alan `next`, adında bir alan `data`hem de bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="3cda1-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="3cda1-116">Örneğin kaynak kodu dosyasına depolanan varsayılarak `acme.cs`, komut satırı</span><span class="sxs-lookup"><span data-stu-id="3cda1-116">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="3cda1-117">Örnek bir kitaplık olarak derler (olmadan kod bir `Main` giriş noktası) ve adlı bir derleme üretir `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="3cda1-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3cda1-118">Yukarıdaki kullanım örnekleri `csc` komut satırında C# Derleyici olarak.</span><span class="sxs-lookup"><span data-stu-id="3cda1-118">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="3cda1-119">Bu derleyici yürütülebilir bir windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-119">This compiler is a windows executable.</span></span> <span data-ttu-id="3cda1-120">C# diğer platformlarda kullanmak için .NET Core araçları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-120">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="3cda1-121">.NET Core ekosistemi kullanan `dotnet` komut satırı derlemeleri yönetmek için CLI.</span><span class="sxs-lookup"><span data-stu-id="3cda1-121">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="3cda1-122">Bu bağımlılıklar yönetme ve C# derleyicisini çağırma içerir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-122">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="3cda1-123">Bkz: [Bu öğretici](../../core/tutorials/using-with-xplat-cli.md) araçların .NET Core tarafından desteklenen platformlardaki tam bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="3cda1-123">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="3cda1-124">Derlemeleri Ara dile (IL) yönergeleri biçiminde yürütülebilir kod ve meta veri biçiminde simgesel bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-124">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="3cda1-125">Çalıştırılmadan önce bir bütünleştirilmiş IL kodu işlemciye özgü kodu otomatik olarak .NET ortak dil çalışma zamanı Just-In-Time (JIT) derleyici tarafından dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3cda1-125">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="3cda1-126">Bütünleştirilmiş kod ve meta verileri içeren işlevlerin kendiliğinden açıklayıcı bir birim olduğundan için gerek yoktur `#include` yönergeleri ve C# üstbilgi dosyaları.</span><span class="sxs-lookup"><span data-stu-id="3cda1-126">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="3cda1-127">Genel türler ve belirli bir derlemesinde bulunan üyeleri program derlerken, derleme yalnızca başvurarak bir C# programı içinde kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-127">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="3cda1-128">Örneğin, bu programın kullandığı `Acme.Collections.Stack` sınıfıyla `acme.dll` derleme:</span><span class="sxs-lookup"><span data-stu-id="3cda1-128">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="3cda1-129">Program dosyada saklanıyorsa `example.cs`, `example.cs` olan derlenmiş, acme.dll derleme derleyicinin /r seçeneğini kullanarak başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="3cda1-129">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="3cda1-130">Bu adlı bir yürütülebilir derleme oluşturur `example.exe`, çalıştırdığınızda, çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cda1-130">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="3cda1-131">C# kaynak metni birkaç kaynak dosyalarının depolanacağı bir programın izin verir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-131">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="3cda1-132">Çok dosyalı C# programı derlenmiş, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyaları serbestçe birbirine başvurabilir — kavramsal olarak, tüm kaynak dosyalarını tek bir büyük dosyaya işlenmeden önce art arda eklenmiş gibi değil.</span><span class="sxs-lookup"><span data-stu-id="3cda1-132">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="3cda1-133">Çok az istisnalar bildirim sırasında Önemsiz olduğundan, iletme bildirimleri hiçbir zaman C# ' ta gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-133">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="3cda1-134">C#, yalnızca bir ortak türü bildirmek için bir kaynak dosyası sınırlamaz Ayrıca kaynak dosyasında bildirilen türüyle eşleşecek şekilde kaynak dosyasının adı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3cda1-134">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3cda1-135">[Önceki](index.md)
[sonraki](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="3cda1-135">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
