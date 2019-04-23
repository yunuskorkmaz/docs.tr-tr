---
title: Dizi İşleçleri
ms.date: 03/30/2017
ms.assetid: 4d332d32-3806-4451-b7af-25af269194ae
ms.openlocfilehash: 62cb654922af9df65b0ec9abb67bdc33fda09339
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113691"
---
# <a name="sequence-operators"></a><span data-ttu-id="07903-102">Dizi İşleçleri</span><span class="sxs-lookup"><span data-stu-id="07903-102">Sequence Operators</span></span>
<span data-ttu-id="07903-103">Genel olarak bakıldığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veya daha fazla aşağıdaki kalitelerini dizisi işleçleri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="07903-103">Generally speaking, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support sequence operators that have one or more of the following qualities:</span></span>  
  
-   <span data-ttu-id="07903-104">Bir lambda ile dizin parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="07903-104">Take a lambda with an index parameter.</span></span>  
  
-   <span data-ttu-id="07903-105">Sıralı satır özellikleri gibi güvenin <xref:System.Linq.Queryable.TakeWhile%2A>.</span><span class="sxs-lookup"><span data-stu-id="07903-105">Rely on the properties of sequential rows, such as <xref:System.Linq.Queryable.TakeWhile%2A>.</span></span>  
  
-   <span data-ttu-id="07903-106">Rastgele bir CLR mantığınız gibi güvenin <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="07903-106">Rely on an arbitrary CLR implementation, such as <xref:System.Collections.Generic.IComparer%601>.</span></span>  
  
|<span data-ttu-id="07903-107">Desteklenmeyen örnekleri</span><span class="sxs-lookup"><span data-stu-id="07903-107">Examples of Unsupported</span></span>|  
|-----------------------------|  
|<xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2CSystem.Collections.Generic.IEnumerable%7B%60%602%7D%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Reverse%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAt%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Range%28System.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Repeat%60%601%28%60%600%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Contains%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%600%2C%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SequenceEqual%2A?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="07903-108">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="07903-108">Differences from .NET</span></span>  
 <span data-ttu-id="07903-109">Tüm desteklenen dizisi işleçleri iş dışındaki ortak dil çalışma zamanında (CLR) beklendiği gibi `Average`.</span><span class="sxs-lookup"><span data-stu-id="07903-109">All supported sequence operators work as expected in the common language runtime (CLR) except for `Average`.</span></span> <span data-ttu-id="07903-110">`Average` Oysa ortalama türü ile aynı türde bir değer döndürür CLR'de `Average` döndürür ya da her zaman bir <xref:System.Double> veya <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="07903-110">`Average` returns a value of the same type as the type being averaged, whereas in the CLR `Average` always returns either a <xref:System.Double> or a <xref:System.Decimal>.</span></span> <span data-ttu-id="07903-111">Kaynak bağımsız değişkenini açıkça ise dönüştürme çift / ondalık ya da Seçici bıraktığı çift / ondalık, sonuçta elde edilen SQL böyle bir dönüştürme de sahip olur ve sonucu beklendiği gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07903-111">If the source argument is explicitly cast to double / decimal or the selector casts to double / decimal, the resulting SQL will also have such a conversion and the result will be as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07903-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07903-112">See also</span></span>

- [<span data-ttu-id="07903-113">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="07903-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
