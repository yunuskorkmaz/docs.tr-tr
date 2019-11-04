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
ms.openlocfilehash: 699887d635ab074fc9ffa4cd7fa354372eb82f25
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422629"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override` değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.

## <a name="example"></a>Örnek

Bu örnekte `Square` sınıfı, `GetArea` soyut `Shape` sınıfından devralındığından, geçersiz kılınan bir `GetArea` uygulamasını sağlamalıdır:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` yöntemi, temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Bir `override` bildirimi tarafından geçersiz kılınan yöntem, geçersiz kılınan temel yöntem olarak bilinir. Geçersiz kılınan temel yöntemin `override` yöntemiyle aynı imzaya sahip olması gerekir. Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).

Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız. Geçersiz kılınan taban yöntemi `virtual`, `abstract`veya `override`olmalıdır.

`override` bildirimi `virtual` yönteminin erişilebilirliğini değiştiremiyor. Hem `override` yöntemi hem de `virtual` yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır.

`override` bir yöntemi değiştirmek için `new`, `static`veya `virtual` değiştiricilerini kullanamazsınız.

Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmeli ve geçersiz kılınan Özellik `virtual`, `abstract`veya `override`olmalıdır.

`override` anahtar sözcüğünü kullanma hakkında daha fazla bilgi için bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Örnek

Bu örnek, `Employee`adlı bir temel sınıfı ve `SalesEmployee`adlı türetilmiş bir sınıfı tanımlar. `SalesEmployee` sınıfı ek bir alan içerir, `salesbonus`ve bunu hesaba almak için `CalculatePay` yöntemi geçersiz kılar.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [Yeni (değiştirici)](new-modifier.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
