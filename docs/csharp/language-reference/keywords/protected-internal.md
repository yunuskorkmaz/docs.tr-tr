---
title: korumalı iç C# başvuru
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713202"
---
# <a name="protected-internal-c-reference"></a>korumalı iç (C# başvuru)

`protected internal` anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Korunan bir iç üyeye geçerli derlemeden veya kapsayan sınıftan türetilmiş türlerden erişilebilir. Diğer erişim değiştiricilerine sahip `protected internal` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

## <a name="example"></a>Örnek

Bir temel sınıfın korunan iç üyesine, kendisini içeren derleme içindeki herhangi bir türden erişilebilir. Ayrıca, başka bir derlemede bulunan türetilmiş bir sınıfta, yalnızca erişim türetilmiş sınıf türünün bir değişkeniyle gerçekleşirse erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

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

Bu örnek, `Assembly1.cs` ve `Assembly2.cs`iki dosya içerir.
İlk dosya, `TestAccess`bir ortak temel sınıf, `BaseClass`ve başka bir sınıf içerir. `BaseClass`, `TestAccess` türü tarafından erişilen korumalı bir dahili üyeye sahip `myValue`sahip.
İkinci dosyada, bir `BaseClass` örneği üzerinden `myValue` erişme girişimi bir hata üretir, bu üyeye türetilmiş bir sınıfın bir örneği aracılığıyla erişim elde edilir `DerivedClass` başarılı olur.

Struct devralınamadığı için yapı üyeleri `protected internal` olamaz.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
