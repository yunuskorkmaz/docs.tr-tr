---
title: (C# Başvurusu) erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 2bcf2b12d1aa1488e6d3e46f5b37ac9535b138dd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389357"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>(C# Başvurusu) erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar

Bir bildirim türü belirttiğinizde, türün erişilebilirlik düzeyi erişilebilirlik düzeyine üyesi veya başka bir türe bağımlı olup olmadığını denetleyin. Örneğin, doğrudan temel sınıf en az türetilen sınıf olarak olarak erişilebilir olması gerekir. Aşağıdaki bildirimleri için bir derleyici hatasına neden temel sınıf `BaseClass` daha az erişilebilir `MyClass`:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Bildirilen erişilebilirlik düzeyi kısıtlamaları aşağıdaki tabloda özetlenmiştir.

|Bağlam|Açıklamalar|
|-------------|-------------|
|[Sınıflar](../../programming-guide/classes-and-structs/classes.md)|Bir sınıf türünün doğrudan temel sınıf en az sınıf türü kendisini olarak erişilebilir olması gerekir.|
|[Arabirimler](../../programming-guide/interfaces/index.md)|Açık bir arabirim türü temel arabirimleri en az arabirim türü kendisini olarak erişilebilir olması gerekir.|
|[Temsilciler](../../programming-guide/delegates/index.md)|Bir temsilci türü parametre türleri ve dönüş türü, en az temsilci türü kendisini olarak erişilebilir olması gerekir.|
|[Sabitler](../../programming-guide/classes-and-structs/constants.md)|Bir sabit değer türü en az sabit olarak olarak erişilebilir olması gerekir.|
|[Alanlar](../../programming-guide/classes-and-structs/fields.md)|Bir alan türü en az alan olarak olarak erişilebilir olması gerekir.|
|[Yöntemler](../../programming-guide/classes-and-structs/methods.md)|Bir yöntemin parametre türleri ve dönüş türü, en az yöntemi olarak olarak erişilebilir olması gerekir.|
|[Özellikler](../../programming-guide/classes-and-structs/properties.md)|Bir özelliğin türünü en az özelliği olarak olarak erişilebilir olması gerekir.|
|[Olaylar](../../programming-guide/events/index.md)|Bir olay türü en az olay olarak olarak erişilebilir olması gerekir.|
|[Dizin Oluşturucular](../../programming-guide/indexers/index.md)|Bir dizin oluşturucu türü ve parametre türleri, en az Indexer olarak erişilebilir olması gerekir.|
|[İşleçler](../../programming-guide/statements-expressions-operators/operators.md)|Operatör için parametre türleri ve dönüş türü, en azından operatör olarak olarak erişilebilir olması gerekir.|
|[Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)|Parametre türleri bir oluşturucunun en az Oluşturucu olarak olarak erişilebilir olması gerekir.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, farklı türlerdeki hatalı bildirimi içerir. Her bildiriminin açıklama beklenen derleyici hata olduğunu gösterir.

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

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../language-reference/keywords/index.md)
- [Erişim Değiştiricileri](../../language-reference/keywords/access-modifiers.md)
- [Erişilebilirlik Etki Alanı](../../language-reference/keywords/accessibility-domain.md)
- [Erişilebilirlik Düzeyleri](../../language-reference/keywords/accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../language-reference/keywords/public.md)
- [private](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)