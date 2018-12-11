---
title: 'Nasıl Yapılır: -Bayt dizisine kopyalamak için işaretçiler kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 49151c6d2a573a24e63f733a5279faeee40de1b7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241132"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Nasıl Yapılır: Bir bayt dizisine kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)

Aşağıdaki örnek, bayt bir diziden kopyalamak için işaretçiler kullanır.

Bu örnekte [güvenli olmayan](../../language-reference/keywords/unsafe.md) işaretçiler, kullanmanıza olanak tanıyan anahtar sözcüğü `Copy` yöntemi. [Sabit](../../language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef dizi işaretçileri bildirmek için kullanılır. `fixed` Deyimi *PIN'ler* çöp toplamadan taşınmayacak böylece bellekte konumunu kaynak ve hedef dizi. Bellek bloklarını diziler için ne zaman sabitlenmemiş `fixed` blok tamamlandı. Çünkü `Copy` Bu örnekte kullanmaktadır `unsafe` anahtar sözcüğü, onu derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.

Bu örnekte, ikinci bir yönetilmeyen işaretçi yerine dizinleri hem dizilerin öğelerine erişir. Bildirimi `pSource` ve `pTarget` işaretçileri, dizileri sabitler. Bu özellik, C# 7.3 ile başlayan kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../index.md)  
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)  
- [-unsafe (C# Derleyici Seçenekleri)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [Atık Toplama](../../../standard/garbage-collection/index.md)  
