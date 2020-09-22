---
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870835"
---
# <a name="resume-without-error"></a>Hatasız devam et

Hata `Resume` işleme kodu dışında bir ifade görüntülendi veya hata olmamasına rağmen kod bir hata işleyicisine atlandı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `Resume`İfadeyi bir hata işleyicisine taşıyın veya silin.  
  
2. Etiketlere atlamalar yordamlar arasında gerçekleşemez, bu nedenle hata işleyicisini tanımlayan etikete yönelik yordamda arama yapın. Bir ifade olmayan bir deyimin hedefi olarak belirtilen yinelenen bir etiket bulursanız `GoTo` `On Error GoTo` , çizgi etiketini amaçlanan hedefle kabul etmek üzere değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Resume Deyimi](../statements/resume-statement.md)
- [On Error Deyimi](../statements/on-error-statement.md)
