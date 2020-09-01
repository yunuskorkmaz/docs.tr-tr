---
description: Checked ve unchecked-C# başvurusu
title: Checked ve unchecked-C# başvurusu
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138273"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# deyimleri işaretli veya işaretlenmemiş bağlamda çalıştırılabilir. Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.  
  
- [denetlenen](checked.md) Denetlenen bağlamı belirtin.  
  
- [işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemler taşma denetimini etkiler:  
  
- Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:  
  
     `++`,, `--` birli `-` , `+` , `-` , `*` , `/`  
  
- İntegral türleri veya `float` bir integral türü arasında açık sayısal dönüştürmeler `double` .  
  
 Ne `checked` de `unchecked` belirtilmemişse, sabit olmayan ifadeler için varsayılan bağlam (çalışma zamanında değerlendirilen ifadeler) [işaretli](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeri tarafından tanımlanır. Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.

 Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir. Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
