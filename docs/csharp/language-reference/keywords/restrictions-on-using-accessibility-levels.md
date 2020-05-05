---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 8082dbd7398b6634b68f1dd2887cd55d6798a5d9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795163"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Erişilebilirlik düzeylerini kullanma kısıtlamaları (C# Başvurusu)

Bir bildirimde bir tür belirttiğinizde, türün erişilebilirlik düzeyinin bir üyenin ya da başka bir türün erişilebilirlik düzeyine bağımlı olup olmadığını kontrol edin. Örneğin, doğrudan temel sınıfı en azından türetilmiş sınıf olarak erişilebilir olmalıdır. Aşağıdaki bildirimler bir derleyici hatasına neden olur çünkü temel sınıf `BaseClass` şundan `MyClass`daha az erişilebilir:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Aşağıdaki tablo, belirtilen erişilebilirlik düzeyleri üzerindeki kısıtlamaları özetler.

|Bağlam|Açıklamalar|
|-------------|-------------|
|[Sınıflar](../../programming-guide/classes-and-structs/classes.md)|Bir sınıf türünün doğrudan temel sınıfı en azından sınıf türünün kendisi kadar erişilebilir olmalıdır.|
|[Arabirimler](../../programming-guide/interfaces/index.md)|Arabirim türünün açık temel arabirimleri en az arabirim türünün kendisi kadar erişilebilir olmalıdır.|
|[Temsilciler](../../programming-guide/delegates/index.md)|Bir temsilci türünün dönüş türü ve parametre türleri en azından temsilci türünün kendisi kadar erişilebilir olmalıdır.|
|[Sabitler](../../programming-guide/classes-and-structs/constants.md)|Bir sabit türü en az sabit değer olarak erişilebilir olmalıdır.|
|[Alanlar](../../programming-guide/classes-and-structs/fields.md)|Alanın türü en azından alanın kendisi kadar erişilebilir olmalıdır.|
|[Yöntemler](../../programming-guide/classes-and-structs/methods.md)|Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi olarak erişilebilir olmalıdır.|
|[Özellikler](../../programming-guide/classes-and-structs/properties.md)|Özelliğin türü en az özelliğin kendisi olarak erişilebilir olmalıdır.|
|[Olaylar](../../programming-guide/events/index.md)|Bir olayın türü en az olayın kendisi olarak erişilebilir olmalıdır.|
|[Dizin Oluşturucular](../../programming-guide/indexers/index.md)|Bir dizin oluşturucunun türü ve parametre türleri en azından dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.|
|[İşleçler](../operators/index.md)|Bir işlecin dönüş türü ve parametre türleri en az işlecin kendisi olarak erişilebilir olmalıdır.|
|[Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)|Bir oluşturucunun parametre türleri en az oluşturucunun kendisi olarak erişilebilir olmalıdır.|

## <a name="example"></a>Örnek

Aşağıdaki örnek farklı türlerin hatalı bildirimlerini içerir. Her bildirimi izleyen yorum, beklenen derleyici hatasını gösterir.

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Etki Alanı](accessibility-domain.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](public.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
