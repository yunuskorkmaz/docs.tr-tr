---
title: extern değiştirici- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 5f4a4b143578603a3285b1a3bc0b1efa11840e77
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422818"
---
# <a name="extern-c-reference"></a>extern (C# Başvurusu)

`extern` değiştiricisi dışarıdan uygulanan bir yöntemi bildirmek için kullanılır. Yönetilmeyen koda çağrı yapmak için birlikte çalışma Hizmetleri kullandığınızda `extern` değiştiricisinin yaygın olarak kullanılması `DllImport` özniteliğidir. Bu durumda, aşağıdaki örnekte gösterildiği gibi, yöntemi de `static`olarak bildirilmelidir:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` anahtar sözcüğü ayrıca bir dış derleme diğer adı tanımlayabilir, bu da aynı bileşenin farklı sürümlerine tek bir bütünleştirilmiş kod içinden başvuruda bulunmak mümkün hale gelir. Daha fazla bilgi için bkz. [extern diğer ad](extern-alias.md).

Aynı üyeyi değiştirmek için [soyut](abstract.md) ve `extern` değiştiricilerini kullanmak hatadır. `extern` değiştiricisinin kullanılması yöntemin dışında C# uygulandığı anlamına gelir, ancak `abstract` değiştiricinin kullanılması, yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir.

extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.

## <a name="example-1"></a>Örnek 1

Bu örnekte, Program kullanıcıdan bir dize alır ve iletiyi bir ileti kutusu içinde görüntüler. Program, User32. dll kitaplığından içeri aktarılan `MessageBox` yöntemini kullanır.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Örnek 2

Bu örnek, bir C# C kitaplığına (yerel dll) çağıran bir programı gösterir.

1. Aşağıdaki C dosyasını oluşturun ve `cmdll.c`adlandırın:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve komut istemine **CL-ld Cmdll. c** yazarak `cmdll.c` dosyasını derleyin.

3. Aynı dizinde aşağıdaki C# dosyayı oluşturun ve `cm.cs`olarak adlandırın:

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

4. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cm.cs` dosyasını şunu yazarak derleyin:

    > **csc cm.cs** (x64 komut istemi için) — veya — **csc-platform: x86 cm.cs** (x32 komut istemi için)

    Bu işlem yürütülebilir dosya `cm.exe`oluşturur.

5. `cm.exe`'i çalıştırın. `SampleMethod` yöntemi, 5 değerini, 10 ile çarpılan değeri döndüren DLL dosyasına geçirir.  Program aşağıdaki çıktıyı üretir:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
