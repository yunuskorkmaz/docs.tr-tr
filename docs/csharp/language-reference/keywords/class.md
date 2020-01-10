---
title: Class anahtar sözcüğü C# başvurusu
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 187a49131e903e00cab54d9db43b6cd8eb359a3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713685"
---
# <a name="class-c-reference"></a>class (C# Başvurusu)

Sınıflar, aşağıdaki örnekte gösterildiği gibi anahtar sözcük `class`kullanılarak bildirilmiştir:

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

Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir. Sınıflar varsayılan olarak `internal`.

İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir. Üyeler varsayılan olarak `private`.

Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

Tür parametrelerine sahip genel sınıfları bildirebilirsiniz. Daha fazla bilgi için bkz. [genel sınıflar](../../programming-guide/generics/generic-classes.md).

Bir sınıf, aşağıdaki üyelerin bildirimlerini içerebilir:

- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)

- [Sabitler](../../programming-guide/classes-and-structs/constants.md)

- [Alanlar](../../programming-guide/classes-and-structs/fields.md)

- [Sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md)

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

- [Veri Erişimi](../../programming-guide/classes-and-structs/properties.md)

- [Dizin Oluşturucular](../../programming-guide/indexers/index.md)

- [İşleçler](../operators/index.md)

- [Olaylar](../../programming-guide/events/index.md)

- [Temsilciler](../../programming-guide/delegates/index.md)

- [Sınıflar](../../programming-guide/classes-and-structs/classes.md)

- [Arabirimler](../../programming-guide/interfaces/index.md)

- [Yapılar](../../programming-guide/classes-and-structs/structs.md)

- [Sabit Listeleri](../builtin-types/enum.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir. Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir. Bu örnekte, iki sınıf bildirilmiştir. İlk sınıf `Child`, iki özel alan (`name` ve `age`), iki ortak Oluşturucu ve bir genel yöntem içerir. İkinci sınıf, `StringTest`, `Main`içermesi için kullanılır.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Açıklamalar

Önceki örnekte özel alanlara (`name` ve `age`) yalnızca `Child` sınıfının public yöntemi aracılığıyla erişildiğine dikkat edin. Örneğin, aşağıdaki gibi bir ifade kullanarak, çocuğun adını `Main` yönteminden yazdıramıyorsunuz:

```csharp
Console.Write(child1.name);   // Error
```

`Main` `Child` özel üyelerine erişmek, yalnızca `Main` sınıfının bir üyesi olması durumunda olabilir.

Bir erişim değiştiricisi olmayan bir sınıf içinde belirtilen türler `private`için varsayılan olarak, bu örnekteki veri üyeleri anahtar sözcük kaldırılırsa `private` olmaya devam eder.

Son olarak, parametresiz Oluşturucu (`child3`) kullanılarak oluşturulan nesne için, `age` alanın varsayılan olarak sıfırdan başlatıldığını görürsünüz.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Başvuru Türleri](./reference-types.md)
