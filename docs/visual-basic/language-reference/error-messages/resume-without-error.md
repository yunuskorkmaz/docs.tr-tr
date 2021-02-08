---
description: 'Hakkında daha fazla bilgi edinin: hata olmadan özgeçmişi'
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792017"
---
# <a name="resume-without-error"></a>Hatasız devam et

Hata `Resume` işleme kodu dışında bir ifade görüntülendi veya hata olmamasına rağmen kod bir hata işleyicisine atlandı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `Resume`İfadeyi bir hata işleyicisine taşıyın veya silin.  
  
2. Etiketlere atlamalar yordamlar arasında gerçekleşemez, bu nedenle hata işleyicisini tanımlayan etikete yönelik yordamda arama yapın. Bir ifade olmayan bir deyimin hedefi olarak belirtilen yinelenen bir etiket bulursanız `GoTo` `On Error GoTo` , çizgi etiketini amaçlanan hedefle kabul etmek üzere değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Resume Deyimi](../statements/resume-statement.md)
- [On Error Deyimi](../statements/on-error-statement.md)
