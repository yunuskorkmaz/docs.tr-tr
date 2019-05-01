---
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 15390fb506fe9bca10f6917f5b26451a5569bece
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921127"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir. Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir. Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.  
  
 **Hata Kimliği:** BC30157  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Emin `With` blok hatalı biçimlendirilmiş.  
  
2. Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code'daki Özel Karakterler](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
