---
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 1d85f49ce0aed44dea12c9ba16135425e6e2e431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565754"
---
# <a name="bad-file-mode"></a>Hatalı dosya modu
Dosya içerikleri düzenleme içinde kullanılan ifadeleri dosyası içinde açıldı moduna uygun olmalıdır. Olası nedenler şunlardır:  
  
-   A `FilePutObject` veya `FileGetObject` deyimi bir sıralı dosyasını belirtir.  
  
-   A `Print` deyim için bir erişim modu dışında açılmış bir dosyada belirtir `Output` veya `Append`.  
  
-   Bir `Input` deyim için bir erişim modu dışında açılmış bir dosyasını belirtir `Input`  
  
-   Salt okunur dosyaya yazma girişimi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Emin `FilePutObject` ve `FileGetObject` için açık olan dosyaları yalnızca başvuran `Random` veya `Binary` erişim.  
  
-   Emin `Print` belirtir ya da için açılan bir dosyanın `Output` veya `Append` erişim modu. Aksi halde veri dosyasına yerleştirmeniz farklı bir deyim kullanın veya uygun bir modda dosyayı tekrar açın.  
  
-   Emin `Input` için açılan bir dosyanın belirtir `Input`. Aksi durumda, farklı bir deyim veri dosyasında veya uygun bir modda dosyasını yeniden kullanın.  
  
-   Salt okunur dosya yazıyorsanız, dosya okuma/yazma durumunu değiştirebilir veya yazma çalışmayın.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileSystem>
- [Sorun giderme: Okuma ve dosyalara metin yazma](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
