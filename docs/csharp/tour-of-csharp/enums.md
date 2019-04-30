---
title: C#Numaralandırmalar - Turu C# dil
description: Numaralandırmalar, ayrık sabitlerle adlı hakkında bilgi edininC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706357"
---
# <a name="enums"></a>Numaralandırmalar

Bir ***sabit listesi türü*** adlandırılmış sabitler kümesini içeren farklı bir değer türüdür. Bir ayrık değerler kümesi olabilir bir tür tanımlamak, ihtiyacınız olduğunda, sabit listeleri tanımlayabilirsiniz. Bunlar bir integral değer türlerinin, temel alınan depolama alanı olarak kullanır. Anlam ayrık değerlere sağlarlar.

Aşağıdaki örnek bildirir ve kullandığı bir `enum` adlı türü `Color` üç sabit değerler ile `Red`, `Green`, ve `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Her `enum` türünde adlı karşılık gelen bir integral türü ***temel alınan türü*** , `enum` türü. Bir `enum` açıkça bir temel türü bildirmiyor türüne sahip bir temel alınan türü `int`. Bir `enum` türün depolama biçimi ve olası değerler aralığı kendi temel türü tarafından belirlenir. Dizi değerlerini bir `enum` türü alabilir on ile sınırlı değildir, `enum` üyeleri. Özellikle, temel alınan herhangi bir değer türü bir `enum` atanabilecek `enum` yazın ve bu geçerli bir benzersiz değer `enum` türü.

Aşağıdaki örnek bildirir bir `enum` adlı türü `Alignment` bir temel alınan türüyle `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Önceki örnekte gösterildiği gibi bir `enum` üye bildirimi, üyenin değeri belirten sabit bir ifade içerebilir. Her biri için sabit değerin `enum` üye, temel alınan türü aralığında olmalıdır `enum`. Olduğunda bir `enum` üye bildirimi açıkça bir değer belirtmiyor, üyenin değeri sıfır verilir (ilk üyesiyse `enum` türü) veya metin içeriğini eklemek önceki değerini `enum` yanı sıra bir üyesi.

`Enum` dönüştürülür tamsayı değerleri ve tersi tür atamaları kullanarak bu değerleri olabilir. Örneğin:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Varsayılan değer aşağıdakilerden `enum` türüdür, tamsayı değeri sıfır değerine dönüştürülüp `enum` türü. Burada değişkenleri otomatik olarak başlatılan bir varsayılan değer durumlarda değişkenleri için verilen değer budur `enum` türleri. Varsayılan değeri için sırayla bir `enum` kolayca kullanılabilmesi için tür, değişmez değer `0` örtük olarak birine dönüştürür `enum` türü. Bu nedenle, aşağıdaki izin verilir.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> [Önceki](interfaces.md)
> [İleri](delegates.md)
