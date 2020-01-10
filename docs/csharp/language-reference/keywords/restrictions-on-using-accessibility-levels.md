---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 90c76e68ca526106f3a8be6e3db2640edbb2bc80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715157"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Erişilebilirlik düzeylerini kullanma kısıtlamaları (C# başvuru)

Bir bildirimde bir tür belirttiğinizde, türün erişilebilirlik düzeyinin bir üyenin ya da başka bir türün erişilebilirlik düzeyine bağımlı olup olmadığını kontrol edin. Örneğin, doğrudan temel sınıfı en azından türetilmiş sınıf olarak erişilebilir olmalıdır. Temel sınıf `BaseClass` `MyClass`daha az erişilebilir olduğu için aşağıdaki bildirimler bir derleyici hatasına neden olur:

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
|[Veri Erişimi](../../programming-guide/classes-and-structs/properties.md)|Özelliğin türü en az özelliğin kendisi olarak erişilebilir olmalıdır.|
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

- [C#Başvurunun](../../language-reference/index.md)
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
