---
title: (C# üzerinde LINQ) bir iç içe geçmiş grup oluşturma
description: C# LINQ sorgu ifadesinde iç içe geçmiş grup oluşturmayı öğrenin.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: c973048d0859f61596c62c294131b8c00d0039f8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404755"
---
# <a name="create-a-nested-group"></a>İç içe geçmiş grup oluşturma

Aşağıdaki örnek, bir LINQ sorgu ifadesinde iç içe geçmiş gruplar oluşturma işlemi gösterilmektedir. Öğrenci yıl veya sınıf düzeyine göre oluşturulan her grup ardından bireylerin adlarına göre gruplara ek bölünmüştür.

## <a name="example"></a>Örnek

> [!NOTE]
> Bu örnekte örnek koda tanımlanan nesneleri başvuruları içeren [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Üç iç içe geçmiş Not `foreach` iç içe geçmiş Grup iç öğeleri üzerinde yinelemek için döngüleri gereklidir.

## <a name="see-also"></a>Ayrıca bkz.

[Dil ile Tümleşik Sorgu (LINQ)](index.md)
