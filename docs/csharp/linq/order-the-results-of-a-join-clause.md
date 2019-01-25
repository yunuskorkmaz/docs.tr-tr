---
title: (C# üzerinde LINQ) join tümcesinin sonuçlarını sıralama
description: C# LINQ join tümcesinin sonuçlarını sıralama öğrenin.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857894"
---
# <a name="order-the-results-of-a-join-clause"></a>Join tümcesinin sonuçlarını sıralama

Bu örnek, bir birleştirme işleminin sonuçlarını sıralama gösterilmektedir. Sıralama alanına katılım işleminden gerçekleştirildiğini unutmayın. Hizmetini kullanıyor olsanız da bir `orderby` yan tümcesi bir veya daha fazla kaynak ile birleştirme öncesinde dizilerinin, genellikle bunu önermiyoruz. Bazı LINQ sağlayıcıları sıralama alanına katılım işleminden koruyabilir değil.

## <a name="example"></a>Örnek

Bu sorgu, bir grup birleştirme oluşturur ve sonra hala kapsamındaki kategori öğesi temelinde grupları sıralar. Anonim tür başlatıcı içinde alt sorguda ürünleri serisinden eşleşen tüm öğeleri sıralar.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [orderby yan tümcesi](../language-reference/keywords/orderby-clause.md)
- [join yan tümcesi](../language-reference/keywords/join-clause.md)
