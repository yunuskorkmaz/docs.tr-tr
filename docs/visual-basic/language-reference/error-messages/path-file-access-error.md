---
title: Yol/Dosya erişim hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 70de8f9cb33ab3d889f4916ae3d5de48cd218092
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871191"
---
# <a name="pathfile-access-error"></a>Yol/Dosya erişim hatası

Dosya erişimi veya disk erişimi işlemi sırasında, işletim sistemi yol ve dosya adı arasında bir bağlantı kuramadı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dosya belirtiminin doğru biçimlendirildiğinden emin olun. Bir dosya adı, tam olarak nitelenmiş (mutlak) veya göreli yol içerebilir. Tam nitelikli bir yol sürücü adı ile başlar (yol başka bir sürücüdeyse) ve kökten açık yolu dosya olarak listeler. Tam nitelikli olmayan herhangi bir yol, geçerli sürücü ve dizine göre belirlenir.  
  
2. Varolan bir salt okunurdur dosyanın yerini alacak bir dosyayı kaydetmeyi denediğinizden emin olun. Bu durumda, hedef dosyanın salt okunurdur özniteliğini değiştirin veya dosyayı farklı bir dosya adı ile kaydedin.  
  
3. Salt biçimli bir dosyayı sıralı veya modda açmaya çalışmayın emin olun `Output` `Append` . Bu durumda, dosyayı `Input` modda açın veya dosyanın salt okunurdur özniteliğini değiştirin.  
  
4. Bir veritabanı veya belge içinde Visual Basic projesi değiştirmeyi denediğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../programming-guide/language-features/error-types.md)
