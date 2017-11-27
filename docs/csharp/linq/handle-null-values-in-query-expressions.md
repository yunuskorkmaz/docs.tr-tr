---
title: "Sorgu ifadelerinde boş değerler işleme"
description: "Sorgu ifadelerinde boş değerler nasıl ele alınacağını."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a>Sorgu ifadelerinde boş değerler işleme

Bu örnek kaynak koleksiyonlarda olası null değerler nasıl ele alınacağını gösterir. Bir nesne koleksiyonu gibi bir <xref:System.Collections.Generic.IEnumerable%601> öğelerine içerebilir [null](../language-reference/keywords/null.md). Bir kaynak koleksiyonu null veya null değeri olan bir öğe içeriyor ve sorgunuzu null değerleri işlemiyor bir <xref:System.NullReferenceException> sorgu yürütülürken oluşturulur.  
  
## <a name="example"></a>Örnek

 Aşağıdaki örnekte gösterildiği gibi bir null başvuru özel durumu önlemek için biçimde geliştirmelisiniz kodu:  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 Önceki örnekte, `where` kategoriler dizisi null tüm öğeler filtreleyen yan tümcesi. Bu teknik JOIN yan tümcesinde null denetimi bağımsızdır. Bu örnekte null ile koşullu ifade çalışır olduğundan `Products.CategoryID` türü `int?` için kestirme olduğu `Nullable<int>`.  
  
## <a name="example"></a>Örnek

 Karşılaştırma anahtarlarından birini bir boş değer atanabilir değer türü yalnızca JOIN yan tümcesinde, boş değer atanabilir bir tür için diğer sorgu ifadesinde çevirebilirsiniz. Aşağıdaki örnekte, varsayımında `EmployeeID` türü değerleri içeren bir sütun `int?`:  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Nullable%601>  
 [LINQ Sorgu ifadeleri](index.md)  
 [Boş değer atanabilir türler](../programming-guide/nullable-types/index.md)
