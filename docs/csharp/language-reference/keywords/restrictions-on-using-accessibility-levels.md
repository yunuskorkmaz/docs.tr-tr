---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları - C# Reference
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173542"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Erişilebilirlik düzeylerinin kullanımına ilişkin kısıtlamalar (C# Reference)

Bir bildirimde bir tür belirttiğiniz zaman, türün erişilebilirlik düzeyinin bir üyenin veya başka bir türün erişilebilirlik düzeyine bağlı olup olmadığını denetleyin. Örneğin, doğrudan taban sınıf en az türemiş sınıf kadar erişilebilir olmalıdır. Taban sınıf `BaseClass` aşağıdakilerden daha az erişilebilir olduğundan derleyici `MyClass`hatasına neden olur:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Aşağıdaki tablo, bildirilen erişilebilirlik düzeylerine ilişkin kısıtlamaları özetleyin.

|Bağlam|Açıklamalar|
|-------------|-------------|
|[Sınıflar](../../programming-guide/classes-and-structs/classes.md)|Bir sınıf türünün doğrudan taban sınıfı en az sınıf türü kadar erişilebilir olmalıdır.|
|[Arabirimler](../../programming-guide/interfaces/index.md)|Arabirim türünün açık temel arabirimleri en az arabirim türü kadar erişilebilir olmalıdır.|
|[Temsilciler](../../programming-guide/delegates/index.md)|Temsilci türünün dönüş türü ve parametre türleri en az temsilci türü kadar erişilebilir olmalıdır.|
|[Sabitler](../../programming-guide/classes-and-structs/constants.md)|Sabitin türü en az sabitin kendisi kadar erişilebilir olmalıdır.|
|[Alanlar](../../programming-guide/classes-and-structs/fields.md)|Bir alanın türü en az alanın kendisi kadar erişilebilir olmalıdır.|
|[Yöntemler](../../programming-guide/classes-and-structs/methods.md)|Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi kadar erişilebilir olmalıdır.|
|[Özellikler](../../programming-guide/classes-and-structs/properties.md)|Bir özelliğin türü en az özelliğin kendisi kadar erişilebilir olmalıdır.|
|[Olaylar](../../programming-guide/events/index.md)|Bir olayın türü en az olayın kendisi kadar erişilebilir olmalıdır.|
|[Dizin Oluşturucular](../../programming-guide/indexers/index.md)|Dizinleyicinin türü ve parametre türleri en az dizinleyicinin kendisi kadar erişilebilir olmalıdır.|
|[İşleçler](../operators/index.md)|Bir işleçin dönüş türü ve parametre türleri en az operatörün kendisi kadar erişilebilir olmalıdır.|
|[Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)|Bir oluşturucuparametre türleri en az yapıcının kendisi kadar erişilebilir olmalıdır.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, farklı türde hatalı bildirimleri içerir. Her bildirimi izleyen açıklama beklenen derleyici hatasını gösterir.

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

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](../../language-reference/keywords/index.md)
- [Erişim Değiştiricileri](../../language-reference/keywords/access-modifiers.md)
- [Erişilebilirlik Etki Alanı](../../language-reference/keywords/accessibility-domain.md)
- [Erişilebilirlik Düzeyleri](../../language-reference/keywords/accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Kamu](../../language-reference/keywords/public.md)
- [Özel](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [Iç](../../language-reference/keywords/internal.md)
