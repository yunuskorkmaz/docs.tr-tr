---
title: Özel korumalı - C# başvurusu
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 35b7c6c4e271b7772968ad63926fe1e66b10a6fa
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633340"
---
# <a name="private-protected-c-reference"></a>private protected (C# Başvurusu)

`private protected` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur. Özel bir korumalı üye, kapsayan sınıfı ancak kendi içeren bütünleştirilmiş kod içinde yalnızca türetilen türler tarafından erişilebilir. Bir karşılaştırması `private protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](accessibility-levels.md).

> [!NOTE]
> `private protected` Erişim değiştiricisi geçerli sürümde C# 7.2 ve üzeri.

## <a name="example"></a>Örnek

Yalnızca statik değişken türü türetilmiş sınıf türü ise bir taban sınıfın özel ve korumalı bir üye türetilen türler, içeren derlemede erişilebilir. Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:  

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
        BaseClass baseObject = new BaseClass();

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

Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly2.cs`.
İlk dosyayı içeren genel bir temel sınıf `BaseClass`ve bu türden türetilmiş tür `DerivedClass1`. `BaseClass` özel bir korumalı üye sahibi `myValue`, hangi `DerivedClass1` iki yolla erişmeyi dener. Erişmek için yapılan ilk girişim `myValue` örneği üzerinden `BaseClass` hataya neden olur. Ancak, devralınan bir üyesi olarak kullanma girişimi `DerivedClass1` başarılı olur.
İkinci dosyasında, erişme denemesi `myValue` devralınan bir üyesi olarak `DerivedClass2` yalnızca Assembly1 türetilmiş türleri tarafından erişilebilir olduğundan bir hata üretecektir.

Yapı üyeleri olamaz `private protected` struct devraldığından.  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
