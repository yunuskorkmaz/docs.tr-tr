---
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: d5d756f1772b9519613e163119b88a3057d36cf3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870625"
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
