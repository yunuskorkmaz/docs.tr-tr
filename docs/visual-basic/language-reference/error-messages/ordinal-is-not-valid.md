---
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ordinal-is-not-valid"></a>Sıra sayısı geçerli değil
Aramanız için dinamik bağlantı kitaplığı (DLL) gösterilen bir yordamı adı yerine bir sayı kullanmak üzere kullanarak `#num` sözdizimi. Bu hata, aşağıdaki olası nedenleri vardır:  
  
-   Dönüştürme girişimi `#num` başarısız bir sıra ifadesi.  
  
-   `#num` Belirtilen herhangi bir işlev DLL'de belirtmiyor.  
  
-   Tür kitaplığı geçersiz bir sıra numarası iç kullanımını kaynaklanan geçersiz bir bildirim sahiptir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ada göre yordam çağrısı veya geçerli bir sayı ifadeyi temsil emin olun.  
  
2.  Emin olun `#num` geçerli bir işlev DLL tanımlar.  
  
3.  Kodu yorum tarafından soruna yordam çağrısı yalıtma. Yazma bir `Declare` yordam ve rapor türü kitaplığı satıcıya sorun bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
