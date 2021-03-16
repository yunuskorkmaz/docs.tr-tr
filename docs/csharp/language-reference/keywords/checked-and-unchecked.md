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
ms.openlocfilehash: 0121090265881bfa8287e2f9e83ad4b886bf17c1
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477489"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)

C# deyimleri işaretli veya işaretlenmemiş bağlamda çalıştırılabilir. Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.  
  
- [denetlenen](checked.md) Denetlenen bağlamı belirtin.  
  
- [işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemler taşma denetimini etkiler:  
  
- Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:  
  
     `++`,, `--` birli `-` , `+` , `-` , `*` , `/`  
  
- İntegral türleri veya `float` bir integral türü arasında açık sayısal dönüştürmeler `double` .  
  
 Ne `checked` de `unchecked` belirtilmemişse, sabit olmayan ifadeler için varsayılan bağlam (çalışma zamanında değerlendirilen Ifadeler) [**Checkforoverflowyetersizliği**](../compiler-options/language.md#checkforoverflowunderflow) derleyici seçeneğinin değeri tarafından tanımlanır. Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.

 Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir. Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
