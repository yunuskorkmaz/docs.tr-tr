---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bir değişkenin Içine ve dışına veri taşıma (Visual Basic)'
title: 'Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: e75be83f82a3e1418099375eb52a2d2cc4fdbd18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481824"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)

Değişken adını atama ifadesinin sol tarafına koyarak bir değişkende bir değer depolursunuz.

## <a name="putting-data-in-a-variable"></a>Verileri bir değişkene koyma

#### <a name="to-store-a-value-in-a-variable"></a>Bir değişkende bir değeri depolamak için

- Atama ifadesinin sol tarafındaki değişken adını kullanın.

    Aşağıdaki örnek, değişkenin değerini ayarlar `alpha` .

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    Atama ifadesinin sağ tarafında oluşturulan değer değişkeninde depolanır.

## <a name="getting-data-from-a-variable"></a>Bir değişkenden veri alma

Değişkenin değerini bir ifadeye değişken adını ekleyerek alırsınız.

#### <a name="to-retrieve-a-value-from-a-variable"></a>Bir değişkenden değer almak için

- Bir ifadede değişken adını kullanın. Bir sabiti, bir sabit veya sabit değer, bir sabit değeri tanımlayan bir ifade dışında herhangi bir yerde kullanabilirsiniz.

  \-veya

- Atama deyimindeki eşittir () işaretinden sonraki değişken adını kullanın `=` .

  Aşağıdaki örnek, değişkenin değerini okur `startValue` ve sonra değişkenin değerini `counter` bir ifadede kullanır.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  Değişkenin değeri yalnızca bir sabit olarak ifade edilir ve sonra atama deyiminin sol tarafındaki değişken veya özellikte saklanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](index.md)
- [Değişken Bildirimi](variable-declaration.md)
- [Nesne Değişkenleri](object-variables.md)
