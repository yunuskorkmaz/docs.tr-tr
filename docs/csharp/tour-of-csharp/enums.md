---
title: "C# numaralandırmaları - C# dili turu"
description: "C# sabitleri adlı numaralandırmalar, ayrık hakkında bilgi edinin"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="enums"></a>Numaralandırmalar

Bir ***enum türü*** adlandırılmış sabitler kümesiyle ayrı değer türüdür. Ayrık değerler kümesi olan tür tanımlama gerektiğinde numaralandırmaları tanımlar. Tam sayı değeri türlerinden biri, temel alınan depolama alanı olarak kullanırlar. Ayrık değerler için anlamsal anlamı sağlarlar.

Aşağıdaki örnek bildirir ve kullandığı bir `enum` adlı türü `Color` üç sabit değerleri ile `Red`, `Green`, ve `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Her `enum` türüne sahip adlı karşılık gelen bir tam sayı türü ***temel alınan tür*** , `enum` türü. Bir `enum` açıkça bir temel alınan tür bildirmiyor türüne sahip bir temel alınan türü `int`. Bir `enum` tür depolama biçimi ve olası değerleri aralığı, temel alınan türü tarafından belirlenir. Kümesini değerlerinden oluşan bir `enum` türü alabilir üzerinde tarafından sınırlı değildir, `enum` üyeleri. Özellikle, arka plandaki herhangi bir değer türü bir `enum` için cast `enum` yazın ve o ayrı geçerli bir değer `enum` türü.

Aşağıdaki örnek bildiren bir `enum` adlı türü `Alignment` bir temel alınan türü ile `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Önceki örnekte gösterildiği gibi bir `enum` üye bildirimi üyesinin değerini belirten bir sabit ifadesine içerebilir. Her sabit değer `enum` üye, temel alınan türü aralığında olmalıdır `enum`. Zaman bir `enum` üye bildirimi açıkça bir değer belirtmiyor, üye sıfır değeri verilir (ilk üyesiyse `enum` türü) veya textually önceki değeri `enum` yanı sıra bir üyesi.

`Enum`değerler dönüştürülür tam sayı değerleri ve tersi tür atamaları kullanarak olabilir. Örneğin:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Varsayılan değer herhangi `enum` türüdür tam sayı değeri sıfır değerine dönüştürülüp `enum` türü. Burada değişkenleri otomatik olarak başlatılır için varsayılan bir değer durumlarda, bu değişkenleri için verilen değerdir `enum` türleri. Varsayılan değer olan sırada bir `enum` kolayca kullanılabilir olması için türü, sabit `0` örtük olarak hiçbirine dönüştürür `enum` türü. Bu nedenle, aşağıdaki izin verilir.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
[Önceki](interfaces.md)
[sonraki](delegates.md)
