---
title: Değiştirici - korumalı C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: babad3b07c5faea1381e6af13d3c713122de2332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660768"
---
# <a name="sealed-c-reference"></a>sealed (C# Başvurusu)

Bir sınıfa uygulandığında `sealed` değiştiricisi kullananların devralmasını diğer sınıflar engeller. Aşağıdaki örnekte, sınıf `B` sınıfından devralan `A`, ancak hiçbir sınıf sınıfı devralabilirsiniz `B`.

```csharp
class A {}
sealed class B : A {}
```

Ayrıca `sealed` bir yöntem veya sanal bir yöntemi geçersiz kılan özellik veya bir temel sınıf özelliği değiştiricisi. Bu izin, sınıfından türetilir ve bunları belirli sanal yöntemleri veya özellikleri geçersiz kılmasını önlemek için sınıflar sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `Z` devraldığı `Y` ancak `Z` sanal işlevini geçersiz kılamaz `F` dosyasında bildirilen `X` hem de korumalı `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Bir sınıfta yeni yöntemleri veya özellikleri tanımladığınızda, türetilen sınıflar olarak bildirerek değil önlemiş engelleyebilir [sanal](virtual.md).

Kullanılacak bir hata olduğunu [soyut](abstract.md) değiştiricisi kapalı bir sınıf ile soyut bir sınıf soyut yöntemleri veya özellikleri uygulaması sağlayan bir sınıf tarafından devralınan gerekir çünkü.

Bir yöntemi veya özelliği uygulandığında `sealed` değiştiricisi her zaman kullanılması gerektiğini ile [geçersiz kılma](override.md).

Yapılardan türetme çünkü bunlar devralınamaz.

Daha fazla bilgi için [devralma](../../programming-guide/classes-and-structs/inheritance.md).

Daha fazla örnek için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

Önceki örnekte, aşağıdaki deyimi kullanarak korumalı sınıfından devralmak deneyebilirsiniz:

`class MyDerivedC: SealedClass {}   // Error`

Sonucu bir hata iletisi oluşturulur.

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a>Açıklamalar

Bir sınıf, yöntem veya özellik mühürlenecek belirlemek için genellikle iki aşağıdaki noktaları dikkate almanız gerekir:

- Olası faydaları sınıflardan türetme sınıfınıza özelleştirme olanağı elde edebilir.

- Olası sınıflardan türetme gibi sınıflarınızdaki değiştirebilir, bunlar artık doğru şekilde çalışması veya olarak bir yöntem bekleniyor.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Değiştiriciler](modifiers.md)
- [override](override.md)
- [virtual](virtual.md)