---
title: "Hatalı dosya modu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>Hatalı dosya modu
Dosya içerikleri düzenleme kullanılan ifadeleri dosyanın açılmış olduğu moduna uygun olmalıdır. Olası nedenler şunlardır:  
  
-   A `FilePutObject` veya `FileGetObject` deyimi sıralı bir dosyayı belirtir.  
  
-   A `Print` deyimi dışında bir erişim modu için açık bir dosyayı belirtir `Output` veya `Append`.  
  
-   Bir `Input` deyimi dışında bir erişim modu için açık bir dosyayı belirtir`Input`  
  
-   Bir salt okunur dosyaya yazma girişimi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Emin olun `FilePutObject` ve `FileGetObject` için açık dosyalara yalnızca başvuran `Random` veya `Binary` erişim.  
  
-   Emin olun `Print` için açık bir dosyayı belirtir `Output` veya `Append` erişim modu. Değilse, veri dosyasında yerleştirmek için farklı bir deyimi kullanın veya uygun bir mod dosyasında yeniden açın.  
  
-   Emin olun `Input` için açık bir dosyayı belirtir `Input`. Aksi durumda, veri dosyasına yerleştirin veya uygun bir mod dosyayı yeniden için farklı bir deyimini kullanın.  
  
-   Bir salt okunur dosyaya yazıyorsanız, dosya okuma/yazma durumunu değiştirme veya yazma çalışmayın.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Sorun giderme: Okuma ve dosyalara metin yazma](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
