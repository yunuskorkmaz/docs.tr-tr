---
title: Özel birleştirme işlemleri (C# üzerinde LINQ)
description: C# dilinde özel LINQ birleştirme işlemleri gerçekleştirmeyi öğreneceksiniz.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: 875ecc3ab2437e299b1d50076bd9b878fa8c64de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43238436"
---
# <a name="perform-custom-join-operations"></a>Özel birleştirme işlemleri gerçekleştirme

Bu örnek ile mümkün olmayan birleştirme işlemleri gerçekleştirme işlemini gösterir `join` yan tümcesi. Bir sorgu ifadesinde `join` yan tümcesi ile sınırlıdır ve en iyi duruma getirilmiş, birleştirme işlemi arayla en yaygın olan equijoins yazın. Equijoin gerçekleştirirken, büyük olasılıkla her zaman en iyi performansı kullanarak erişmenizi sağlayacak `join` yan tümcesi.

Ancak, `join` yan tümcesi aşağıdaki durumlarda kullanılamaz:

- Ne zaman eşitsizlik (bir olmayan-equijoin) bir ifade üzerinde birleştirme predicated.

- Ne zaman birleştirme eşitlik ve eşitsizlik birden fazla deyimde de predicated.

- Ne zaman, birleştirme işleminden önce sağ tarafındaki (iç) dizisi için bir geçici aralık değişkeni Ekle gerekir.

 Equijoins olmayan birleştirmeler gerçekleştirme için birden çok kullanabilirsiniz `from` bağımsız olarak her bir veri kaynağı tanıtmak amacıyla yan tümceler. Ardından bir koşul ifadesinde geçerli bir `where` yan tümcesinin aralık değişkeni için her kaynak. İfade bir yöntem çağrısının form da yararlanabilirsiniz.

> [!NOTE]
> Bu tür özel birleştirme işlemi birden çok kullanımıyla karıştırmayın `from` iç koleksiyonlara erişmek için yan tümcesi. Daha fazla bilgi için [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).

## <a name="example"></a>Örnek

İlk yöntem aşağıdaki örnekte basit bir çapraz birleştirme gösterir. Çok büyük sonuç kümelerinin oluşturmadığından arası birleştirmeler dikkatli kullanılmalıdır. Ancak, bunlar karşı ek sorgular çalıştırdığınız kaynak dizileri oluşturmak için bazı senaryolarda yararlı olabilir.

İkinci yöntem, bir dizi Kategori Kimliği Kategori listesinden sol tarafta listelenen tüm ürünlerin üretir. Kullanımına dikkat edin `let` yan tümcesi ve `Contains` geçici bir dizi oluşturmak için yöntemi. Sorgu önce bir dizi oluşturun ve ilk ortadan kaldırmak da mümkündür `from` yan tümcesi.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte sorgu iç (sağ taraf) dizisi söz konusu olduğunda join tümcesi kendisini önce alınamıyor, anahtarların eşleşmesi temeline göre iki diziyi eklemeniz gerekir. Bu birleştirme ile gerçekleştirilmişse bir `join` yan tümcesi, ardından `Split` her öğe için çağrılacak yöntem sahip. Birden çok kullanımı `from` yinelenen yöntem çağrısının ek yükten kaçınmak sorgu yan tümceleri sağlar. Ancak, bu yana `join` hala olabilir kullanarak birden çok daha hızlı bu özel durumda iyileştirilmiş `from` yan tümceleri. Sonuçlar, öncelikli olarak nasıl pahalı yöntem çağrısında olduğuna bağlı olarak değişir.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)  
- [join yan tümcesi](../language-reference/keywords/join-clause.md)  
- [Join yan tümcesinin sonuçlarını sıralama](order-the-results-of-a-join-clause.md)  