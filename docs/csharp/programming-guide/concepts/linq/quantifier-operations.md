---
title: Niceleyici İşlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635489"
---
# <a name="quantifier-operations-c"></a>Niceleyici İşlemleri (C#)
Niceleyici işlemleri, bir <xref:System.Boolean> dizideki öğelerden bazılarının veya tümünün bir koşulu karşılayıp karşıladığını gösteren bir değer döndürer.  
  
 Aşağıdaki resimde, iki farklı kaynak dizisinde iki farklı niceleme işlemi gösterilmiştir. İlk işlem, öğelerden birinin veya daha fazlasının 'A' karakteri `true`olup olmadığını sorar ve sonuç . İkinci işlem tüm öğelerin 'A' karakteri olup olmadığını `true`sorar ve sonuç .  
  
 ![LINQ Niceleme İşlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Herhangi biri|Bir dizideki öğelerin bir durumu karşılayıp karşılamadığını belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Bir dizinin belirli bir öğe yi içerip içermediğini belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Sorgu İfadesözdizimi Örnekleri  
  
### <a name="all"></a>Tümü  
Aşağıdaki örnek, `All` tüm dizeleri belirli bir uzunlukta olup olmadığını denetlemek için kullanır.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Herhangi biri  
Aşağıdaki örnekte, `Any` dizeleri 'o' ile başlatılır olup olmadığını kontrol etmek için kullanır.  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contains  
Aşağıdaki örnekte `Contains` belirli bir öğeye sahip bir dizi kontrol etmek için kullanır.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
