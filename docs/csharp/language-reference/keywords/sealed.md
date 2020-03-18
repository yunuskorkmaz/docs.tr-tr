---
title: mühürlü değiştirici - C# Referans
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713111"
---
# <a name="sealed-c-reference"></a>sealed (C# Başvurusu)

Bir sınıfa uygulandığında, `sealed` değiştirici diğer sınıfların ondan devralmasını engeller. Aşağıdaki örnekte, `B` sınıf sınıftan `A`devralır, ancak hiçbir `B`sınıf sınıftan devralabilir.

```csharp
class A {}
sealed class B : A {}
```

`sealed` Değiştiriciyi, temel sınıftaki sanal bir yöntemi veya özelliği geçersiz kılan bir yöntem veya özellik üzerinde de kullanabilirsiniz. Bu, sınıfların sınıfınızdan türemesine izin vermenize ve belirli sanal yöntemleri veya özellikleri geçersiz kılmalarını önlemenize olanak tanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `Z` `Y` 'de `Z` bildirilen `F` `X` ve mühürlü olan sanal işlevi geçersiz `Y`kılamaz, devralır, ancak

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Bir sınıfta yeni yöntemler veya özellikler tanımladığınızda, türeyen sınıfların [bunları sanal](virtual.md)olarak bildirmeyerek bunları geçersiz kılmasını engelleyebilirsiniz.

[Soyut](abstract.md) bir sınıf soyut yöntemler veya özelliklerin uygulanmasını sağlayan bir sınıf tarafından devralınması gerektiğinden, soyut değiştiricinin mühürlü bir sınıfla kullanılması bir hatadır.

Bir yönteme veya özelliğe `sealed` uygulandığında, değiştirici her zaman [geçersiz kılma](override.md)ile kullanılmalıdır.

Structs örtülü olduğundan, onlar devralınamaz.

Daha fazla bilgi için [Bkz. Kalıtım.](../../programming-guide/classes-and-structs/inheritance.md)

Daha fazla örnek için Bkz. [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

Önceki örnekte, aşağıdaki deyimi kullanarak mühürlü sınıftan devralmayı deneyebilirsiniz:

`class MyDerivedC: SealedClass {}   // Error`

Sonuç bir hata iletisi:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Açıklamalar

Bir sınıfı, yöntemi veya özelliği mühürleyip mühürlemeyeceğinibelirlemek için genellikle aşağıdaki iki noktayı göz önünde bulundurmanız gerekir:

- Sınıfları özelleştirme yeteneği ile elde edebileceği olası faydalar.

- Türeyen sınıfların, sınıflarınızı artık doğru veya beklendiği gibi çalışamayacak şekilde değiştirebilen potansiyel.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Değiştiriciler](index.md)
- [Geçersiz kılma](override.md)
- [virtual](virtual.md)
