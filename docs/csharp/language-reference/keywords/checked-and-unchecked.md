---
title: Checked ve Unchecked (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# ifadelerinin işaretli veya işaretsiz bağlamda çalıştırabilirsiniz. Checked bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretli bir bağlamda aritmetik taşma göz ardı edilir ve sonuç kesilmiş.  
  
-   [işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli belirt bağlamı.  
  
-   [Unchecked](../../../csharp/language-reference/keywords/unchecked.md) denetlenmeyen bağlamı belirtin.  
  
 Ne `checked` ya da `unchecked` belirtilmemişse, varsayılan bağlam derleyici seçenekleri gibi dış faktörlere bağlıdır.  
  
 Aşağıdaki işlemleri taşma denetleyerek etkilenir:  
  
-   Tam sayı türleri üzerinde aşağıdaki önceden tanımlanmış işleçleri kullanarak ifadeler:  
  
     `++` `--` -(tekli)   `+` -   `*` `/`  
  
-   Açık sayısal dönüşümler tam sayı türleri arasında.  
  
 [/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) derleyici seçeneği açıkça kapsamında olmayan tüm tamsayı aritmetik ifadeler işaretli veya işaretsiz bağlamının belirtmenize olanak sağlar bir `checked` veya `unchecked` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Deyim Anahtar Sözcükleri](../../../csharp/language-reference/keywords/statement-keywords.md)
