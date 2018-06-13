---
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587390"
---
# <a name="bad-file-mode"></a>Hatalı dosya modu
Dosya içerikleri düzenleme kullanılan ifadeleri dosyanın açılmış olduğu moduna uygun olmalıdır. Olası nedenler şunlardır:  
  
-   A `FilePutObject` veya `FileGetObject` deyimi sıralı bir dosyayı belirtir.  
  
-   A `Print` deyimi dışında bir erişim modu için açık bir dosyayı belirtir `Output` veya `Append`.  
  
-   Bir `Input` deyimi dışında bir erişim modu için açık bir dosyayı belirtir `Input`  
  
-   Bir salt okunur dosyaya yazma girişimi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Emin olun `FilePutObject` ve `FileGetObject` için açık dosyalara yalnızca başvuran `Random` veya `Binary` erişim.  
  
-   Emin olun `Print` için açık bir dosyayı belirtir `Output` veya `Append` erişim modu. Değilse, veri dosyasında yerleştirmek için farklı bir deyimi kullanın veya uygun bir mod dosyasında yeniden açın.  
  
-   Emin olun `Input` için açık bir dosyayı belirtir `Input`. Aksi durumda, veri dosyasına yerleştirin veya uygun bir mod dosyayı yeniden için farklı bir deyimini kullanın.  
  
-   Bir salt okunur dosyaya yazıyorsanız, dosya okuma/yazma durumunu değiştirme veya yazma çalışmayın.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
