---
title: (C# üzerinde LINQ) join tümcesinin sonuçlarını sıralama
description: C# LINQ join tümcesinin sonuçlarını sıralama öğrenin.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: e4a12b6f9b4a99decb1f64524ebe67a196084a04
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404742"
---
# <a name="order-the-results-of-a-join-clause"></a>Join tümcesinin sonuçlarını sıralama

Bu örnek, bir birleştirme işleminin sonuçlarını sıralama gösterilmektedir. Sıralama alanına katılım işleminden gerçekleştirildiğini unutmayın. Hizmetini kullanıyor olsanız da bir `orderby` yan tümcesi bir veya daha fazla kaynak ile birleştirme öncesinde dizilerinin, genellikle bunu önermiyoruz. Bazı LINQ sağlayıcıları sıralama alanına katılım işleminden koruyabilir değil.

## <a name="example"></a>Örnek

Bu sorgu, bir grup birleştirme oluşturur ve sonra hala kapsamındaki kategori öğesi temelinde grupları sıralar. Anonim tür başlatıcı içinde alt sorguda ürünleri serisinden eşleşen tüm öğeleri sıralar.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

[Dil ile Tümleşik Sorgu (LINQ)](index.md)  
[orderby yan tümcesi](../language-reference/keywords/orderby-clause.md)  
[join yan tümcesi](../language-reference/keywords/join-clause.md)  