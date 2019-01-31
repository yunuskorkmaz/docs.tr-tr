---
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 8339d038f845b8568f31f3068a98ccccf580aeae
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286656"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Temsilci sınıfında\<SınıfAdı >' Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz sahip
Bir çağrı `Invoke` bir temsilci olduğundan başarısız oldu `Invoke` temsilci sınıfı üzerinde uygulanmadı.  
  
 **Hata Kimliği:** BC30220  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Temsilci sınıfının örneği ile oluşturulduğundan emin olun. bir `Dim` ifadesi ve bir yordam temsilci örneği ile atanan `AddressOf` işleci.  
  
2.  Temsilci sınıfı uygulayan kod bulun ve bunu uygulayan emin `Invoke` yordamı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
