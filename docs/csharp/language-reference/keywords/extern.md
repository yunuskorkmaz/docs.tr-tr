---
title: extern değiştiricisi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: d860f1a3c6917238a529093672dc5f2abc5ae066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620206"
---
# <a name="extern-c-reference"></a><span data-ttu-id="81f94-102">extern (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="81f94-102">extern (C# Reference)</span></span>

<span data-ttu-id="81f94-103">`extern` Değiştiricisi dışarıdan uygulanan bir yöntemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="81f94-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="81f94-104">Yaygın `extern` değiştiricisinin `DllImport` yönetilmeyen koda çağrı yapmak birlikte çalışma hizmetlerini kullanırken özniteliği.</span><span class="sxs-lookup"><span data-stu-id="81f94-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="81f94-105">Bu durumda, yöntem olarak da bildirilmeleri gerekir `static`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="81f94-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="81f94-106">`extern` Anahtar sözcüğü, tek bir derleme içinde aynı bileşenin farklı sürümlerine başvurmayı olanaklı kılan bir dış derleme takma adı da tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="81f94-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="81f94-107">Daha fazla bilgi için [extern diğer adı](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="81f94-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="81f94-108">Kullanılacak bir hata olduğunu [soyut](abstract.md) ve `extern` birlikte aynı üyeyi değiştirmek için değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="81f94-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="81f94-109">Kullanarak `extern` değiştiricisi anlamına gelir yöntemin C# kodunun dışında uygulandığını kullanarak ise `abstract` değiştiricisini kullanmak yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir;.</span><span class="sxs-lookup"><span data-stu-id="81f94-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="81f94-110">extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="81f94-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="81f94-111">C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.</span><span class="sxs-lookup"><span data-stu-id="81f94-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="81f94-112">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="81f94-112">Example 1</span></span>

<span data-ttu-id="81f94-113">Bu örnekte, program kullanıcıdan bir dize alır ve bir ileti kutusu içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="81f94-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="81f94-114">Programın kullandığı `MessageBox` User32.dll kitaplığından aktarılan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81f94-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="81f94-115">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="81f94-115">Example 2</span></span>

<span data-ttu-id="81f94-116">Bu örnekte, bir C kitaplığına (bir yerel DLL) çağıran bir C# programı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="81f94-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="81f94-117">Aşağıdaki C dosyası oluşturun ve adlandırın `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="81f94-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="81f94-118">Visual Studio Kurulum dizininden bir Visual Studio x64 (veya x32) yerel Araçlar komut istemi penceresi açın ve `cmdll.c` yazarak dosya **cl -LD cmdll.c** komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="81f94-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="81f94-119">Aynı dizinde, aşağıdaki C# dosyası oluşturun ve adlandırın `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="81f94-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. <span data-ttu-id="81f94-120">Visual Studio Kurulum dizininden bir Visual Studio x64 (veya x32) yerel Araçlar komut istemi penceresi açın ve `cm.cs` yazarak dosyası:</span><span class="sxs-lookup"><span data-stu-id="81f94-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="81f94-121">**CSC cm.cs** (x64 için komut istemi) — veya — **csc-platform: x 86 cm.cs** (x32 için komut istemi)</span><span class="sxs-lookup"><span data-stu-id="81f94-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="81f94-122">Bu yürütülebilir dosya oluşturur `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="81f94-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="81f94-123">`cm.exe`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="81f94-123">Run `cm.exe`.</span></span> <span data-ttu-id="81f94-124">`SampleMethod` Yöntemi 5 değerini değerin 10 ile çarpılmış olarak döndüren DLL dosyasına geçirir.</span><span class="sxs-lookup"><span data-stu-id="81f94-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="81f94-125">Program şu çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="81f94-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="81f94-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="81f94-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="81f94-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81f94-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="81f94-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="81f94-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81f94-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81f94-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81f94-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="81f94-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="81f94-131">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="81f94-131">Modifiers</span></span>](modifiers.md)
