---
description: 'Hakkında daha fazla bilgi edinin: BC36599: Range değişken adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan çıkarsanamıyor'
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: b729b6786f9b7803a794b9a4e786d94fa41a57ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792069"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>BC36599: Range değişken adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan çıkarsanamıyor

Bir veya daha fazla bağımsız değişken alan bir programlama öğesi bir LINQ sorgusuna dahildir. Derleyici, bu programlama öğesinden bir Aralık değişkeni çıkarsanamıyor.

**Hata kimliği:** BC36599

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Aşağıdaki kodda gösterildiği gibi, programlama öğesi için açık bir değişken adı sağlayın:

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Select yan tümcesi](../queries/select-clause.md)
