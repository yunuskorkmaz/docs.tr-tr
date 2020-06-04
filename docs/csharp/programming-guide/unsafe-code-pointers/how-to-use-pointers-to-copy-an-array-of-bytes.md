---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma-C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397421"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)

Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.

Bu örnek, yönteminde işaretçiler kullanmanıza olanak tanıyan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır `Copy` . [Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır. `fixed`İfade, kaynak ve hedef dizilerinin konumunu çöp toplama tarafından taşınmayacak şekilde *sabitler* . Blok tamamlandığında diziler için bellek blokları `fixed` sabitlenemez. `Copy`Bu örnekteki yöntem `unsafe` anahtar sözcüğünü kullandığından, [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.

Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir. `pSource`Ve `pTarget` işaretçilerinin bildirimi dizileri sabitler. Bu özellik C# 7,3 ile başlayarak kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [-unsafe (C# derleyici seçenekleri)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
