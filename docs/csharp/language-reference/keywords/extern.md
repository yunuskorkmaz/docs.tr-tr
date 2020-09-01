---
description: extern değiştirici-C# başvurusu
title: extern değiştirici-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138975"
---
# <a name="extern-c-reference"></a><span data-ttu-id="7f340-103">extern (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7f340-103">extern (C# Reference)</span></span>

<span data-ttu-id="7f340-104">`extern`Değiştirici, dışarıdan uygulanan bir yöntemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f340-104">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="7f340-105">Bir değiştiricinin ortak kullanımı, `extern` `DllImport` yönetilmeyen koda çağrı yapmak Için birlikte çalışabilirlik Hizmetleri kullandığınızda özniteliğiyle birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="7f340-105">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="7f340-106">Bu durumda, `static` Aşağıdaki örnekte gösterildiği gibi yöntemi de olarak bildirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="7f340-106">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="7f340-107">`extern`Anahtar sözcüğü aynı zamanda bir dış derleme diğer adı tanımlayabilir, bu da aynı bileşenin farklı sürümlerine tek bir bütünleştirilmiş kod içinden başvuruda bulunmak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="7f340-107">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="7f340-108">Daha fazla bilgi için bkz. [extern diğer ad](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="7f340-108">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="7f340-109">[abstract](abstract.md) `extern` Aynı üyeyi değiştirmek için soyut ve değiştiricilerin birlikte kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="7f340-109">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="7f340-110">`extern`Değiştiricinin kullanılması yöntemin C# kodu dışında uygulandığı anlamına gelir, ancak `abstract` değiştiricinin kullanılması, yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7f340-110">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="7f340-111">extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="7f340-111">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="7f340-112">C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.</span><span class="sxs-lookup"><span data-stu-id="7f340-112">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="7f340-113">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="7f340-113">Example 1</span></span>

<span data-ttu-id="7f340-114">Bu örnekte, Program kullanıcıdan bir dize alır ve iletiyi bir ileti kutusu içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7f340-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="7f340-115">Program, `MessageBox` User32.dll kitaplığından içeri aktarılan yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f340-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="7f340-116">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="7f340-116">Example 2</span></span>

<span data-ttu-id="7f340-117">Bu örnek, bir C kitaplığına (yerel DLL) çağıran bir C# programını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f340-117">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="7f340-118">Aşağıdaki C dosyasını oluşturun ve adlandırın `cmdll.c` :</span><span class="sxs-lookup"><span data-stu-id="7f340-118">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="7f340-119">Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cmdll.c` komut istemine **CL-ld Cmdll. c** yazarak dosyayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="7f340-119">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="7f340-120">Aynı dizinde aşağıdaki C# dosyasını oluşturun ve adlandırın `cm.cs` :</span><span class="sxs-lookup"><span data-stu-id="7f340-120">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="7f340-121">Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cm.cs` şunu yazarak dosyayı derleyin:</span><span class="sxs-lookup"><span data-stu-id="7f340-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="7f340-122">**csc cm.cs** (x64 komut istemi için) — veya — **csc-platform: x86 cm.cs** (x32 komut istemi için)</span><span class="sxs-lookup"><span data-stu-id="7f340-122">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="7f340-123">Bu, yürütülebilir dosyayı oluşturur `cm.exe` .</span><span class="sxs-lookup"><span data-stu-id="7f340-123">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="7f340-124">`cm.exe` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7f340-124">Run `cm.exe`.</span></span> <span data-ttu-id="7f340-125">`SampleMethod`Yöntemi, 5 değerini, 10 ile çarpılan değeri döndüren dll dosyasına geçirir.</span><span class="sxs-lookup"><span data-stu-id="7f340-125">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="7f340-126">Program aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7f340-126">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="7f340-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7f340-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7f340-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f340-128">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="7f340-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f340-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f340-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7f340-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f340-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7f340-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7f340-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="7f340-132">Modifiers</span></span>](index.md)
