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
ms.openlocfilehash: 387ef707166705c4df501bd6740d438683aa2d69
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203008"
---
# <a name="extern-c-reference"></a>extern (C# Başvurusu)

`extern` Değiştirici, dışarıdan uygulanan bir yöntemi bildirmek için kullanılır. Bir `extern` değiştiricinin ortak kullanımı, yönetilmeyen koda çağrı `DllImport` yapmak için birlikte çalışabilirlik Hizmetleri kullandığınızda özniteliğiyle birlikte bulunur. Bu durumda, aşağıdaki örnekte gösterildiği gibi yöntemi de olarak `static`bildirilmelidir:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` Anahtar sözcüğü aynı zamanda bir dış derleme diğer adı tanımlayabilir, bu da aynı bileşenin farklı sürümlerine tek bir bütünleştirilmiş kod içinden başvuruda bulunmak mümkün hale gelir. Daha fazla bilgi için bkz. [extern diğer ad](extern-alias.md).

Aynı üyeyi değiştirmek için [soyut](abstract.md) ve `extern` değiştiricilerin birlikte kullanılması hatadır. Değiştiricinin kullanılması, yöntemin C# kod dışında uygulandığı anlamına gelir `abstract` , ancak değiştiricinin kullanılması, yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir. `extern`

extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.

## <a name="example-1"></a>Örnek 1

Bu örnekte, Program kullanıcıdan bir dize alır ve iletiyi bir ileti kutusu içinde görüntüler. Program, User32. `MessageBox` dll kitaplığından içeri aktarılan yöntemi kullanır.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Örnek 2

Bu örnek, bir C# C kitaplığına (yerel dll) çağıran bir programı gösterir.

1. Aşağıdaki C dosyasını oluşturun ve adlandırın `cmdll.c`:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut istemi penceresi açın ve komut istemine `cmdll.c` **CL-ld Cmdll. c** yazarak dosyayı derleyin.

3. Aynı dizinde aşağıdaki C# dosyayı oluşturun ve adlandırın `cm.cs`:

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

4. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut istemi penceresi açın ve şunu yazarak `cm.cs` dosyayı derleyin:

    > **csc cm.cs** (x64 komut istemi için) — veya — **csc-platform: x86 cm.cs** (x32 komut istemi için)

    Bu, yürütülebilir dosyayı `cm.exe`oluşturur.

5. `cm.exe`'i çalıştırın. `SampleMethod` Yöntemi, 5 değerini, 10 ile çarpılan değeri döndüren dll dosyasına geçirir.  Program aşağıdaki çıktıyı üretir:

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
- [Değiştiriciler](modifiers.md)
