---
title: "Sıra sayısı geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
