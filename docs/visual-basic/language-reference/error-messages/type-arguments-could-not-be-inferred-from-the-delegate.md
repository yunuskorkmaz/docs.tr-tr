---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1024cf6f2c1fa112db29cb710eef190a5022d3af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838605"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Tür bağımsız değişkenleri temsilciden gösterilemedi
Atama ifadesi kullanan `AddressOf` genel adresi atamak için yordamı bir temsilci, ancak genel yordam herhangi bir türü bağımsız değişken sağlamıyor.  
  
 Normalde, genel tür çağırdığınızda, bir tür bağımsız değişkeni genel tür tanımlar. her tür parametresi için sağlayın. Herhangi bir tür bağımsız değişkeni sağlamazsanız derleyici için tür parametreleri geçirilecek türlerini çıkarması çalışır. İçerik türlerini çıkarması derleyici için yeterli bilgi sağlamazsa bir hata oluşturulur.  
  
 **Hata Kimliği:** BC36564  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yordamı genel tür bağımsız değişkenleri belirtin `AddressOf` ifade.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Visual Basic'de genel yordamlar](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
