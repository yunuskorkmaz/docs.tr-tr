---
title: Nicelik belirteci IşlemleriC#()
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423359"
---
# <a name="quantifier-operations-c"></a>Nicelik belirteci IşlemleriC#()
Nicelik belirteci işlemleri bir dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten <xref:System.Boolean> bir değer döndürür.  
  
 Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir. İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç `true`. İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.|Yok.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Kaydedilmemiş|Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.|Yok.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.|Yok.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
