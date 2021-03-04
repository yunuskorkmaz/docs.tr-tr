---
description: 'Hakkında daha fazla bilgi edinin: tek örnekli bir başlatma için gerekli olan bir işletim sistemi kaynağı alınamadığından beklenmeyen bir hata oluştu'
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 76f7bd43c05ea3bd46b352a791debac984ca8fcd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103614"
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
- [Hata Ayıklayıcı Temel Bilgileri](/visualstudio/debugger/debugger-basics)
- [Visual Studio geri bildirim seçenekleri](/visualstudio/ide/feedback-options)
