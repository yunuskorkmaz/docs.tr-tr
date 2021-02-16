---
description: 'Hakkında daha fazla bilgi edinin: verileri filtreleme (Visual Basic)'
title: Verileri Filtreleme
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 2e259209df35a89eb4730f79ffccfee7cb64b9e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428603"
---
# <a name="filtering-data-visual-basic"></a>Verileri filtreleme (Visual Basic)

Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder. Seçim olarak da bilinir.

Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir. Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.

![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)

Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.

## <a name="methods"></a>Yöntemler

|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|OfType|Belirtilen türe atama becerisine bağlı olarak değerleri seçer.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Konum|Bir koşul işlevini temel alan değerleri seçer.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği

Aşağıdaki örnek, `Where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için öğesini kullanır.

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [WHERE yan tümcesi](../../../language-reference/queries/where-clause.md)
- [Nasıl yapılır: sorgu sonuçlarını filtreleme](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [Nasıl yapılır: bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (Visual Basic)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
