---
title: 'Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bfda451cefff699561253910715d8450414b00ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650874"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)
Atama ifadesinin sol tarafta değişken adını koyarak bir değer bir değişkende saklayın.  
  
## <a name="putting-data-in-a-variable"></a>Bir değişkende veri koyma  
  
#### <a name="to-store-a-value-in-a-variable"></a>Bir değişkene bir değer depolamak için  
  
-   Değişken adı atama ifadesinin sol taraftaki kullanın.  
  
     Aşağıdaki örnekte değişken değerini ayarlar `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Atama ifadesinin sağ tarafında oluşturulan değeri değişkende depolanır.  
  
## <a name="getting-data-from-a-variable"></a>Bir değişkeninden veri alma  
 Bir deyimde değişken adı dahil olmak üzere bir değişkenin değerini alır.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Bir değişkeninden bir değer almak için  
  
-   Değişken adı bir ifade kullanın. Bir değişken kullanabilirsiniz herhangi bir yerde bir sabit ya da bir hazır değer dışında bir sabit değer tanımlayan bir ifade kullanabilirsiniz.  
  
     -veya-  
  
-   Eşittir aşağıdaki değişken adını kullanın (`=`) bir atama deyiminde oturum açın.  
  
     Aşağıdaki örnek değişkenin değeri olarak okur `startValue` ve değişkenin değerini kullanır `counter` deyimde.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Değişkenin değeri olarak yalnızca bir sabit gerekir ve ardından değişkeni veya özellikte Atama ifadesinin sol tarafında depolanır ifade katılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
