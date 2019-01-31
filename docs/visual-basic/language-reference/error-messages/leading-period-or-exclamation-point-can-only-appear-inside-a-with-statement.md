---
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 367da8e7c9fd8c14a16a09b1f023e7637d78309d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259563"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
Bir nokta (.) ya da ünlem işareti (!) olmayan iç bir `With` olmadan bir ifade soldaki blok gerçekleşir. Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üye içeren öğeyi belirten bir ifade gerektirir. Bu hemen erişimcisinin veya hedefi olarak sola görünmelidir bir `With` üye erişimi içeren yapı taşıdır.  
  
 **Hata Kimliği:** BC30157  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Emin `With` blok hatalı biçimlendirilmiş.  
  
2.  Yoksa hiçbir `With` engelleme, değerlendirilen erişimcisinin üyeyi içeren tanımlanmış bir öğe sola bir ifade ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Code'daki Özel Karakterler](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
