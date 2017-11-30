---
title: "Join tümcesinin sonuçlarını sıralama"
description: "Join tümcesinin sonuçlarını sıralama yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a>Join tümcesinin sonuçlarını sıralama
Bu örnek, bir birleştirme işlemi sonuçlarını sıralama gösterilmektedir. Sıralama birleştirme sonrasında gerçekleştirildiğini unutmayın. Kullanabilirsiniz ancak bir `orderby` yan tümcesi bir veya daha fazla kaynak ile dizilerinin birleştirme öncesinde, genellikle bunu önermiyoruz. Bazı LINQ sağlayıcıları bu birleştirme sonrasında sıralama koruyabilir değil.  
  
## <a name="example"></a>Örnek  
 Bu sorgu, bir grup birleşim oluşturur ve hala kapsam içi kategori öğesi temelinde grupları sıralar. Anonim tür başlatıcısı bir alt sorgu ürünleri serisinden eşleşen tüm öğeleri sıralar.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [OrderBy yan tümcesi](../language-reference/keywords/orderby-clause.md)  
 [Join tümcesi](../language-reference/keywords/join-clause.md) 
