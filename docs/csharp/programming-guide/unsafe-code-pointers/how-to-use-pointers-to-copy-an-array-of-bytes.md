---
title: Bayt dizisi kopyalamak için işaretçiler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698462"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Bir dizi bayt kopyalamak için işaretçiler nasıl kullanılır (C# Programlama Kılavuzu)

Aşağıdaki örnek, bir diziden diğerine bayt kopyalamak için işaretçiler kullanır.

Bu örnek, [unsafe](../../language-reference/keywords/unsafe.md) `Copy` yöntemde işaretçileri kullanmanıza olanak tanıyan güvenli olmayan anahtar sözcüğü kullanır. [Sabit](../../language-reference/keywords/fixed-statement.md) deyim, işaretçileri kaynak ve hedef dizilerine bildirmek için kullanılır. İfade, `fixed` kaynak ve hedef dizilerinin konumunu bellekte *sabitler,* böylece çöp toplama tarafından taşınmaz. `fixed` Blok tamamlandığında dizilerin bellek blokları sabitlenmez. Bu `Copy` örnekteki yöntem anahtar `unsafe` sözcüğü kullandığından, [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmiş olması gerekir.

Bu örnek, ikinci bir yönetilmeyen işaretçi yerine endeksleri kullanarak her iki dizinin öğelerine erişer. Ve `pSource` `pTarget` işaretçilerin bildirimi dizileri sabitler. Bu özellik C# 7.3 ile başlayarak kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [-güvenli değil (C# Derleyici Seçenekleri)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Çöp Toplama](../../../standard/garbage-collection/index.md)
