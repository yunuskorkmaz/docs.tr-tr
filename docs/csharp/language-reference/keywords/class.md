---
title: class anahtar sözcüğü (C# Başvurusu)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 04e64e825e4297ceb432393c7bd145a6cf4fcb2c
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948517"
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

- [Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)

- [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Olaylar](../../../csharp/programming-guide/events/index.md)

- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)

- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)

- [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek bildiren sınıfı alanları, Oluşturucular ve yöntemleri gösterir. Ayrıca nesne örnek oluşturma ve yazdırma örnek verilerini gösterir. Bu örnekte, iki sınıf bildirilir. İlk sınıf `Child`, iki özel alan içeriyor (`name` ve `age`), iki ortak oluşturucular ve bir genel yöntem. İkinci sınıfı `StringTest`, kapsamak için kullanılmış `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Açıklamalar

Önceki örnekte dikkat özel alanlar (`name` ve `age`) yalnızca genel yöntemi aracılığıyla erişilebilir `Child` sınıfı. Örneğin, çocuğunuzun adı, yazdırma olamaz `Main` yöntemi, böyle bir deyimi kullanarak:

```csharp
Console.Write(child1.name);   // Error
```

Özel üyelerine erişme `Child` gelen `Main` yalnızca sağlayabileceğinizden varsa `Main` sınıf üyesi olan.

Türleri bildirilen bir erişim değiştiricisi varsayılan olmayan bir sınıf içinde `private`, bu örnekte veri üyeleri durumda olacaktır `private` anahtar sözcüğü kaldırılmışsa.

Son olarak, varsayılan oluşturucu kullanılarak oluşturulan nesne için dikkat edin (`child3`), alan başlatılır yaş varsayılan olarak sıfır.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[C# başvurusu](../../../csharp/language-reference/index.md)  
[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
[Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)