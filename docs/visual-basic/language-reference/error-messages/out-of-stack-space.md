---
title: Yığın için ayrılan alan doldu
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349192"
---
# <a name="out-of-stack-space-visual-basic"></a>Yığın için ayrılan alan doldu (Visual Basic)
Yığın, yürütülen programınızın taleplerini dinamik olarak büyüyen ve küçüldüğü belleğin çalışma alanıdır. Sınırları aşıldı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordamların çok derin iç içe olmadığını kontrol edin.  
  
2. Özyinelemeli yordamların düzgün sonlandırılmadığından emin olun.  
  
3. Yerel değişkenler kullanılabilir olandan daha fazla yerel değişken alanı gerektiriyorsa, modül düzeyinde bazı değişkenler bildirmeyi deneyin. Ayrıca, `Static`ile `Property`, `Sub`veya `Function` anahtar sözcüğüyle önce statik yordamdaki tüm değişkenleri de bildirebilirsiniz. Ya da yordamlar içindeki bağımsız statik değişkenleri bildirmek için `Static` ifadesini kullanabilirsiniz.  
  
4. Sabit uzunluklu dizeler değişken uzunluklu dizeler olarak daha fazla yığın alanı kullanırken, sabit uzunluklu Dizelerinizin bazılarını değişken uzunluklu dizeler olarak yeniden tanımlayın. Dizeyi, yığın alanı gerektirmeyen modül düzeyinde de tanımlayabilirsiniz.  
  
5. Yığın üzerinde etkin olan yordamları görüntülemek için `Calls` iletişim kutusunu kullanarak iç içe `DoEvents` işlev çağrılarının sayısını denetleyin.  
  
6. Yığında zaten olan bir olay yordamını çağıran bir olay tetikleyerek bir "olay basamaklandırmaya" neden olmadığından emin olun. Olay basamaklama, Sonlandırılmamış özyinelemeli yordam çağrısına benzerdir, ancak çağrı, koddaki açık bir çağrı yerine Visual Basic tarafından yapıldığından daha az açıktır. Yığında etkin olan yordamları görüntülemek için `Calls` iletişim kutusunu kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bellek Pencereleri](/visualstudio/debugger/memory-windows)
