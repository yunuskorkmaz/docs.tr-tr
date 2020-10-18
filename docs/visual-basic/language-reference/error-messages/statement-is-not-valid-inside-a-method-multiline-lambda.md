---
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159683"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a>BC30024: Ifade bir yöntem/çok satırlı lambda içinde geçerli değil

İfade `Sub` ,, `Function` özellik `Get` veya özellik yordamı içinde geçerli değil `Set` . Bazı deyimler modüle veya sınıf düzeyine yerleştirilebilir. Diğer bir deyişle, gibi `Option Strict` diğer tüm bildirimlerin önünde olmalıdır.

 **Hata kimliği:** BC30024

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- İfadeyi yordamdan kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../statements/sub-statement.md)
- [Function Deyimi](../statements/function-statement.md)
- [Get Deyimi](../statements/get-statement.md)
- [Set deyimleri](../statements/set-statement.md)
