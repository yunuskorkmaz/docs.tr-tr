---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
Uygulamayı gerekli işletim sistemi kaynağı alınamadı. Bu sorunun olası nedeni bazıları şunlardır:  
  
-   Uygulaması adlandırılmış işletim sistemi nesneleri oluşturma izni yok.  
  
-   Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için izinlere sahip değil.  
  
-   İşletim sistemi nesnenin erişmek uygulama gerekiyor, ancak başka bir işlem kullanıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Uygulaması adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
2.  Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
3.  Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.  
  
4.  Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri'ne çağırın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Hata ayıklayıcı temel bilgileri](/visualstudio/debugger/debugger-basics)  
 [Bizimle iletişime geçin](/visualstudio/ide/talk-to-us)
