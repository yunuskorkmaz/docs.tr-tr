---
title: 'Nasıl yapılır: Verileri bir değişkene Içine ve dışına taşıma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: df55f122c4ea029a383196f8d9684295ac8926aa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631117"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Nasıl yapılır: Verileri bir değişkene Içine ve dışına taşıma (Visual Basic)

Değişken adını atama ifadesinin sol tarafına koyarak bir değişkende bir değer depolursunuz.

## <a name="putting-data-in-a-variable"></a>Verileri bir değişkene koyma

#### <a name="to-store-a-value-in-a-variable"></a>Bir değişkende bir değeri depolamak için

- Atama ifadesinin sol tarafındaki değişken adını kullanın.

    Aşağıdaki örnek, değişkenin `alpha`değerini ayarlar.

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    Atama ifadesinin sağ tarafında oluşturulan değer değişkeninde depolanır.

## <a name="getting-data-from-a-variable"></a>Bir değişkenden veri alma

Değişkenin değerini bir ifadeye değişken adını ekleyerek alırsınız.

#### <a name="to-retrieve-a-value-from-a-variable"></a>Bir değişkenden değer almak için

- Bir ifadede değişken adını kullanın. Bir sabiti, bir sabit veya sabit değer, bir sabit değeri tanımlayan bir ifade dışında herhangi bir yerde kullanabilirsiniz.

  \-veya

- Atama deyimindeki eşittir (`=`) işaretinden sonraki değişken adını kullanın.

  Aşağıdaki örnek, değişkenin `startValue` değerini okur ve sonra değişkenin `counter` değerini bir ifadede kullanır.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  Değişkenin değeri yalnızca bir sabit olarak ifade edilir ve sonra atama deyiminin sol tarafındaki değişken veya özellikte saklanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
