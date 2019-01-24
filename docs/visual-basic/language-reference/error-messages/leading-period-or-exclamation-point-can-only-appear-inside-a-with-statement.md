---
title: Önde gelen &#39;. &#39; veya &#39;! &#39; yalnızca içinde görünebilir bir &#39;ile&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e64318d4ececbd887f55a1a202cc2d58c90c8fc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625958"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Önde gelen &#39;. &#39; veya &#39;! &#39; yalnızca içinde görünebilir bir &#39;ile&#39; deyimi
Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir. Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir. Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.  
  
 **Hata Kimliği:** BC30157  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Emin `With` blok hatalı biçimlendirilmiş.  
  
2.  Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Code'daki Özel Karakterler](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
