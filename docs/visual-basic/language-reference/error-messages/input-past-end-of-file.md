---
title: "Dosya sonunun ötesinde giriş"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a>Dosya sonunun ötesinde giriş
Ya da bir `Input` deyimi boş bir dosya veya bir tüm verileri kullanılır veya kullandığınız okuma `EOF` işlevi bir dosyayla ikili erişim için açıldı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kullanım `EOF` hemen önce işlev `Input` dosyasının sonuna algılamak için deyimi.  
  
2.  İkili erişimi için dosya açıldıktan kullanırsanız `Seek` ve `Loc`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
