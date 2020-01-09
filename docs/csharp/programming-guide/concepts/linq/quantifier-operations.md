---
title: Nicelik belirteci IşlemleriC#()
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635489"
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
|Tümü|Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.|Yok.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.|Yok.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="all"></a>Tümü  
Aşağıdaki örnek, tüm dizelerin belirli bir uzunlukta olduğunu denetlemek için `All` kullanır.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Tümü  
Aşağıdaki örnek, tüm dizelerin ' o ' ile başlayıp başlamamı kontrol etmek için `Any` kullanır.  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>İçerir  
Aşağıdaki örnek, bir dizinin belirli bir öğeye sahip olup olmadığını denetlemek için `Contains` kullanır.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
