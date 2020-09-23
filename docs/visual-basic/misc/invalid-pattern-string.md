---
title: Geçersiz desenli dize
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 5ef12ac27e96205f9ef1c964293847f56b11cb78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090696"
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
