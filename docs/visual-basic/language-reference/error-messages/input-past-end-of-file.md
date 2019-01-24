---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 29a9b5ce3c3f8e6a02b52beda1338fd699143570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491343"
---
# <a name="input-past-end-of-file"></a>Dosya sonunun ötesinde giriş
Ya da bir `Input` ifadesi boş olan bir dosyayı veya tüm veriler kullanılır veya kullandığınız okuma `EOF` işlevi bir dosyayla ikili erişimi için açılır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kullanım `EOF` hemen önce işlev `Input` deyimini dosyanın sonuna algılayın.  
  
2.  Dosya ikili erişimi için açılıp açılmadığını kullanın `Seek` ve `Loc`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
