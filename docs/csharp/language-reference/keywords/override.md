---
title: geçersiz kılma değiştiricisi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: cbd5e21e7ca71a4986099a0386c684a6db37c3e8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591179"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)

`override` Değiştiricisi, genişletme veya soyut ya da sanal uygulaması devralınan yöntemi, özelliği, dizin oluşturucusu veya olayı değiştirmek için gereklidir.

## <a name="example"></a>Örnek

Bu örnekte, `Square` sınıfı, geçersiz kılınan bir uygulamasını sağlaması gerektiği `Area` çünkü `Area` Özet devralınan `ShapesClass`:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Bir `override` yöntemi, bir temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Yöntemi tarafından geçersiz kılınan bir `override` bildirimi geçersiz kılınan taban yöntemi bilinir. Geçersiz kılınan taban yöntemi olarak aynı imzaya sahip olmalıdır `override` yöntemi. Devralma hakkında daha fazla bilgi için bkz: [devralma](../../programming-guide/classes-and-structs/inheritance.md).

Sanal olmayan veya statik bir yöntemi geçersiz kılınamıyor. Geçersiz kılınan taban yöntemi olmalıdır `virtual`, `abstract`, veya `override`.

Bir `override` bildirimi erişilebilirliğini değiştiremez `virtual` yöntemi. Her iki `override` yöntemi ve `virtual` yöntemi aynı olmalıdır [erişim düzeyi değiştiricisi](access-modifiers.md).

Kullanamazsınız `new`, `static`, veya `virtual` değiştirmek için değiştiriciler bir `override` yöntemi.

Devralınan özellik olarak geçersiz kılan bir özellik bildirimi tam olarak aynı erişim değiştiricisi, türü ve adı belirtmeniz gerekir ve geçersiz kılınan özelliğin olmalıdır `virtual`, `abstract`, veya `override`.

Nasıl kullanılacağı hakkında daha fazla bilgi için `override` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Örnek

Bu örnek adlı bir temel sınıf tanımlar `Employee`ve adlı bir türetilmiş sınıf `SalesEmployee`. `SalesEmployee` Sınıfı içeren ek bir alan `salesbonus`ve metot geçersiz kılmaları `CalculatePay` hesaba katması için.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Devralma](../../programming-guide/classes-and-structs/inheritance.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](modifiers.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [new](new.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
