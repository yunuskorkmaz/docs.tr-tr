---
title: 'Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748109"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)

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
