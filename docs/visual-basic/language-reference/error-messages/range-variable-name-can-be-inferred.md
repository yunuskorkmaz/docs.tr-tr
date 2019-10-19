---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: ca50ddd86cfbba8db0148ed315645714acabc18d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582418"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir

Bir veya daha fazla bağımsız değişken alan bir programlama öğesi bir LINQ sorgusuna dahildir. Derleyici, bu programlama öğesinden bir Aralık değişkeni çıkarsanamıyor.

**Hata kimliği:** BC36599

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Aşağıdaki kodda gösterildiği gibi, programlama öğesi için açık bir değişken adı sağlayın:

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
