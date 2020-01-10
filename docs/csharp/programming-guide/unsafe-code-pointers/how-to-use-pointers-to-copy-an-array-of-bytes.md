---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma- C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698462"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)

Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.

Bu örnek, `Copy` yönteminde işaretçiler kullanmanıza olanak sağlayan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır. [Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır. `fixed` bildiri, kaynak ve hedef dizilerin konumunu çöp toplama tarafından taşınamayacak şekilde *sabitler* . `fixed` bloğu tamamlandığında diziler için bellek blokları sabitlenemez. Bu örnekteki `Copy` yöntemi `unsafe` anahtar sözcüğünü kullandığından, [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.

Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir. `pSource` ve `pTarget` işaretçilerinin bildirimi dizileri sabitler. Bu özellik 7,3 ile C# başlayarak kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [-unsafe (C# derleyici seçenekleri)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)
