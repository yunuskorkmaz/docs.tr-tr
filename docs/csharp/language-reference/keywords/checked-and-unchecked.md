---
title: İşaretli ve İşaretsiz - C# Başvurusu
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173646"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# deyimleri denetlenen veya denetlenmemiş bağlamında yürütülebilir. Denetlenen bir bağlamda, aritmetik taşma bir özel durum yükseltir. Denetlenmemiş bir bağlamda, aritmetik taşması yoksayılır ve sonuç hedef türüne uymayan yüksek sıralı bitler atılarak kesilir.  
  
- [kontrol edildi](checked.md) Denetlenen bağlamı belirtin.  
  
- [işaretlenmemiş](unchecked.md) İşaretlenmemiş bağlamı belirtin.  
  
 Aşağıdaki işlemler taşma denetiminden etkilenir:  
  
- İntegral türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:  
  
     `++`, `--`, `-`unary `-` `*`, `+`, ,`/`  
  
- İntegral türleri arasında veya integral `float` `double` türünden veya integral türünden açık sayısal dönüşümler.  
  
 Ne `checked` belirtilmişse ne de `unchecked` belirtilmişse, sabit olmayan ifadeler (çalışma zamanında değerlendirilen ifadeler) için varsayılan [bağlam, -denetlenen](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeriyle tanımlanır. Varsayılan olarak, bu seçeneğin değeri ayarlanmamış ve aritmetik işlemler denetlenmemiş bir bağlamda yürütülür.

 Sabit ifadeler (derleme zamanında tam olarak değerlendirilebilen ifadeler) için varsayılan bağlam her zaman denetlenir. Sabit bir ifade açıkça denetlenmemiş bir içeriğe yerleştirilmediği sürece, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
