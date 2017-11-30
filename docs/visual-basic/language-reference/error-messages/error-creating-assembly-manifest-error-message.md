---
title: "Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici bir derleme bir bildirim oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır. Bağlayıcı derlemesi oluşturma öncesi çıkması aşamasında bir hata bildirdi.  
  
 Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir. Tam olarak bir derlemeyi imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir. Oturum bütünleştirilmiş gecikme için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlayın. Derleme gecikmeli imzalanmış olduğunda özel anahtar gerekli değildir. Daha fazla bilgi için bkz: [nasıl yapılır: derleme (Visual Studio) oturum](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **Hata Kimliği:** BC30140  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve konusuna bakın [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) AL1019 hata için daha fazla açıklama ve öneriler  
  
2.  Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: derleme (Visual Studio) oturum açın](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [İmzalama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe (derleme bağlayıcı)](https://msdn.microsoft.com/library/c405shex)  
 [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Bizimle iletişime geçin](/visualstudio/ide/talk-to-us)
