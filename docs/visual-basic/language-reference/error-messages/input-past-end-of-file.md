---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013796"
---
# <a name="input-past-end-of-file"></a>Dosya sonunun ötesinde giriş
Ya da bir `Input` ifadesi boş olan bir dosyayı veya tüm veriler kullanılır veya kullandığınız okuma `EOF` işlevi bir dosyayla ikili erişimi için açılır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Kullanım `EOF` hemen önce işlev `Input` deyimini dosyanın sonuna algılayın.  
  
2. Dosya ikili erişimi için açılıp açılmadığını kullanın `Seek` ve `Loc`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
