---
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396252"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Deyim yöntem/çok satırlı lambda içinde geçerli değil
İfade `Sub` ,, `Function` özellik `Get` veya özellik yordamı içinde geçerli değil `Set` . Bazı deyimler modüle veya sınıf düzeyine yerleştirilebilir. Diğer bir deyişle, gibi `Option Strict` diğer tüm bildirimlerin önünde olmalıdır.  
  
 **Hata kimliği:** BC30024  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İfadeyi yordamdan kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../statements/sub-statement.md)
- [Function Deyimi](../statements/function-statement.md)
- [Get Deyimi](../statements/get-statement.md)
- [Set deyimleri](../statements/set-statement.md)
