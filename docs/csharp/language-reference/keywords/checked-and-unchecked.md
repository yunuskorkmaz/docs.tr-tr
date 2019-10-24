---
title: İşaretli ve Işaretsiz C# başvuru
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771772"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C#deyimler işaretli veya işaretlenmemiş bağlamda çalıştırılabilir. Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.  
  
- [denetlenen](checked.md) Denetlenen bağlamı belirtin.  
  
- [işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemler taşma denetimini etkiler:  
  
- Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:  
  
     `++`, `--`, birli `-`, `+`, `-`, `*`, `/`  
  
- İntegral türleri arasında veya `float` ya da `double` bir integral türüne açık sayısal dönüştürmeler.  
  
 Ne `checked` ne de `unchecked` belirtilmemişse, sabit olmayan ifadeler (çalışma zamanında değerlendirilen ifadeler) için varsayılan bağlam, [-Checked](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeri tarafından tanımlanır. Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.
 
 Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir. Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
