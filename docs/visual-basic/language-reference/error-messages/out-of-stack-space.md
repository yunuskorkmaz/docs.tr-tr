---
title: Yığın için ayrılan alan doldu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925586"
---
# <a name="out-of-stack-space-visual-basic"></a>Yığın için ayrılan alan doldu (Visual Basic)
Büyür ve küçülür bellek dinamik olarak yürütülen programınızın talepleri olan bir çalışma alanı yığınıdır. Kendi sınırları aşıldı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordamlar çok derin iç içe değil olduğunu kontrol edin.  
  
2. Özyinelemeli yordamlar düzgün sonlandırmak emin olun.  
  
3. Yerel değişkenler kullanılabilir alandan daha fazla yerel değişken gerektiriyorsa, Modül düzeyinde bazı değişkenleri bildirme deneyin. Ayrıca tüm değişkenleri yordamda statik koyarak bildirebilirsiniz `Property`, `Sub`, veya `Function` anahtar sözcüğü ile `Static`. Ya da `Static` yordamları statik bağımsız değişkenler bildirmek için deyimi.  
  
4. Daha fazla yığın alanı değişken uzunluklu dizeler sabit uzunluklu dizeler kullanmak gibi bazı değişken uzunluklu dizeler olarak, sabit uzunluklu dizeler yeniden tanımlama. Ayrıca, hiçbir yığın alanı gerektiren modül düzeyinde dizesi tanımlayabilirsiniz.  
  
5. Sayısını denetleyin iç içe geçmiş `DoEvents` işlev çağrıları kullanarak `Calls` hangi yordamların yığında etkin görünüme iletişim kutusu.  
  
6. Bir "olay cascade" olay yordamı zaten yığında çağıran olarak olay tetiklemeyi tarafından neden olmadı emin olun. Bir olay cascade Sonlandırılmamış özyinelemeli yordam çağrısı benzer, ancak kod içinde açık çağrı yerine, Visual Basic çağrı yapıldığından daha az belirgin. Kullanım `Calls` hangi yordamların yığında etkin görünüme iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bellek Pencereleri](/visualstudio/debugger/memory-windows)
