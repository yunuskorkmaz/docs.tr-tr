---
title: class (C# Başvurusu)
ms.date: 07/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae4b019ee88b6f331a76c750ab94fc76a3343adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="class-c-reference"></a>class (C# Başvurusu)

Sınıfları, anahtar sözcüğünü kullanarak bildirildiğinde `class`, aşağıdaki örnekte gösterildiği gibi:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a>Açıklamalar
C# içinde yalnızca tek devralma izin verilir. Diğer bir deyişle, bir sınıf bir taban sınıftan yalnızca uygulama devralabilirsiniz. Ancak, bir sınıfın birden fazla arabirimi uygulayabilirsiniz. Aşağıdaki tabloda sınıf devralma ve arabirim uygulamasına örnekleri gösterilmektedir:

|Devralma|Örnek|
|-----------------|-------------|
|Yok.|`class ClassA { }`|
|Tek|`class DerivedClass: BaseClass { }`|
|None, iki arabirimlerini uygular|`class ImplClass: IFace1, IFace2 { }`|
|Tek bir arabirim uygular|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Diğer sınıflar içinde iç içe değil doğrudan bir ad alanındaki bildirme sınıfları olabilir ya da [ortak](../../../csharp/language-reference/keywords/public.md) veya [iç](../../../csharp/language-reference/keywords/internal.md). Sınıflardır `internal` varsayılan olarak.

Sınıf üyeleri, iç içe geçmiş sınıflar dahil olabilir [ortak](../../../csharp/language-reference/keywords/public.md), `protected internal`, [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [özel](../../../csharp/language-reference/keywords/private.md), veya `private protected`. Üye olan [özel](../../../csharp/language-reference/keywords/private.md) varsayılan olarak.

Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).

Tür parametreleri olan genel sınıfları bildirebilirsiniz. Daha fazla bilgi için bkz: [Genel sınıflar](../../../csharp/programming-guide/generics/generic-classes.md).

Bir sınıf bildirimleri aşağıdaki üyeleri içerebilir:

- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [Sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Alanları](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)

- [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Olayları](../../../csharp/programming-guide/events/index.md)

- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)

- [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)

- [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a>Örnek
Aşağıdaki örnek bildiren sınıfı alanları, Oluşturucular ve yöntemleri gösterir. Ayrıca nesne örnek oluşturma ve yazdırma örnek verilerini gösterir. Bu örnekte, iki sınıf bildirilir. İlk sınıf `Child`, iki özel alan içeriyor (`name` ve `age`), iki ortak oluşturucular ve bir genel yöntem. İkinci sınıfı `StringTest`, kapsamak için kullanılmış `Main`.

[!code-csharp[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]

## <a name="comments"></a>Açıklamalar
Önceki örnekte dikkat özel alanlar (`name` ve `age`) yalnızca genel yöntemi aracılığıyla erişilebilir `Child` sınıfı. Örneğin, çocuğunuzun adı, yazdırma olamaz `Main` yöntemi, böyle bir deyimi kullanarak:

```csharp
Console.Write(child1.name);   // Error
```

Özel üyelerine erişme `Child` gelen `Main` yalnızca sağlayabileceğinizden varsa `Main` sınıf üyesi olan.

Türleri bildirilen bir erişim değiştiricisi varsayılan olmayan bir sınıf içinde `private`, bu örnekte veri üyeleri durumda olacaktır `private` anahtar sözcüğü kaldırılmışsa.

Son olarak, varsayılan oluşturucu kullanılarak oluşturulan nesne için dikkat edin (`child3`), alan başlatılır yaş varsayılan olarak sıfır.

## <a name="c-language-specification"></a>C# Dil Belirtimi
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)
