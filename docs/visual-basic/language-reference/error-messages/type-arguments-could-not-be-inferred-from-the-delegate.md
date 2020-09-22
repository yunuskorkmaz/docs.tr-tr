---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 51b0bbf2e346acdd84a1bc2283db4a71adc9f7dc
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870436"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Tür bağımsız değişkenleri temsilciden gösterilemedi

Atama ekstresi `AddressOf` , bir temsilciye genel yordamın adresini atamak için kullanır, ancak genel yordamda herhangi bir tür bağımsız değişkeni sağlamaz.  
  
 Normal olarak, genel bir tür çağırdığınızda, genel türün tanımladığı her tür parametresi için bir tür bağımsız değişkeni sağlarsınız. Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametrelerine geçirilecek türleri çıkarması için girişimde bulunur. Bağlam derleyicinin türleri çıkarması için yeterli bilgi sağlamıyorsa bir hata oluşturulur.  
  
 **Hata kimliği:** BC36564  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İfadedeki genel yordamın tür bağımsız değişkenlerini belirtin `AddressOf` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [AddressOf İşleci](../operators/addressof-operator.md)
- [Visual Basic'de Genel Yordamlar](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Tür Listesi](../statements/type-list.md)
- [Uzantı Metotları](../../programming-guide/language-features/procedures/extension-methods.md)
