---
title: İç içe bir grup oluşturma (C#'da LINQ)
description: C#'daki LINQ sorgu ifadesinde iç içe bir grup oluşturmayı öğrenin.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688624"
---
# <a name="create-a-nested-group"></a>İç içe geçmiş grup oluşturma

Aşağıdaki örnekte, BIR LINQ sorgu ifadesinde iç içe gruplar nasıl oluşturulacak gösterilmektedir. Öğrenci yılı veya not düzeyine göre oluşturulan her grup daha sonra bireylerin adlarına göre gruplara ayrılır.

## <a name="example"></a>Örnek

> [!NOTE]
> Bu örnek, sorgulayan [nesneler koleksiyonunda](query-a-collection-of-objects.md)örnek kodda tanımlanan nesnelere başvurular içerir.

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

İç içe bir `foreach` grubun iç öğeleri üzerinde üç iç içe döngünün yeniden kaydedilmesi gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
