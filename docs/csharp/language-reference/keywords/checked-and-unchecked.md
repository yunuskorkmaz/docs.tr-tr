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
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="checked-and-unchecked-c-reference"></a>Checked ve Unchecked (C# Başvurusu)
C# ifadelerinin işaretli veya işaretsiz bağlamda çalıştırabilirsiniz. Checked bir bağlamda aritmetik taşma bir özel durum oluşturur. İşaretli bir bağlamda aritmetik taşma dikkate alınmaz ve sonucu hedef türünde uymayan tüm yüksek düzey BITS atarak kesilir.  
  
-   [işaretli](checked.md) işaretli belirt bağlamı.  
  
-   [Unchecked](unchecked.md) denetlenmeyen bağlamı belirtin.  
  
 Aşağıdaki işlemleri taşma denetleyerek etkilenir:  
  
-   Tam sayı türleri üzerinde aşağıdaki önceden tanımlanmış işleçleri kullanarak ifadeler:  
  
     `++`, `--`, tekli `-`, `+`, `-`, `*`, `/`  
  
-   Açık sayısal dönüşümler arasında tam sayı türleri, veya `float` veya `double` bir tam sayı türü.  
  
 Ne `checked` ya da `unchecked` belirtilirse, sabit olmayan ifadeleri (çalışma zamanında değerlendirilir ifadelerde) için varsayılan bağlamı değeri tarafından tanımlanan [-işaretli](../compiler-options/checked-compiler-option.md) derleyici seçeneği. Varsayılan olarak bu seçenek unset değeri ve aritmetik işlemler işaretli bir bağlamda yürütülür.
 
 Sabit ifadeleri (derleme zamanında tam olarak değerlendirilebilir ifadelerde) için varsayılan içeriği her zaman denetlenir. Bir sabit ifadesine açıkça bir denetlenmeyen bağlamında eklenmediği sürece, derleme zamanı ifade değerlendirmesi sırasında ortaya taşan derleme zamanı hatalara neden olabilir.
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [C# Anahtar Sözcükleri](index.md)  
 [Deyim Anahtar Sözcükleri](statement-keywords.md)
