---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma-C# Programlama Kılavuzu
description: Bir bayt dizisini kopyalamak için işaretçileri nasıl kullanacağınızı öğrenin. Bir kod örneğine ve kullanılabilir ek kaynaklara bakın.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: f0122d29729ac8ad634f39f0643902e9bb78a8a5
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478612"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)

Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.

Bu örnek, yönteminde işaretçiler kullanmanıza olanak tanıyan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır `Copy` . [Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır. `fixed`İfade, kaynak ve hedef dizilerinin konumunu çöp toplama tarafından taşınmayacak şekilde *sabitler* . Blok tamamlandığında diziler için bellek blokları `fixed` sabitlenemez. `Copy`Bu örnekteki yöntem `unsafe` anahtar sözcüğünü kullandığından, [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks) derleyici seçeneğiyle derlenmesi gerekir.

Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir. `pSource`Ve `pTarget` işaretçilerinin bildirimi dizileri sabitler. Bu özellik C# 7,3 ile başlayarak kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [**AllowUnsafeBlocks** (C# derleyici seçenekleri)](../../language-reference/compiler-options/language.md#allowunsafeblocks)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
