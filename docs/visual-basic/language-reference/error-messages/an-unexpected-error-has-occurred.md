---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197379"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
Uygulama gerekli bir işletim sistemi kaynağını alamadı. Bu sorunun olası nedenlerinden bazıları şunlardır:  
  
- Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturma izni yok.  
  
- Ortak dil çalışma zamanının bellekle eşlenen dosyalar oluşturma izni yok.  
  
- Uygulamanın bir işletim sistemi nesnesine erişmesi gerekir, ancak başka bir işlem onu kullanıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
2. Ortak dil çalışma zamanının, bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
3. Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanıyor olabilecek tüm işlemleri temizlemek için bilgisayarı yeniden başlatın.  
  
4. Hatanın oluştuğu koşulları göz önünde, Microsoft Ürün Destek Hizmetleri 'ni çağıran  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Hata Ayıklayıcısı Temel Bilgileri](/visualstudio/debugger/debugger-basics)
- [Bizimle İletişime Geçin](/visualstudio/ide/feedback-options)
