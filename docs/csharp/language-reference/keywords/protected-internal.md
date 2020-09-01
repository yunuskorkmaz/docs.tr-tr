---
description: Protected Internal-C# başvurusu
title: Protected Internal-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: a7537fba93c0d7145f04c6236d15c11b70f8bf98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139443"
---
# <a name="protected-internal-c-reference"></a>korumalı iç (C# Başvurusu)

`protected internal`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Korunan bir iç üyeye geçerli derlemeden veya kapsayan sınıftan türetilmiş türlerden erişilebilir. `protected internal`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

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

Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .
İlk dosya bir ortak temel sınıf, `BaseClass` ve başka bir sınıf içerir `TestAccess` . `BaseClass` , türü tarafından erişilen korumalı bir iç üyeye sahip `myValue` `TestAccess` .
İkinci dosyada, `myValue` bir örneği üzerinden erişim girişimi `BaseClass` bir hata üretir, bu üyeye türetilmiş bir sınıf örneği aracılığıyla erişim `DerivedClass` başarılı olur.

Struct üye olamaz `protected internal` çünkü yapı devralınamaz.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [genel](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
