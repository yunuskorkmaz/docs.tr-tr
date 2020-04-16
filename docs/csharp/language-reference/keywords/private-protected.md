---
title: özel korumalı - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463050"
---
# <a name="private-protected-c-reference"></a>özel korumalı (C# Reference)

`private protected` Anahtar kelime birleşimi bir üye erişim değiştiricidir. Özel korumalı bir üye, içerdiği sınıftan türetilen türlere, ancak yalnızca kendi içderlemesi içinde erişilebilir. Diğer erişim `private protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.

> [!NOTE]
> Erişim `private protected` değiştirici C# sürüm 7.2 ve sonraki sürümlerinde geçerlidir.

## <a name="example"></a>Örnek

Taban sınıfın özel korumalı üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türüyse, içerdiği derlemedeki türetilmiş türlerden erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

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

Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .
İlk dosya, ortak taban `BaseClass`sınıf ve ondan türetilen `DerivedClass1`bir tür içerir. `BaseClass`iki şekilde erişmeye `myValue`çalışan `DerivedClass1` özel bir korumalı üyesi ne sahiptir. Bir örnek üzerinden `myValue` erişmek için `BaseClass` ilk girişimi bir hata üretecek. Ancak, kalıtsal bir üye olarak kullanma `DerivedClass1` girişimi başarılı olacaktır.

İkinci dosyada, devralınan `myValue` bir üye `DerivedClass2` olarak erişme girişimi, yalnızca Derleme1'de türetilen türler tarafından erişilebilir olduğundan bir hata üretir.

Bir `Assembly1.cs` ad <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `Assembly2`içeriyorsa, `DerivedClass1` türemiş `private protected` sınıfın ' `BaseClass`da bildirilen üyelere erişimi olacak. `InternalsVisibleTo`üyeleri `private protected` diğer derlemelerde türetilmiş sınıflara görünür kılar.

Yapı üyeleri, yapının devralınamayacağı için olamaz. `private protected`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
