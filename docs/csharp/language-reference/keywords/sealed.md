---
description: Sealed değiştirici-C# başvurusu
title: Sealed değiştirici-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 5b945503c6f6546f571a2422ae77760da0363b08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136974"
---
# <a name="sealed-c-reference"></a>sealed (C# Başvurusu)

Bir sınıfa uygulandığında, `sealed` değiştirici diğer sınıfların bundan devralmasını önler. Aşağıdaki örnekte sınıf sınıfından `B` devralınır `A` , ancak sınıfından hiçbir sınıf devralamıyor `B` .

```csharp
class A {}
sealed class B : A {}
```

Değiştirici, bir `sealed` temel sınıftaki sanal bir yöntemi veya özelliği geçersiz kılan bir yöntem veya özellik üzerinde de kullanabilirsiniz. Bu, sınıfların sınıfınızdan türetmesine izin verir ve belirli sanal yöntemlerin veya özelliklerin geçersiz kılınmasını önler.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ' `Z` den devralır, `Y` ancak içinde `Z` `F` ve korumalı olarak belirtilen sanal işlevi geçersiz kılamazsınız `X` `Y` .

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Bir sınıfta yeni yöntemler veya özellikler tanımladığınızda, türetilen sınıfların bunları [sanal](virtual.md)olarak bildirmeyerek geçersiz kılmasını engelleyebilirsiniz.

Soyut bir sınıf, soyut yöntemlerin veya özelliklerin bir uygulamasını sağlayan bir sınıf tarafından devralınamadığı için Sealed bir sınıf ile [soyut](abstract.md) değiştiricinin kullanılması hatadır.

Bir yönteme veya özelliğe uygulandığında, `sealed` değiştiricinin her zaman [geçersiz kılma](override.md)ile kullanılması gerekir.

Yapılar örtük olarak mühürlenmediğinden devralınamaz.

Daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).

Daha fazla örnek için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

Önceki örnekte, aşağıdaki ifadeyi kullanarak Sealed sınıfından devralmayı deneyebilirsiniz:

`class MyDerivedC: SealedClass {}   // Error`

Sonuç bir hata iletisidir:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Açıklamalar

Bir sınıfın, yöntemin veya özelliğin mühürlendirilip zorlanmayacağını anlamak için genellikle aşağıdaki iki noktayı dikkate almalısınız:

- Sınıfların türetireceği olası avantajlar, sınıfınızı özelleştirme özelliği aracılığıyla elde edebilir.

- Sınıfları Türetmenin olasılığı, sınıflarınızı daha sonra düzgün şekilde veya beklendiği gibi çalışmayacak şekilde değiştirebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Değiştiriciler](index.md)
- [override](override.md)
- [virtual](virtual.md)
