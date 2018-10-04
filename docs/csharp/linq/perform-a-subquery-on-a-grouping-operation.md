---
title: (C# üzerinde LINQ) gruplandırma işleminde alt sorgu gerçekleştirme
description: C# içinde LINQ kullanarak bir gruplandırma işleminde alt sorgu gerçekleştirme yapma.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261126"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Gruplandırma işleminde alt sorgu gerçekleştirme

Bu makalede, kaynak verileri gruplar halinde sıralar ve sonra bir alt sorgu her bir grup üzerinde tek tek gerçekleştiren bir sorgu oluşturmak için iki farklı yolu gösterilmektedir. Her örnekte temel tekniği kullanarak kaynak öğeleri gruplandırmak için olan bir *devamlılık* adlı `newGroup`ve ardından yeni bir alt sorgu karşı oluşturma `newGroup`. Bu alt sorgu, dış sorgu tarafından oluşturulan her yeni gruba göre çalıştırılır. Bu örnekte son çıkışı değil bir grup ancak anonim türler düz dizisi olduğunu unutmayın.  
  
Gruba hakkında daha fazla bilgi için bkz. [group yan tümcesi](../language-reference/keywords/group-clause.md).  
  
Devamlılıklar hakkında daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md). Aşağıdaki örnek, veri kaynağı olarak bir bellek içi veri yapısı kullanır, ancak tüm LINQ veri kaynağı türü için aynı ilkeler geçerlidir.  
  
## <a name="example"></a>Örnek

> [!NOTE]
> Bu örnekte örnek koda tanımlanan nesneleri başvuruları içeren [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
