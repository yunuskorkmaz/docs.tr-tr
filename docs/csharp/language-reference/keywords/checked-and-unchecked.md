---
title: Checked ve Unchecked - C# başvurusu
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
ms.openlocfilehash: 12f65fe4b1dc710ff5c053073817dbd793c86082
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661931"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# ifadeleri işaretli veya işaretsiz bağlam içinde çalıştırabilirsiniz. Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretlenmemiş bir bağlamda aritmetik taşma göz ardı edilir ve hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak sonuç kesilmiş.  
  
- [işaretli](checked.md) içerik teslim belirtin.  
  
- [denetlenmeyen](unchecked.md) denetlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemleri taşma denetimi tarafından etkilenir:  
  
- Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleç kullanarak ifadeleri:  
  
     `++`, `--`, birli `-`, `+`, `-`, `*`, `/`  
  
- Açık sayısal dönüştürmeler integral türleri arasında ya da `float` veya `double` bir integral türü.  
  
 Kullanılmazsa `checked` ya da `unchecked` belirtilirse, sabit olmayan ifade (çalışma zamanında değerlendirilir ifadeleri) için varsayılan bağlamı değeri tarafından tanımlanan [-kullanıma](../compiler-options/checked-compiler-option.md) derleyici seçeneği. Varsayılan olarak bu seçenek değeri ayarlanmamış ve işaretlenmemiş bir bağlamda aritmetik işlemler yürütülür.
 
 (Tam olarak derleme zamanında değerlendirilebilen ifadeleri) sabit ifadeler için her zaman varsayılan bağlamı denetlenir. Sabit bir ifade açıkça işaretlenmemiş bir bağlamda eklenmediği sürece ifadesi derleme zamanı değerlendirmesi sırasında gerçekleşen taşıyor derleme zamanı hatalarına neden.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
