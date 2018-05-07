---
title: 'Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d63c254abe6d12c094e0d1252c9721f668947f09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)
Değeri değişmeyen bir değişken kavramı çelişkili gibi görünebilir. Ancak bazı durumlarda bir sabit uygun olmadığı ve sabit bir değere sahip bir değişken kullanışlıdır. Böyle bir durumda olan bir üye değişkenine tanımlayabilirsiniz [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.  
  
 Kullanamazsınız [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md) bildirme ve aşağıdaki durumlarda sabit bir değer atamak için:  
  
-   `Const` Deyimi kullanmak istediğiniz veri türünü kabul etmiyor  
  
-   Derleme zamanında değeri biliyor musunuz  
  
-   Derleme zamanında sabit değer işlem oluşturulamıyor  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Değeri değişmeyen bir değişken oluşturmak için  
  
1.  Modül düzeyinde sahip bir üye değişken bildirme [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)ve dahil [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Belirleyebileceğiniz `ReadOnly` yalnızca bir üye değişkenine üzerinde. Başka bir deyişle, herhangi bir yordam dışında modülü düzeyinde değişkeni tanımlamanız gerekir.  
  
2.  Tek bir deyimde derleme zamanında değerinde işlem, bir başlatma yan tümcesinde kullanın. `Dim` deyimi. İzleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesi eşittir işareti (`=`), ardından bir ifade. Bu ifade bir sabit değere derleyici değerlendirebilir emin olun.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Bir değere atayabileceğiniz bir `ReadOnly` değişken yalnızca bir kez. Bunu yaptıktan sonra hiçbir kod hiç değerini değiştirebilirsiniz.  
  
     Değer derleme zamanında bilmiyorsanız ya da tek bir deyimde derleme zamanında hesaplayamıyor hala bunu bir oluşturucu çalışma zamanında atayabilirsiniz. Bunu yapmak için bildirmelisiniz `ReadOnly` sınıf veya yapı düzeyinde değişken. Bu sınıf veya yapı oluşturucusu, değişkenin sabit değer işlem ve oluşturucudan döndürmeden önce değişkenine atayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
