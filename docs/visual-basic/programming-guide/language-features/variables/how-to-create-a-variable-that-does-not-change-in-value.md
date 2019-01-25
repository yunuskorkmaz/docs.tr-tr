---
title: 'Nasıl yapılır: (Visual Basic) değeri değişmeyen bir değişken oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 626b46123e3047b391cd67d3e85c25c5432b2a69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640205"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Nasıl yapılır: (Visual Basic) değeri değişmeyen bir değişken oluşturma
Bir değişkenin değerini değiştirmez kavramımız çelişkili görünebilir. Ancak bazı durumlarda bir sabit uygun olmadığı durumlarda ve sabit bir değere sahip bir değişken sağlamak kullanışlıdır. Böyle bir durumda olan bir üye değişkeni tanımlayabilirsiniz [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.  
  
 Kullanamazsınız [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md) bildirmek ve aşağıdaki durumlarda bir sabit değer atamak için:  
  
-   `Const` Deyimi kullanmak istediğiniz veri türünü kabul etmiyor  
  
-   Derleme zamanında bir değer kattığını değil  
  
-   Sabit değer derleme zamanında işlem belirleyemiyoruz  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Değeri değişmeyen bir değişken oluşturmak için  
  
1.  Modül düzeyinde olan bir üye değişkeni bildirme [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)ve [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Belirtebileceğiniz `ReadOnly` yalnızca bir üye değişkeni üzerinde. Başka bir deyişle, her türlü yordam dışında Modül düzeyinde değişkeni tanımlamanız gerekir.  
  
2.  Değerin tek bir deyimde derleme zamanında bilgi işlem, bir başlatma yan tümcesi içinde kullanın. `Dim` deyimi. İzleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesiyle birlikte bir eşittir işareti (`=`) ve ardından bir ifade. Derleyici, bu ifade bir sabit değere değerlendirebilirsiniz emin olun.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Bir değer atamak için bir `ReadOnly` değişken yalnızca bir kez. Bunu yaptıktan sonra kod her zamankinden değerini değiştirebilirsiniz.  
  
     Değer derleme zamanında bilmiyorsanız veya tek bir deyimde derleme zamanında hesaplayamıyor, yine de uygulamayı çalışma zamanında bir oluşturucuda atayabilirsiniz. Bunu yapmak için size bildirmelidir `ReadOnly` sınıf veya yapı düzeyinde değişken. Bu sınıf veya yapı için oluşturucu, sabit değişkenin değerini hesaplamak ve oluşturucudan döndürmeden önce değişkene atayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
