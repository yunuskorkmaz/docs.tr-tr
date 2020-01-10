---
title: extern değiştirici- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713533"
---
# <a name="extern-c-reference"></a><span data-ttu-id="a014a-102">extern (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a014a-102">extern (C# Reference)</span></span>

<span data-ttu-id="a014a-103">`extern` değiştiricisi dışarıdan uygulanan bir yöntemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a014a-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="a014a-104">Yönetilmeyen koda çağrı yapmak için birlikte çalışma Hizmetleri kullandığınızda `extern` değiştiricisinin yaygın olarak kullanılması `DllImport` özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="a014a-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="a014a-105">Bu durumda, aşağıdaki örnekte gösterildiği gibi, yöntemi de `static`olarak bildirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="a014a-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="a014a-106">`extern` anahtar sözcüğü ayrıca bir dış derleme diğer adı tanımlayabilir, bu da aynı bileşenin farklı sürümlerine tek bir bütünleştirilmiş kod içinden başvuruda bulunmak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a014a-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="a014a-107">Daha fazla bilgi için bkz. [extern diğer ad](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="a014a-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="a014a-108">Aynı üyeyi değiştirmek için [soyut](abstract.md) ve `extern` değiştiricilerini kullanmak hatadır.</span><span class="sxs-lookup"><span data-stu-id="a014a-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="a014a-109">`extern` değiştiricisinin kullanılması yöntemin dışında C# uygulandığı anlamına gelir, ancak `abstract` değiştiricinin kullanılması, yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a014a-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="a014a-110">extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="a014a-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="a014a-111">C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.</span><span class="sxs-lookup"><span data-stu-id="a014a-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="a014a-112">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a014a-112">Example 1</span></span>

<span data-ttu-id="a014a-113">Bu örnekte, Program kullanıcıdan bir dize alır ve iletiyi bir ileti kutusu içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a014a-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="a014a-114">Program, User32. dll kitaplığından içeri aktarılan `MessageBox` yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a014a-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="a014a-115">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a014a-115">Example 2</span></span>

<span data-ttu-id="a014a-116">Bu örnek, bir C# C kitaplığına (yerel dll) çağıran bir programı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a014a-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="a014a-117">Aşağıdaki C dosyasını oluşturun ve `cmdll.c`adlandırın:</span><span class="sxs-lookup"><span data-stu-id="a014a-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="a014a-118">Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve komut istemine **CL-ld Cmdll. c** yazarak `cmdll.c` dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="a014a-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="a014a-119">Aynı dizinde aşağıdaki C# dosyayı oluşturun ve `cm.cs`olarak adlandırın:</span><span class="sxs-lookup"><span data-stu-id="a014a-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="a014a-120">Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cm.cs` dosyasını şunu yazarak derleyin:</span><span class="sxs-lookup"><span data-stu-id="a014a-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="a014a-121">**csc cm.cs** (x64 komut istemi için) — veya — **csc-platform: x86 cm.cs** (x32 komut istemi için)</span><span class="sxs-lookup"><span data-stu-id="a014a-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="a014a-122">Bu işlem yürütülebilir dosya `cm.exe`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a014a-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="a014a-123">`cm.exe`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a014a-123">Run `cm.exe`.</span></span> <span data-ttu-id="a014a-124">`SampleMethod` yöntemi, 5 değerini, 10 ile çarpılan değeri döndüren DLL dosyasına geçirir.</span><span class="sxs-lookup"><span data-stu-id="a014a-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="a014a-125">Program aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a014a-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="a014a-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a014a-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a014a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a014a-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="a014a-128">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="a014a-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a014a-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a014a-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a014a-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a014a-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a014a-131">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a014a-131">Modifiers</span></span>](index.md)
