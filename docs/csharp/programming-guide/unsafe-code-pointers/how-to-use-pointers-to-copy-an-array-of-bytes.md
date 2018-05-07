---
title: 'Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 800a600f0fa7ca52d0433c8d90039434bf6b7f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)

Aşağıdaki örnek, bir diziden bayt kopyalamak için işaretçiler kullanır.

Bu örnekte [güvensiz](../../language-reference/keywords/unsafe.md) içinde işaretçileri kullanmanıza olanak tanır anahtar sözcüğü `Copy` yöntemi. [Sabit](../../language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef diziler işaretçiler bildirmek için kullanılır. `fixed` Deyimi *PIN'ler* kaynak ve hedef konumu, böylece atık toplama tarafından taşınmayacak bellekte dizi. Bellek blokları dizileri ne zaman sabitlenmemiş `fixed` blok tamamlandı. Çünkü `Copy` Bu örnekte bir yöntem `unsafe` anahtar sözcüğü, onu derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.

Bu örnekte, ikinci bir yönetilmeyen işaretçi yerine dizinlerini her iki dizi öğeleri erişir. Bildirimi `pSource` ve `pTarget` işaretçileri sabitler diziler. Bu özellik, C# 7.3 ile başlayarak kullanılabilir.

## <a name="example"></a>Örnek

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Ayrıca Bkz.
 [C# Programlama Kılavuzu](../index.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](index.md)  
 [-unsafe (C# Derleyici Seçenekleri)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [Atık Toplama](../../../standard/garbage-collection/index.md)  
