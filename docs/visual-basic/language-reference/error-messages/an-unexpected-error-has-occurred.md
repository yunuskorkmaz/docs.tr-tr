---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587658"
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
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Hata ayıklayıcı temel bilgileri](/visualstudio/debugger/debugger-basics)  
 [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
