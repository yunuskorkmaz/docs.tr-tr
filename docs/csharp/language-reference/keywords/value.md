---
description: value bağlamsal anahtar sözcüğü-C# başvurusu
title: value bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ad2eb6f12d8c295dc5203994d6c570cd2377e3ee
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828922"
---
# <a name="value-c-reference"></a>value (C# Başvurusu)

Bağlamsal anahtar sözcüğü, `value` `set` [özellik](../../programming-guide/classes-and-structs/properties.md) ve [Dizin Oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde erişimcisinde kullanılır. Yöntemin giriş parametresine benzerdir. Sözcük, `value` istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur. Aşağıdaki örnekte, `MyDerivedClass` `Name` `value` yedekleme alanına yeni bir dize atamak için parametresini kullanan adlı bir özelliğe sahiptir `name` . İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Daha fazla bilgi için [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md) makalelerine bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
