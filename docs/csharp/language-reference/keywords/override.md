---
title: değiştirici geçersiz kılma - C# Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713254"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override` Değiştirici, devralınan bir yöntemin, özelliğin, dizinleyicinin veya olayın soyut veya sanal uygulamasını genişletmek veya değiştirmek için gereklidir.

## <a name="example"></a>Örnek

Bu örnekte, `Square` sınıf soyut `GetArea` `GetArea` `Shape` sınıftan devralınan çünkü geçersiz bir uygulama sağlamalıdır:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Yöntem, `override` taban sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Bir `override` bildirim tarafından geçersiz kılınan yöntem, geçersiz kılınan temel yöntem olarak bilinir. Geçersiz kılınan temel yöntem, yöntemle `override` aynı imzaya sahip olmalıdır. Devralma hakkında bilgi için [bkz.](../../programming-guide/classes-and-structs/inheritance.md)

Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız. Geçersiz kılınan baz yöntemi `virtual` `abstract`, `override`veya .

Bir `override` bildirim `virtual` yöntemin erişilebilirliğini değiştiremez. Hem `override` yöntem hem `virtual` de yöntem aynı [erişim düzeyi değiştirici](access-modifiers.md)olmalıdır.

Bir `override` yöntemi `new`değiştirmek `static`için `virtual` , veya değiştiriciler kullanamazsınız.

Geçersiz kılınan bir özellik bildirimi, devralınan özellikle tam olarak aynı erişim değiştiricisini, türünü `virtual`ve `abstract`adını `override`belirtmelidir ve geçersiz kılınan özellik , yani .

Anahtar kelimenin `override` nasıl kullanılacağı hakkında daha fazla bilgi için, [Geçersiz Kılma ve Yeni Anahtar Kelimelerle Sürüm](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) leme ve Geçersiz Kılma ve Yeni Anahtar [Kelimeleri'nin ne zaman kullanılacağını bilmek](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)için bkz.

## <a name="example"></a>Örnek

Bu örnek, adlı `Employee`bir taban sınıf ve `SalesEmployee`türetilmiş bir sınıf tanımlanır. Sınıf `SalesEmployee` fazladan bir alan `salesbonus`içerir ve bunu `CalculatePay` dikkate almak için yöntemi geçersiz kılar.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
- [Soyut](abstract.md)
- [virtual](virtual.md)
- [yeni (değiştirici)](new-modifier.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
