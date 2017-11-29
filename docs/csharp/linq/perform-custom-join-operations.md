---
title: "Özel birleştirme işlemleri gerçekleştirme"
description: "Özel birleştirme işlemleri gerçekleştirme."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a>Özel birleştirme işlemleri gerçekleştirme

Bu örnek ile mümkün olmayan birleştirme işlemleri gerçekleştirme gösterilmektedir `join` yan tümcesi. Bir sorgu ifadesinde `join` yan tümcesi sınırlıdır ve en iyi duruma getirilmiş, bunun en yaygın equijoins birleştirme işlemi yazın. Equijoin gerçekleştirirken, büyük olasılıkla her zaman en iyi performansı kullanarak hatalarla `join` yan tümcesi.  
  
 Ancak, `join` yan tümcesi aşağıdaki durumlarda kullanılamaz:  
  
-   Ne zaman birleştirme eşitsizlik (bir harici-equijoin) ifadeye bağlı predicated.  
  
-   Ne zaman birleştirme üzerinde eşitlik veya eşitsizlik birden fazla ifade predicated.  
  
-   Birleştirme işlemi önce sağ tarafında (iç) sırası için geçici aralık değişkeni tanıtmak olduğunda.  
  
 Equijoins olmayan birleştirmeler gerçekleştirmek için birden çok kullanabilirsiniz `from` bağımsız olarak her veri kaynağı tanıtmak için yan tümceleri. Ardından bir koşul ifadesi geçerli bir `where` yan tümcesine her kaynak için aralık değişkeni. İfade bir yöntem çağrısı form da alabilir.  
  
> [!NOTE]
>  Bu tür bir özel birleştirme işlemi birden çok kullanımı ile karıştırmayın `from` iç koleksiyonları erişmek için yan tümceleri. Daha fazla bilgi için bkz: [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).  
  
## <a name="example"></a>Örnek  
 İlk yöntem aşağıdaki örnekte basit bir çapraz birleştirme gösterir. Çok büyük sonuç kümeleri oluşturdukları olduğundan çapraz birleştirmeler dikkatli kullanılmalıdır. Ancak, bunlar karşı ek sorgular çalıştırdığınız kaynak sıraları oluşturmak için bazı senaryolarda yararlı olabilir.  
  
 İkinci yöntem kategorisi Kimliğine sol tarafındaki kategori listesinde listelenen tüm ürünleri dizisi üretir. Kullanımına dikkat edin `let` yan tümcesi ve `Contains` geçici bir dizi oluşturmak için yöntemi. Sorgu önce dizi oluşturmak ve ilk ortadan kaldırmak mümkündür `from` yan tümcesi.  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte sorgu, iç (sağ tarafta) dizisi söz konusu olduğunda JOIN yan tümcesi önce kendisini alınamıyor anahtarları eşleşmesini temel alan iki sıraları katılmanız gerekir. Bu katılımı ile gerçekleştirilen varsa bir `join` yan tümcesi, sonra `Split` yöntemi her öğe için çağrılacak sahip olabilir. Birden çok kullanımını `from` yan tümceleri yinelenen yöntem çağrısının yükünü önlemek sorgu sağlar. Ancak, bu yana `join` bunu hala olabilir birden çok kullanarak daha hızlı bu özel durumda iyileştirilmiş `from` yan tümceleri. Sonuçları öncelikle nasıl pahalı yöntem çağrısının olduğuna bağlı olarak değişir.  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [Join tümcesi](../language-reference/keywords/join-clause.md)  
 [Join tümcesinin sonuçlarını sıralama](order-the-results-of-a-join-clause.md)
