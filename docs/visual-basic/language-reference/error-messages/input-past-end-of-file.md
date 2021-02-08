---
description: 'Daha fazla bilgi edinin: dosya sonunun ötesinde giriş'
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: b65a57bdc56367518a93880be28781e56c9b99cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796047"
---
# <a name="input-past-end-of-file"></a>Dosya sonunun ötesinde giriş

Bir `Input` ifade, boş olan bir dosyadan veya tüm verilerin kullanıldığı bir dosyadan okunuyor ya da `EOF` işlevi ikili erişim için açılmış bir dosya ile kullandınız.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `EOF` `Input` Dosya sonunu algılamak için deyimden hemen önce işlevini kullanın.  
  
2. Dosya ikili erişim için açılırsa, `Seek` ve kullanın `Loc` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
