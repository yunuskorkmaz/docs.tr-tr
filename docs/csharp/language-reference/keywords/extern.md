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
# <a name="extern-c-reference"></a>extern (C# Başvurusu)

`extern` Değiştirici, harici olarak uygulanan bir yöntemi bildirmek için kullanılır. `extern` Değiştiricinin yaygın kullanımı, `DllImport` yönetilmeyen koda çağırmak için Interop hizmetlerini kullanırken özniteliktir. Bu durumda, yöntem de olarak `static`bildirilmelidir , aşağıdaki örnekte gösterildiği gibi:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` Anahtar kelime, aynı bileşenin farklı sürümlerine tek bir derleme içinden başvurmayı mümkün kılan harici bir derleme diğer adı da tanımlayabilir. Daha fazla bilgi için [extern diğer adı.](extern-alias.md)

Soyut [ve](abstract.md) `extern` değiştiriciler aynı üyeyi değiştirmek için birlikte kullanmak bir hatadır. Değiştiricinin `extern` kullanılması, yöntemin C# kodu dışında uygulandığı anlamına gelirken, `abstract` değiştiricinin kullanılması yöntem uygulamasının sınıfta sağlanamadığı anlamına gelir.

extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.

## <a name="example-1"></a>Örnek 1

Bu örnekte, program kullanıcıdan bir dize alır ve bir ileti kutusunun içinde görüntüler. Program User32.dll kitaplığından alınan `MessageBox` yöntemi kullanır.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Örnek 2

Bu örnek, C kitaplığına (yerel bir DLL) çağıran bir C# programını göstermektedir.

1. Aşağıdaki C dosyasını oluşturun `cmdll.c`ve adlandırın:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Visual Studio yükleme dizininden Visual Studio x64 (veya x32) Native Tools `cmdll.c` Komut Komut Ustem penceresini açın ve komut isteminde **cl -LD cmdll.c** yazarak dosyayı derle.

3. Aynı dizinde, aşağıdaki C# dosyasını oluşturun `cm.cs`ve adlandırın:

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

4. Visual Studio yükleme dizininden Visual Studio x64 (veya x32) Native Tools `cm.cs` Komut Komut Ustem penceresini açın ve dosyayı yazarak derle:

    > **csc cm.cs** (x64 komut istemi için) —veya— **csc -platform:x86 cm.cs** (x32 komut istemi için)

    Bu, yürütülebilir `cm.exe`dosyayı oluşturur.

5. `cm.exe` öğesini çalıştırın. Yöntem, `SampleMethod` 5 değerini DLL dosyasına geçirir ve değeri 10 ile çarpar.  Program aşağıdaki çıktıyı üretir:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
