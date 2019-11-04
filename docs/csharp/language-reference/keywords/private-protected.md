---
title: özel korumalı C# başvuru
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: dfb2e754d81116012b9fc3f8fd4f6fe1ad0daef1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422620"
---
# <a name="private-protected-c-reference"></a>özel korumalı (C# başvuru)

`private protected` anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Özel korumalı bir üyeye, kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde erişilebilir. Diğer erişim değiştiricilerine sahip `private protected` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

> [!NOTE]
> `private protected` erişim değiştiricisi C# sürüm 7,2 ve üzeri sürümlerde geçerlidir.

## <a name="example"></a>Örnek

Bir temel sınıfın özel korumalı bir üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türü ise, kendisini kapsayan derlemede bulunan türetilmiş türlerden erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
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

Bu örnek, `Assembly1.cs` ve `Assembly2.cs`iki dosya içerir.
İlk dosya, bir ortak temel sınıf, `BaseClass`ve ondan türetilmiş bir tür içerir, `DerivedClass1`. `BaseClass`, `myValue``DerivedClass1` iki şekilde erişmeye çalıştığı özel korumalı bir üyeye sahip. Bir `BaseClass` örneği üzerinden `myValue` ilk kez erişme girişimi bir hata üretir. Ancak, bunu `DerivedClass1` devralınmış üye olarak kullanma girişimi başarılı olur.
İkinci dosyada, `DerivedClass2` devralınmış bir `myValue` erişme girişimi yalnızca Assembly1 içindeki türetilmiş türler tarafından erişilebilir olduğundan bir hata üretir.

Struct devralınamadığı için yapı üyeleri `private protected` olamaz.  

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
