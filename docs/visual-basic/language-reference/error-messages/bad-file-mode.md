---
description: 'Daha fazla bilgi: Hatalı dosya modu'
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: da792407fb37f5c206be7ff39da14d314ef1e2d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797087"
---
# <a name="bad-file-mode"></a>Hatalı dosya modu

Dosya içeriğini düzenleme bölümünde kullanılan deyimler, dosyanın açıldığı moda uygun olmalıdır. Olası nedenler şunlardır:  
  
- `FilePutObject`Or `FileGetObject` deyimleri sıralı bir dosya belirtir.  
  
- Bir `Print` ifade, veya dışında bir erişim modu için açılan bir dosya `Output` belirtir `Append` .  
  
- Bir `Input` ifade, bir erişim modu için açılan bir dosyayı belirtir `Input`  
  
- Salt okunurdur bir dosyaya yazma girişimi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- ' In `FilePutObject` `FileGetObject` yalnızca veya erişim için açık olan dosyalara başvuruda bulunduğundan emin olun `Random` `Binary` .  
  
- `Print`Ya da erişim modu için açılmış bir dosya belirttiğinden emin olun `Output` `Append` . Aksi takdirde, verileri dosyaya yerleştirmek için farklı bir ifade kullanın veya dosyayı uygun bir modda yeniden açın.  
  
- `Input`İçin açılmış bir dosya belirttiğinden emin olun `Input` . Aksi takdirde, verileri dosyaya yerleştirmek veya uygun modda dosyayı yeniden açmak için farklı bir ifade kullanın.  
  
- Salt okunurdur bir dosyaya yazıyorsanız dosyanın okuma/yazma durumunu değiştirin veya yazmaya çalışmayın.  
  
- Nesnesinde bulunan işlevleri kullanın `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem>
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
