---
title: Class anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 506cc3b86961ca22361d37d372bcac9632528cae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602238"
---
# <a name="class-c-reference"></a>class (C# Başvurusu)

Sınıflar, aşağıdaki örnekte gösterildiği gibi `class`anahtar sözcüğü kullanılarak bildirilmiştir:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Açıklamalar

İçinde C#yalnızca tekli devralmaya izin verilir. Diğer bir deyişle, bir sınıf yalnızca bir temel sınıftan uygulamayı devralınabilir. Ancak, bir sınıf birden fazla arabirim uygulayabilir. Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:

|Devralma|Örnek|
|-----------------|-------------|
|Yok.|`class ClassA { }`|
|Tek|`class DerivedClass: BaseClass { }`|
|Hiçbiri, iki arabirim uygular|`class ImplClass: IFace1, IFace2 { }`|
|Tek, bir arabirim uygular|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir. Sınıflar varsayılan `internal` olarak ' dir.

İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir. Üyeler varsayılan `private` olarak ' dir.

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

- [İşleçler](../../programming-guide/statements-expressions-operators/operators.md)

- [Olaylar](../../programming-guide/events/index.md)

- [Temsilciler](../../programming-guide/delegates/index.md)

- [Sınıflar](../../programming-guide/classes-and-structs/classes.md)

- [Arabirimler](../../programming-guide/interfaces/index.md)

- [Yapılar](../../programming-guide/classes-and-structs/structs.md)

- [Sabit Listeleri](../../programming-guide/enumeration-types.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir. Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir. Bu örnekte, iki sınıf bildirilmiştir. İlk sınıf `Child`olan, iki özel alan (`name` ve `age`), iki ortak Oluşturucu ve bir genel yöntem içerir. İkinci sınıfı `StringTest`, öğesini içermesi `Main`için kullanılır.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Açıklamalar

Önceki örnekte özel alanlara (`name` ve `age`) yalnızca `Child` sınıfın genel yöntemiyle erişildiğine dikkat edin. Örneğin, aşağıdaki gibi bir ifade kullanarak alt öğenin adını `Main` yöntemden yazdıramazsınız:

```csharp
Console.Write(child1.name);   // Error
```

' In `Child` `Main` özel üyelerine erişim, yalnızca sınıfının bir üyesi `Main` ise mümkün olacaktır.

Bir erişim değiştiricisi `private`olmayan bir sınıf içinde bildirildiği türler, bu nedenle bu örnekteki veri üyeleri anahtar sözcüğünün kaldırılmakta olması `private` durumunda olmaya devam eder.

Son olarak, parametresiz Oluşturucu (`child3`) kullanılarak oluşturulan nesne için `age` , alanın varsayılan olarak sıfıra başlatıldığını fark edersiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Başvuru Türleri](./reference-types.md)
