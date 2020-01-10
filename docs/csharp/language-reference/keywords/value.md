---
title: value bağlamsal anahtar sözcüğü C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712903"
---
# <a name="value-c-reference"></a>value (C# Başvurusu)

Bağlamsal anahtar sözcük `value`, [özellik](../../programming-guide/classes-and-structs/properties.md) ve [dizin oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde `set` erişimcisinde kullanılır. Yöntemin giriş parametresine benzerdir. Sözcük `value`, istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur. Aşağıdaki örnekte `MyDerivedClass`, `name`yedekleme alanına yeni bir dize atamak için `value` parametresini kullanan `Name` adlı bir özelliğe sahiptir. İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Indexeres](../../programming-guide/indexers/index.md) makaleleri.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
