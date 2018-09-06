---
title: extern değiştiricisi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 92ba2324345a6fc196dc3702e5f84886fba09ffc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799404"
---
# <a name="extern-c-reference"></a>extern (C# Başvurusu)

`extern` Değiştiricisi dışarıdan uygulanan bir yöntemi bildirmek için kullanılır. Yaygın `extern` değiştiricisinin `DllImport` yönetilmeyen koda çağrı yapmak birlikte çalışma hizmetlerini kullanırken özniteliği. Bu durumda, yöntem olarak da bildirilmeleri gerekir `static`, aşağıdaki örnekte gösterildiği gibi:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` Anahtar sözcüğü, tek bir derleme içinde aynı bileşenin farklı sürümlerine başvurmayı olanaklı kılan bir dış derleme takma adı da tanımlayabilir. Daha fazla bilgi için [extern diğer adı](extern-alias.md).

Kullanılacak bir hata olduğunu [soyut](abstract.md) ve `extern` birlikte aynı üyeyi değiştirmek için değiştiriciler. Kullanarak `extern` değiştiricisi anlamına gelir yöntemin C# kodunun dışında uygulandığını kullanarak ise `abstract` değiştiricisini kullanmak yöntem uygulamasının sınıfta sağlanmadığı anlamına gelir;.

extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.

## <a name="example-1"></a>Örnek 1

Bu örnekte, program kullanıcıdan bir dize alır ve bir ileti kutusu içinde görüntüler. Programın kullandığı `MessageBox` User32.dll kitaplığından aktarılan yöntemi.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Örnek 2

Bu örnekte, bir C kitaplığına (bir yerel DLL) çağıran bir C# programı gösterilmektedir.

1. Aşağıdaki C dosyası oluşturun ve adlandırın `cmdll.c`:

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. Visual Studio Kurulum dizininden bir Visual Studio x64 (veya x32) yerel Araçlar komut istemi penceresi açın ve `cmdll.c` yazarak dosya **cl -LD cmdll.c** komut isteminde.

3. Aynı dizinde, aşağıdaki C# dosyası oluşturun ve adlandırın `cm.cs`:

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

4. Visual Studio Kurulum dizininden bir Visual Studio x64 (veya x32) yerel Araçlar komut istemi penceresi açın ve `cm.cs` yazarak dosyası:

> **CSC cm.cs** (x64 için komut istemi) — veya — **csc-platform: x 86 cm.cs** (x32 için komut istemi)

Bu yürütülebilir dosya oluşturur `cm.exe`.

5. Çalıştırma `cm.exe`. `SampleMethod` Yöntemi 5 değerini değerin 10 ile çarpılmış olarak döndüren DLL dosyasına geçirir.  Program şu çıktıyı üretir:

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Değiştiriciler](modifiers.md)  