---
description: değiştirici-C# başvurusunu geçersiz kıl
title: değiştirici-C# başvurusunu geçersiz kıl
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134466"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override`Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.

## <a name="example"></a>Örnek

Bu örnekte,, `Square` `GetArea` `GetArea` soyut sınıftan devralınmış olduğundan, sınıfının geçersiz kılınan bir uygulamasını sağlaması gerekir `Shape` :

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Bir `override` yöntemi, temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Bir bildirim tarafından geçersiz kılınan yöntem, `override` geçersiz kılınan temel yöntem olarak bilinir. Geçersiz kılınan temel yöntemin, yöntemiyle aynı imzaya sahip olması gerekir `override` . Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).

Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız. Geçersiz kılınan taban yöntemi `virtual` , veya olmalıdır `abstract` `override` .

`override`Bildirim, yönteminin erişilebilirliğini değiştiremez `virtual` . Hem `override` yöntemi hem de `virtual` yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır.

`new` `static` `virtual` Bir yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız `override` .

Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmeli ve geçersiz kılınan özellik `virtual` , `abstract` veya olmalıdır `override` .

Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `override` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Örnek

Bu örnek, adlı bir temel sınıfı `Employee` ve adlı türetilmiş bir sınıfı tanımlar `SalesEmployee` . `SalesEmployee`Sınıfı ek bir alan içerir `salesbonus` ve `CalculatePay` bunu hesaba almak için yöntemi geçersiz kılar.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [Yeni (değiştirici)](new-modifier.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
