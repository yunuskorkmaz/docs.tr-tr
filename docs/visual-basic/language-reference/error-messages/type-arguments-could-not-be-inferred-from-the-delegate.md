---
title: "Tür bağımsız değişkenleri temsilciden gösterilemedi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords: BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Tür bağımsız değişkenleri temsilciden gösterilemedi
Atama deyimini kullanan `AddressOf` genel adresi atamak için yordamı bir temsilci, ancak genel yordam için herhangi bir tür bağımsız değişkeni sağlamaz.  
  
 Normalde, genel bir tür çağırdığınızda, genel tür tanımlar her tür parametresi için bir tür bağımsız değişken sağlayın. Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametreleri geçirilecek türleri Infer dener. İçerik türlerini anlamak derleyici için yeterli bilgi sağlamıyorsa, bir hata oluşturulur.  
  
 **Hata Kimliği:** BC36564  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Genel yordamda tür bağımsız değişkenleri belirtin `AddressOf` ifade.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Visual Basic'de genel yordamlar](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Tür listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
