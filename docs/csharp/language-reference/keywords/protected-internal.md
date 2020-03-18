---
title: korumalı dahili - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713202"
---
# <a name="protected-internal-c-reference"></a>korumalı dahili (C# Reference)

`protected internal` Anahtar kelime birleşimi bir üye erişim değiştiricidir. Korumalı bir iç üyeye geçerli derlemeden veya içeren sınıftan türetilen türlerden erişilebilir. Diğer erişim `protected internal` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.

## <a name="example"></a>Örnek

Taban sınıfın korumalı bir iç üyesine, içerdiği derlemedeki herhangi bir türden erişilebilir. Erişim türemiş sınıf türünden bir değişken aracılığıyla oluşursa, başka bir derlemede bulunan türemiş bir sınıfta da erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .
İlk dosya, ortak taban `BaseClass`sınıf ve başka `TestAccess`bir sınıf içerir. `BaseClass`türüne göre erişilen korumalı bir `TestAccess` dahili üyeye `myValue`sahip.
İkinci dosyada, bir hata `myValue` örneği `BaseClass` üzerinden erişim girişimi bir hata üretirken, türetilmiş bir `DerivedClass` sınıfın bir örneği aracılığıyla bu üyeye erişim başarılı olacaktır.

Yapı üyeleri, yapının devralınamayacağı için olamaz. `protected internal`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [Kamu](public.md)
- [Özel](private.md)
- [Iç](internal.md)
- [Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
