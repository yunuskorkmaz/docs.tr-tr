---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873959"
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
