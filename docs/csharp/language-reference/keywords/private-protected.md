---
title: özel korumalı-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301807"
---
# <a name="private-protected-c-reference"></a>özel korumalı (C# Başvurusu)

`private protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Özel korumalı bir üyeye, kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde erişilebilir. `private protected`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

> [!NOTE]
> `private protected`Access Modifier, C# sürüm 7,2 ve üzeri sürümlerde geçerlidir.

## <a name="example"></a>Örnek

Bir temel sınıfın özel korumalı bir üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türü ise, kendisini kapsayan derlemede bulunan türetilmiş türlerden erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .
İlk dosya, bir ortak temel sınıf, `BaseClass` ve ondan türetilmiş bir tür içerir `DerivedClass1` . `BaseClass`, `myValue` iki şekilde erişmeye çalışan özel korumalı bir üyenin sahibidir `DerivedClass1` . Bir örneğinden ilk erişme girişimi `myValue` `BaseClass` bir hata üretir. Ancak, bunu devralınmış bir üye olarak kullanma girişimi `DerivedClass1` başarılı olur.

İkinci dosyada, devralınan bir üye olarak erişim girişimi `myValue` `DerivedClass2` yalnızca Assembly1 içindeki türetilmiş türler tarafından erişilebilen bir hata oluşturur.

`Assembly1.cs` <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Bu adları içeriyorsa `Assembly2` , türetilmiş sınıfın `DerivedClass1` `private protected` içinde belirtilen üyelere erişimi olur `BaseClass` . `InternalsVisibleTo``private protected`üyeleri diğer derlemelerdeki türetilmiş sınıflara görünür hale getirir.

Struct üye olamaz `private protected` çünkü yapı devralınamaz.

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
- [özelleştirme](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
