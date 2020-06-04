---
title: Geçersiz desenli dize
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402219"
---
# <a name="invalid-pattern-string"></a>Geçersiz desenli dize
Bir aramanın işleminde belirtilen model dizesi `Like` geçersiz.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Liste ifadeleri için geçerli karakterleri gözden geçirin.  
  
2. Model aralığında, başlangıç aralığı karakterinin ' de olduğu gibi bitiş aralığı karakterinden küçük olduğundan emin olun `[a-z]` .  
  
3. Model aralığında, içinde olduğu gibi birbirini izleyen birden çok tire olmadığından emin olun `[a--z]` .  
  
4. Kapanış ayracı ile bitiş deseninin aralığı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Like İşleci](../language-reference/operators/like-operator.md)
