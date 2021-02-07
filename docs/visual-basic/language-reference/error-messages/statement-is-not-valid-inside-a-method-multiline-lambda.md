---
description: 'Hakkında daha fazla bilgi edinin: BC30024: deyimde yöntem/çok satırlı lambda içinde geçerli değil'
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: c70e5563ab8c161966cd9790ae1f192fa5d50b17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731181"
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
