---
title: değiştirici C# başvurusunu geçersiz kıl
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: bbdbcaf466e0b4dca4b78902ca9e7a49b02ac718
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394231"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override` Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.

## <a name="example"></a>Örnek

Bu örnekte,, soyut `Square` `GetArea` `GetArea` sınıftandevralınmışolduğundan,sınıfınıngeçersizkılınanbir`Shape` uygulamasını sağlaması gerekir:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Bir `override` yöntemi, temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Bir `override` bildirim tarafından geçersiz kılınan yöntem, geçersiz kılınan temel yöntem olarak bilinir. Geçersiz kılınan temel yöntemin, `override` yöntemiyle aynı imzaya sahip olması gerekir. Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).

Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız. Geçersiz kılınan taban yöntemi `virtual`, `abstract`veya `override`olmalıdır.

Bildirim, `virtual` yönteminin erişilebilirliğini değiştiremez. `override` Hem yöntemi hem de yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır. `virtual` `override`

Bir `new` `static` `virtual` yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız. `override`

Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmeli ve geçersiz kılınan özellik `virtual`, `abstract`veya `override`olmalıdır.

`override` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için, bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Örnek

Bu örnek `Employee`, adlı bir temel sınıfı ve adlı `SalesEmployee`türetilmiş bir sınıfı tanımlar. Sınıfı ek bir `salesbonus`alan içerir ve bunu hesaba almak için yöntemi `CalculatePay` geçersiz kılar. `SalesEmployee`

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](modifiers.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [Yeni (değiştirici)](new-modifier.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
