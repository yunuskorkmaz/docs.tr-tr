---
description: Class anahtar sözcüğü-C# başvurusu
title: Class anahtar sözcüğü-C# başvurusu
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142121"
---
# <a name="class-c-reference"></a>class (C# Başvurusu)

Sınıflar `class` , aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü kullanılarak bildirilmiştir:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Açıklamalar

C# içinde yalnızca tek devralmaya izin verilir. Diğer bir deyişle, bir sınıf yalnızca bir temel sınıftan uygulamayı devralınabilir. Ancak, bir sınıf birden fazla arabirim uygulayabilir. Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:

|Devralma|Örnek|
|-----------------|-------------|
|Yok|`class ClassA { }`|
|Tek|`class DerivedClass : BaseClass { }`|
|Hiçbiri, iki arabirim uygular|`class ImplClass : IFace1, IFace2 { }`|
|Tek, bir arabirim uygular|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir. Sınıflar `internal` Varsayılan olarak ' dir.

İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir. Üyeler `private` Varsayılan olarak ' dir.

Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

Tür parametrelerine sahip genel sınıfları bildirebilirsiniz. Daha fazla bilgi için bkz. [genel sınıflar](../../programming-guide/generics/generic-classes.md).

Bir sınıf, aşağıdaki üyelerin bildirimlerini içerebilir:

- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)

- [Sabitler](../../programming-guide/classes-and-structs/constants.md)

- [Alanlar](../../programming-guide/classes-and-structs/fields.md)

- [Sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md)

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

- [Özellikler](../../programming-guide/classes-and-structs/properties.md)

- [Dizin Oluşturucular](../../programming-guide/indexers/index.md)

- [İşleçler](../operators/index.md)

- [Ekinlikler](../../programming-guide/events/index.md)

- [Temsilciler](../../programming-guide/delegates/index.md)

- [Sınıflar](../../programming-guide/classes-and-structs/classes.md)

- [Arabirimler](../../programming-guide/interfaces/index.md)

- [Yapı türleri](../builtin-types/struct.md)

- [Numaralandırma türleri](../builtin-types/enum.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir. Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir. Bu örnekte, iki sınıf bildirilmiştir. İlk sınıf olan, `Child` iki özel alan ( `name` ve `age` ), iki ortak Oluşturucu ve bir genel yöntem içerir. İkinci sınıfı, `StringTest` öğesini içermesi için kullanılır `Main` .

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Yorumlar

Önceki örnekte özel alanlara ( `name` ve `age` ) yalnızca sınıfın genel yöntemiyle erişildiğine dikkat edin `Child` . Örneğin, `Main` aşağıdaki gibi bir ifade kullanarak alt öğenin adını yöntemden yazdıramazsınız:

```csharp
Console.Write(child1.name);   // Error
```

' In özel üyelerine erişim, `Child` `Main` yalnızca `Main` sınıfının bir üyesi ise mümkün olacaktır.

Bir erişim değiştiricisi olmayan bir sınıf içinde bildirildiği türler `private` , bu nedenle bu örnekteki veri üyeleri `private` anahtar sözcüğünün kaldırılmakta olması durumunda olmaya devam eder.

Son olarak, parametresiz Oluşturucu () kullanılarak oluşturulan nesne için `child3` , `age` alanın varsayılan olarak sıfıra başlatıldığını fark edersiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Başvuru türleri](./reference-types.md)
