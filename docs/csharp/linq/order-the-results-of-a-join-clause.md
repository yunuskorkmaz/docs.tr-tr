---
title: Birleştirme yan tümcesinin sonuçlarını sipariş edin (C#'da LINQ)
description: C#'daki LINQ birleştirme yan tümcesinin sonuçlarını nasıl sipariş edebilirsiniz öğrenin.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659871"
---
# <a name="order-the-results-of-a-join-clause"></a>Join yan tümcesinin sonuçlarını sıralama

Bu örnek, birbirle işleminin sonuçlarının nasıl sıralanın gösteriş olduğunu gösterir. Sıralamanın birleştirmeden sonra gerçekleştirildiğini unutmayın. Birleştirmeden önce `orderby` kaynak dizilerinden bir veya daha fazlasına sahip bir yan tümce yi kullanabilirsiniz, ancak genellikle bunu önermiyoruz. Bazı LINQ sağlayıcıları birleştirmeden sonra bu siparişi koruyamayabilir.

## <a name="example"></a>Örnek

Bu sorgu bir grup birleştirme oluşturur ve sonra hala kapsam içinde olan kategori öğesine göre grupları sıralar. Anonim tür baş harfinin içinde, bir alt sorgu ürün dizisindeki tüm eşleşen öğeleri sıralar.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [orderby yan tümcesi](../language-reference/keywords/orderby-clause.md)
- [birleştirme yan tümcesi](../language-reference/keywords/join-clause.md)
