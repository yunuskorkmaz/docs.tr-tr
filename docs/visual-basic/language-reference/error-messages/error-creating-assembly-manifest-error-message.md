---
title: 'Derleme bildirimi oluşturulurken hata oldu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972285"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Bütünleştirilmiş kod bildirimi oluşturulurken hata \<oluştu: hata iletisi >
Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme Bağlayıcısı (al. exe, Alink olarak da bilinir) çağırır. Bağlayıcı, derlemeyi oluşturmak için önceden egörev aşamasında bir hata bildirdi.  
  
 Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir. Bir derlemeyi tamamen imzalamak için ortak ve özel anahtarlarla ilgili bilgileri içeren geçerli bir anahtar dosyası sağlamanız gerekir. Bir derlemeyi imzalamayı geciktirmek için **yalnızca gecikmeli imzala** onay kutusunu seçmeniz ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir. Bir derleme Gecikmeli imzalanmışsa özel anahtar gerekli değildir. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi güçlü bir adla](../../../standard/assembly/sign-strong-name.md)imzalayın.  
  
 **Hata KIMLIĞI:** BC30140  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Alıntı yapılan hata iletisini inceleyin ve [al. exe](../../../framework/tools/al-exe-assembly-linker.md)konusuna başvurun. hata AL1019 daha fazla açıklama ve öneri  
  
2. Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala](../../../standard/assembly/sign-strong-name.md)
- [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
- [Al. exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
