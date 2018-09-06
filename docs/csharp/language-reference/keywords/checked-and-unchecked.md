---
title: Checked ve Unchecked (C# Başvurusu)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 04f603905690497bcd4249f73c7296be2c269a60
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741938"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# ifadeleri işaretli veya işaretsiz bağlam içinde çalıştırabilirsiniz. Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretlenmemiş bir bağlamda aritmetik taşma göz ardı edilir ve hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak sonuç kesilmiş.  
  
-   [işaretli](checked.md) içerik teslim belirtin.  
  
-   [denetlenmeyen](unchecked.md) denetlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemleri taşma denetimi tarafından etkilenir:  
  
-   Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleç kullanarak ifadeleri:  
  
     `++`, `--`, birli `-`, `+`, `-`, `*`, `/`  
  
-   Açık sayısal dönüştürmeler integral türleri arasında ya da `float` veya `double` bir integral türü.  
  
 Kullanılmazsa `checked` ya da `unchecked` belirtilirse, sabit olmayan ifade (çalışma zamanında değerlendirilir ifadeleri) için varsayılan bağlamı değeri tarafından tanımlanan [-kullanıma](../compiler-options/checked-compiler-option.md) derleyici seçeneği. Varsayılan olarak bu seçenek değeri ayarlanmamış ve işaretlenmemiş bir bağlamda aritmetik işlemler yürütülür.
 
 (Tam olarak derleme zamanında değerlendirilebilen ifadeleri) sabit ifadeler için her zaman varsayılan bağlamı denetlenir. Sabit bir ifade açıkça işaretlenmemiş bir bağlamda eklenmediği sürece ifadesi derleme zamanı değerlendirmesi sırasında gerçekleşen taşıyor derleme zamanı hatalarına neden.
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
