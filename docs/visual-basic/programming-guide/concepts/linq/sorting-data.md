---
title: Verileri Sıralama
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406800"
---
# <a name="sorting-data-visual-basic"></a>Verileri sıralama (Visual Basic)

Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar. İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir. İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.

Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir.

![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)

Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.

## <a name="methods"></a>Yöntemler

|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|OrderBy|Değerleri artan düzende sıralar.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|OrderByDescending|Değerleri azalan düzende sıralar.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|ThenBy|Artan sırada ikincil bir sıralama gerçekleştirir.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|ThenByDescending|Azalan sırada ikincil bir sıralama gerçekleştirir.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|Reverse|Bir koleksiyondaki öğelerin sırasını tersine çevirir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri

### <a name="primary-sort-examples"></a>Birincil sıralama örnekleri

#### <a name="primary-ascending-sort"></a>Birincil artan sıralama

Aşağıdaki örnek, bir `Order By` dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a>Birincil azalan sıralama

Sonraki örnekte, `Order By Descending` BIR LINQ sorgusunda, dizeyi azalan sırada ilk harfine göre sıralamak için yan tümcesinin nasıl kullanılacağı gösterilmektedir.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a>İkincil sıralama örnekleri

#### <a name="secondary-ascending-sort"></a>İkincil artan sıralama

Aşağıdaki örnek, bir `Order By` dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir. Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a>İkincil azalan sıralama

Sonraki örnekte, `Order By Descending` BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağı gösterilmektedir ve azalan düzende bir birincil sıralama, artan sırada ve ikincil bir sıralama işlemleri yapılır. Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Order By Yan Tümcesi](../../../language-reference/queries/order-by-clause.md)
- [Nasıl yapılır: sorgu sonuçlarını sıralama](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
