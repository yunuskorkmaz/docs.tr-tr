---
title: 'Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4032bbcbf9924eb5aad4e2cb1a6e74df9a472eca
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;
Visual Basic derleyici bir derleme bir bildirim oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır. Bağlayıcı derlemesi oluşturma öncesi çıkması aşamasında bir hata bildirdi.  
  
 Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir. Tam olarak bir derlemeyi imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir. Oturum bütünleştirilmiş gecikme için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlayın. Derleme gecikmeli imzalanmış olduğunda özel anahtar gerekli değildir. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **Hata Kimliği:** BC30140  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). hata AL1019 daha ayrıntılı bir açıklama ve öneriler  
  
2.  Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
