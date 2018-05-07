---
title: Yol dosya erişim hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pathfile-access-error"></a>Yol/Dosya erişim hatası
Bir dosya erişim veya disk erişimi işlemi sırasında işletim sistemi yolunu ve dosya adı arasında bir bağlantı yapılamıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya belirtiminin doğru biçimlendirildiğinden emin olun. Bir dosya adı bir tam (mutlak) veya göreli içerebilir yolu. (Yolu, başka bir sürücüdeyse) tam nitelenmiş bir yol sürücü adıyla başlar ve kök dosyasının açık yolunu listeler. Tam olmayan tüm geçerli sürücü ve dizine göreli yoludur.  
  
2.  Varolan salt okunur dosya değiştirirler bir dosyayı kaydetmek denemedi emin olun. Bu durumda, hedef dosya salt okunur özniteliğini değiştirmek veya dosyayı farklı bir dosya adıyla kaydedin.  
  
3.  Değil dener salt okunur bir dosya olarak sıralı açmak emin olun `Output` veya `Append` modu. Bu durumda, dosyayı açma `Input` modu veya değişiklik dosyasının salt okunur özniteliği.  
  
4.  Visual Basic projesinde bir veritabanı veya belge değiştirme girişiminde bulunmadı emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
