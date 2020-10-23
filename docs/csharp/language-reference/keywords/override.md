---
description: değiştirici-C# başvurusunu geçersiz kıl
title: değiştirici-C# başvurusunu geçersiz kıl
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434885"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override`Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.

Aşağıdaki örnekte, `Square` sınıfı `GetArea` `GetArea` soyut sınıftan devralındığından, sınıfının geçersiz kılınan bir uygulamasını sağlaması gerekir `Shape` :

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Bir `override` yöntemi, temel sınıftan devralınan yöntemin yeni bir uygulamasını sağlar. Bir bildirim tarafından geçersiz kılınan yöntem, `override` geçersiz kılınan temel yöntem olarak bilinir. Bir `override` yöntem geçersiz kılınan taban yöntemiyle aynı imzaya sahip olmalıdır. C# 9,0 ' den başlayarak, `override` Yöntemler birlikte değişken dönüş türlerini destekler. Özellikle, bir yöntemin dönüş türü, `override` karşılık gelen temel yöntemin dönüş türünden türetilebilir. C# 8,0 ve önceki sürümlerde, bir `override` yöntemin ve geçersiz kılınan temel yöntemin dönüş türleri aynı olmalıdır.

Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız. Geçersiz kılınan taban yöntemi `virtual` , veya olmalıdır `abstract` `override` .

`override`Bildirim, yönteminin erişilebilirliğini değiştiremez `virtual` . Hem `override` yöntemi hem de `virtual` yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır.

`new` `static` `virtual` Bir yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız `override` .

Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmelidir. C# 9,0 ile başlayarak, salt okuma geçersiz kılma özellikleri birlikte değişken dönüş türlerini destekler. Geçersiz kılınan özellik `virtual` , veya olmalıdır `abstract` `override` .

Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `override` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md). Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).

## <a name="example"></a>Örnek

Bu örnek, adlı bir temel sınıfı `Employee` ve adlı türetilmiş bir sınıfı tanımlar `SalesEmployee` . `SalesEmployee`Sınıfı ek bir alan içerir `salesbonus` ve `CalculatePay` bunu hesaba almak için yöntemi geçersiz kılar.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [geçersiz kılma yöntemleri](~/_csharplang/spec/classes.md#override-methods) bölümüne bakın.

Covaryant dönüş türleri hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [Yeni (değiştirici)](new-modifier.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
