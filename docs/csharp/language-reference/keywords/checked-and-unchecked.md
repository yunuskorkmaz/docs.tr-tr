---
title: "Checked ve Unchecked (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# ifadelerinin işaretli veya işaretsiz bağlamda çalıştırabilirsiniz. Checked bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretli bir bağlamda aritmetik taşma göz ardı edilir ve sonuç kesilmiş.  
  
-   [işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli belirt bağlamı.  
  
-   [Unchecked](../../../csharp/language-reference/keywords/unchecked.md) denetlenmeyen bağlamı belirtin.  
  
 Ne `checked` ya da `unchecked` belirtilmemişse, varsayılan bağlam derleyici seçenekleri gibi dış faktörlere bağlıdır.  
  
 Aşağıdaki işlemleri taşma denetleyerek etkilenir:  
  
-   Tam sayı türleri üzerinde aşağıdaki önceden tanımlanmış işleçleri kullanarak ifadeler:  
  
     `++``--` -(tekli) `+`  -    `*``/`  
  
-   Açık sayısal dönüşümler tam sayı türleri arasında.  
  
 [/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) derleyici seçeneği açıkça kapsamında olmayan tüm tamsayı aritmetik ifadeler işaretli veya işaretsiz bağlamının belirtmenize olanak sağlar bir `checked` veya `unchecked` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Deyim anahtar sözcükleri](../../../csharp/language-reference/keywords/statement-keywords.md)
