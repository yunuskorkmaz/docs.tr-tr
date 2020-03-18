---
title: Özel birleştirme işlemleri gerçekleştirin (C#'da LINQ)
description: C#'da özel LINQ birleştirme işlemlerini nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659858"
---
# <a name="perform-custom-join-operations"></a>Özel birleştirme işlemleri gerçekleştirme

Bu örnek, `join` yan tümceyle mümkün olmayan birleştirme işlemlerinin nasıl gerçekleştirildiğini gösterir. Sorgu ifadesinde, `join` yan tümce, açık ara en yaygın birleştirme işlemi türü olan equijoins ile sınırlıdır ve bunlar için en iyi duruma getirilir. Bir equijoin gerçekleştirirken, büyük olasılıkla her zaman `join` yan tümceyi kullanarak en iyi performansı alırsınız.

Ancak, `join` yan tümce aşağıdaki durumlarda kullanılamaz:

- Birleştirme eşitsizlik ifadesine (eşit olmayan bir şey) dayanıyorsa.

- Birleştirme birden fazla eşitlik veya eşitsizlik ifadesine dayanıyorsa.

- Birleştirme işleminden önce sağ taraf (iç) dizisi için geçici bir aralık değişkeni getirmeniz gerektiğinde.

 Denk olmayan birleştirmeler gerçekleştirmek için, her veri kaynağını `from` bağımsız olarak tanıtmak için birden çok yan tümce kullanabilirsiniz. Daha sonra her kaynak için `where` aralık değişkenine bir yan tümcedeki yüklem ifadesini uygularsınız. İfade de bir yöntem çağrısı şeklinde alabilir.

> [!NOTE]
> Bu tür özel birleştirme işlemini iç koleksiyonlara `from` erişmek için birden çok yan tümcenin kullanılmasıyla karıştırmayın. Daha fazla bilgi için [ara yan tümcesi'ne](../language-reference/keywords/join-clause.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekteki ilk yöntem basit bir çapraz birleştirme gösterir. Çapraz birleştirmeler, çok büyük sonuç kümeleri oluşturabildiklerinden dikkatli kullanılmalıdır. Ancak, ek sorguların çalıştırıldığı kaynak dizileri oluşturmak için bazı senaryolarda yararlı olabilir.

İkinci yöntem, kategori kimliği sol taraftaki kategori listesinde listelenen tüm ürünlerin bir dizisini üretir. Geçici bir dizi `let` oluşturmak `Contains` için yan tümcenin ve yöntemin kullanımına dikkat edin. Ayrıca, sorgudan önce dizi oluşturmak ve ilk `from` yan tümceyi ortadan kaldırmak da mümkündür.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, sorgunun, iç (sağ taraf) dizisinde birleştirme yan tümcesi kendisinden önce alınamayan eşleşen tuşlara dayalı iki diziyi birleştirmesi gerekir. Bu birleştirme bir `join` yan tümceyle `Split` gerçekleştirildiyse, yöntemin her öğe için çağrılması gerekir. Birden çok `from` yan tümcenin kullanılması, sorgunun yinelenen yöntem çağrısının ek yükünden kaçınmasını sağlar. Ancak, `join` en iyi duruma geldiğinden, bu özel durumda `from` yine de birden çok yan tümce yi kullanmaktan daha hızlı olabilir. Sonuçlar, öncelikle yöntem çağrısının ne kadar pahalı olduğuna bağlı olarak değişir.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [birleştirme yan tümcesi](../language-reference/keywords/join-clause.md)
- [Join yan tümcesinin sonuçlarını sıralama](order-the-results-of-a-join-clause.md)
