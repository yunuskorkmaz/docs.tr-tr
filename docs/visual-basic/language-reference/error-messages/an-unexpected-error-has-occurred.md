---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9aa7ba0babe0a89942e320a76e07c05162b31700
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313618"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
Uygulamayı gerekli işletim sistemi kaynak alınamadı. Bu sorunun olası nedeni bazıları şunlardır:  
  
-   Uygulamanın işletim sistemi bir adlandırılan nesne oluşturma izniniz yok.  
  
-   Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturma izniniz yok.  
  
-   Uygulamasının bir işletim sistemi nesne erişmesi gerekir, ancak başka bir işlem tarafından kullanılıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Uygulamanın işletim sistemi bir adlandırılan nesne oluşturmak için yeterli izinlere sahip olduğunu denetleyin.  
  
2. Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olduğunu denetleyin.  
  
3. Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.  
  
4. Altında hatanın gerçekleştiği durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri'ni arayın  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Hata Ayıklayıcısı Temel Bilgileri](/visualstudio/debugger/debugger-basics)
- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
