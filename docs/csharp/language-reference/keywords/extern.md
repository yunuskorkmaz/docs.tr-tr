---
title: extern değiştirici - C# Referans
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713533"
---
# <a name="extern-c-reference"></a><span data-ttu-id="879eb-102">extern (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="879eb-102">extern (C# Reference)</span></span>

<span data-ttu-id="879eb-103">`extern` Değiştirici, harici olarak uygulanan bir yöntemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="879eb-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="879eb-104">`extern` Değiştiricinin yaygın kullanımı, `DllImport` yönetilmeyen koda çağırmak için Interop hizmetlerini kullanırken özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="879eb-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="879eb-105">Bu durumda, yöntem de olarak `static`bildirilmelidir , aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="879eb-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="879eb-106">`extern` Anahtar kelime, aynı bileşenin farklı sürümlerine tek bir derleme içinden başvurmayı mümkün kılan harici bir derleme diğer adı da tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="879eb-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="879eb-107">Daha fazla bilgi için [extern diğer adı.](extern-alias.md)</span><span class="sxs-lookup"><span data-stu-id="879eb-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="879eb-108">Soyut [ve](abstract.md) `extern` değiştiriciler aynı üyeyi değiştirmek için birlikte kullanmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="879eb-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="879eb-109">Değiştiricinin `extern` kullanılması, yöntemin C# kodu dışında uygulandığı anlamına gelirken, `abstract` değiştiricinin kullanılması yöntem uygulamasının sınıfta sağlanamadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="879eb-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="879eb-110">extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="879eb-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="879eb-111">C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.</span><span class="sxs-lookup"><span data-stu-id="879eb-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="879eb-112">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="879eb-112">Example 1</span></span>

<span data-ttu-id="879eb-113">Bu örnekte, program kullanıcıdan bir dize alır ve bir ileti kutusunun içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="879eb-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="879eb-114">Program User32.dll kitaplığından alınan `MessageBox` yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="879eb-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="879eb-115">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="879eb-115">Example 2</span></span>

<span data-ttu-id="879eb-116">Bu örnek, C kitaplığına (yerel bir DLL) çağıran bir C# programını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="879eb-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="879eb-117">Aşağıdaki C dosyasını oluşturun `cmdll.c`ve adlandırın:</span><span class="sxs-lookup"><span data-stu-id="879eb-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="879eb-118">Visual Studio yükleme dizininden Visual Studio x64 (veya x32) Native Tools `cmdll.c` Komut Komut Ustem penceresini açın ve komut isteminde **cl -LD cmdll.c** yazarak dosyayı derle.</span><span class="sxs-lookup"><span data-stu-id="879eb-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="879eb-119">Aynı dizinde, aşağıdaki C# dosyasını oluşturun `cm.cs`ve adlandırın:</span><span class="sxs-lookup"><span data-stu-id="879eb-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="879eb-120">Visual Studio yükleme dizininden Visual Studio x64 (veya x32) Native Tools `cm.cs` Komut Komut Ustem penceresini açın ve dosyayı yazarak derle:</span><span class="sxs-lookup"><span data-stu-id="879eb-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="879eb-121">**csc cm.cs** (x64 komut istemi için) —veya— **csc -platform:x86 cm.cs** (x32 komut istemi için)</span><span class="sxs-lookup"><span data-stu-id="879eb-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="879eb-122">Bu, yürütülebilir `cm.exe`dosyayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879eb-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="879eb-123">`cm.exe` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="879eb-123">Run `cm.exe`.</span></span> <span data-ttu-id="879eb-124">Yöntem, `SampleMethod` 5 değerini DLL dosyasına geçirir ve değeri 10 ile çarpar.</span><span class="sxs-lookup"><span data-stu-id="879eb-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="879eb-125">Program aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="879eb-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="879eb-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="879eb-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="879eb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="879eb-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="879eb-128">C# Referans</span><span class="sxs-lookup"><span data-stu-id="879eb-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="879eb-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="879eb-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="879eb-130">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="879eb-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="879eb-131">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="879eb-131">Modifiers</span></span>](index.md)
