---
title: sınıf anahtar kelime - C# Referans
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673101"
---
# <a name="class-c-reference"></a>class (C# Başvurusu)

Sınıflar, aşağıdaki örnekte `class`gösterildiği gibi anahtar kelime kullanılarak bildirilir:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Açıklamalar

C#'da yalnızca tek bir devralmaya izin verilir. Başka bir deyişle, bir sınıf yalnızca bir taban sınıftan uygulama devralabilir. Ancak, bir sınıf birden fazla arabirim uygulayabilir. Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:

|Devralma|Örnek|
|-----------------|-------------|
|None|`class ClassA { }`|
|Tek|`class DerivedClass : BaseClass { }`|
|Yok, iki arabirim uygular|`class ImplClass : IFace1, IFace2 { }`|
|Tek, bir arayüz uygular|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Diğer sınıflar içinde iç içe olmayan, doğrudan bir ad alanı içinde beyan ettiğiniz [sınıflar, genel](./public.md) veya [dahili](./internal.md)olabilir. Sınıflar `internal` varsayılan olarak vardır.

İç içe sınıflar da dahil olmak üzere sınıf [üyeleri, kamu,](public.md) [korunan iç,](protected-internal.md) [korumalı,](protected.md) [iç,](internal.md) [özel](private.md)veya [özel korumalı](private-protected.md)olabilir. Üyeler `private` varsayılan olarak vardır.

Daha fazla bilgi için [Erişim Değiştiriciler'e](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.

Tür parametreleri olan genel sınıfları bildirebilirsiniz. Daha fazla bilgi için [Genel Sınıflar'a](../../programming-guide/generics/generic-classes.md)bakın.

Bir sınıf aşağıdaki üyelerin bildirimlerini içerebilir:

- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)

- [Sabitler](../../programming-guide/classes-and-structs/constants.md)

- [Alanlar](../../programming-guide/classes-and-structs/fields.md)

- [Sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md)

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

- [Özellikler](../../programming-guide/classes-and-structs/properties.md)

- [Dizin Oluşturucular](../../programming-guide/indexers/index.md)

- [İşleçler](../operators/index.md)

- [Olaylar](../../programming-guide/events/index.md)

- [Temsilciler](../../programming-guide/delegates/index.md)

- [Sınıflar](../../programming-guide/classes-and-structs/classes.md)

- [Arabirimler](../../programming-guide/interfaces/index.md)

- [Yapı türleri](../builtin-types/struct.md)

- [Numaralandırma türleri](../builtin-types/enum.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, sınıf alanlarını, oluşturucuları ve yöntemleri bildireni gösterir. Ayrıca nesne anlık ve yazdırma örneği verilerini de gösterir. Bu örnekte, iki sınıf bildirilir. Birinci sınıf, `Child`iki özel alan`name` `age`(ve), iki kamu yapıcılar ve bir ortak yöntem içerir. İkinci sınıf, `StringTest`, içerdiği `Main`için kullanılır.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Yorumlar

Önceki örnekte özel alanlara`name` (ve) `age`yalnızca `Child` sınıfın ortak yöntemiyle erişilenebildiğine dikkat edin. Örneğin, aşağıdaki gibi bir ifade kullanarak `Main` yöntemden çocuğun adını yazdıramazsınız:

```csharp
Console.Write(child1.name);   // Error
```

Özel `Child` üyelere `Main` yalnızca sınıfın bir `Main` üyesi olsaydı erişmek mümkündür.

Erişim değiştiricisi varsayılan olarak bir sınıf `private`içinde bildirilen türler , bu `private` nedenle bu örnekteki veri üyeleri anahtar sözcük kaldırılırsa yine de olacaktır.

Son olarak, parametresiz oluşturucu kullanılarak oluşturulan`child3`nesne `age` için alanın varsayılan olarak sıfıra başlandığını unutmayın.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Referans Türleri](./reference-types.md)
