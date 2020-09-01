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
# <a name="extern-c-reference"></a>extern (C# Başvurusu)

`extern`Değiştirici, dışarıdan uygulanan bir yöntemi bildirmek için kullanılır. Bir değiştiricinin ortak kullanımı, `extern` `DllImport` yönetilmeyen koda çağrı yapmak Için birlikte çalışabilirlik Hizmetleri kullandığınızda özniteliğiyle birlikte bulunur. Bu durumda, `static` Aşağıdaki örnekte gösterildiği gibi yöntemi de olarak bildirilmelidir:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern`Anahtar sözcüğü aynı zamanda bir dış derleme diğer adı tanımlayabilir, bu da aynı bileşenin farklı sürümlerine tek bir bütünleştirilmiş kod içinden başvuruda bulunmak mümkün hale gelir. Daha fazla bilgi için bkz. [extern diğer ad](extern-alias.md).

[abstract](abstract.md) `extern` Aynı üyeyi değiştirmek için soyut ve değiştiricilerin birlikte kullanılması hatadır. `extern`Değiştiricinin kullanılması yöntemin C# kodu dışında uygulandığı anlamına gelir, ancak `abstract` değiştiricinin kullanılması, yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir.

extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.

## <a name="example-1"></a>Örnek 1

Bu örnekte, Program kullanıcıdan bir dize alır ve iletiyi bir ileti kutusu içinde görüntüler. Program, `MessageBox` User32.dll kitaplığından içeri aktarılan yöntemi kullanır.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Örnek 2

Bu örnek, bir C kitaplığına (yerel DLL) çağıran bir C# programını gösterir.

1. Aşağıdaki C dosyasını oluşturun ve adlandırın `cmdll.c` :

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cmdll.c` komut istemine **CL-ld Cmdll. c** yazarak dosyayı derleyin.

3. Aynı dizinde aşağıdaki C# dosyasını oluşturun ve adlandırın `cm.cs` :

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

4. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel araçlar komut Istemi penceresi açın ve `cm.cs` şunu yazarak dosyayı derleyin:

    > **csc cm.cs** (x64 komut istemi için) — veya — **csc-platform: x86 cm.cs** (x32 komut istemi için)

    Bu, yürütülebilir dosyayı oluşturur `cm.exe` .

5. `cm.exe` öğesini çalıştırın. `SampleMethod`Yöntemi, 5 değerini, 10 ile çarpılan değeri döndüren dll dosyasına geçirir.  Program aşağıdaki çıktıyı üretir:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
