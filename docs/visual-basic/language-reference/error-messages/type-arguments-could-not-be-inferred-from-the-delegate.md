---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 757483f1e88276dd9db82de1c2a7e47b5c975b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Tür bağımsız değişkenleri temsilciden gösterilemedi
Atama deyimini kullanan `AddressOf` genel adresi atamak için yordamı bir temsilci, ancak genel yordam için herhangi bir tür bağımsız değişkeni sağlamaz.  
  
 Normalde, genel bir tür çağırdığınızda, genel tür tanımlar her tür parametresi için bir tür bağımsız değişken sağlayın. Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametreleri geçirilecek türleri Infer dener. İçerik türlerini anlamak derleyici için yeterli bilgi sağlamıyorsa, bir hata oluşturulur.  
  
 **Hata Kimliği:** BC36564  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Genel yordamda tür bağımsız değişkenleri belirtin `AddressOf` ifade.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Visual Basic'de genel yordamlar](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
