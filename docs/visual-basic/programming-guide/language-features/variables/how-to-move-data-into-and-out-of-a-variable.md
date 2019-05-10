---
title: 'Nasıl yapılır: Veri taşıma içine ve dışına bir değişken (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 033d1cb0116b78ca9e3677c920ee5745117573d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663525"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Nasıl yapılır: Veri taşıma içine ve dışına bir değişken (Visual Basic)
Bir değer atama deyiminin sol tarafında değişken adını koyarak bir değişkende depolayın.  
  
## <a name="putting-data-in-a-variable"></a>Bir değişkende veri yerleştirme  
  
#### <a name="to-store-a-value-in-a-variable"></a>Değer bir değişkende depolamak için  
  
- Değişken adı, atama deyiminin sol tarafında kullanın.  
  
     Aşağıdaki örnek, değişkenin değerini ayarlar `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Atama ifadesi sağ tarafında oluşturulan değeri değişkeninde depolanır.  
  
## <a name="getting-data-from-a-variable"></a>Bir değişkenden gelen veri alma  
 Bir değişkenin değeri, değişken adı bir ifade dahil ederek alın.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Bir değişkenden gelen bir değer almak için  
  
- Değişken adı bir ifade kullanın. Bir değişkeni kullanabilirsiniz herhangi bir sabit bir değer veya bir sabit değer dışında bir ifadede bir sabitin değeri tanımlar kullanabilirsiniz.  
  
     -veya-  
  
- Eşit aşağıdaki değişken adını kullanın (`=`) bir atama ifadesinde oturum açın.  
  
     Aşağıdaki örnek, değişkenin değerini okur `startValue` ve değişkeninin değeri kullanır `counter` bir ifadede.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Değişkeninin değeri ifade yalnızca bir sabit olur ve ardından değişken veya özellik atama ifadesi sol tarafındaki depolanır katılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
