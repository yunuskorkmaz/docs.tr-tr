---
title: 'Nasıl yapılır: Herhangi bir Sözcük veya Alana Göre Metin Verilerini Sıralama veya Filtreleme (LINQ)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 798f30d39b4f805001c8c28b9ad6212061550775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397732"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)

Aşağıdaki örnek, virgülle ayrılmış değerler gibi yapılandırılmış metnin çizgilerinin satırdaki herhangi bir alana göre nasıl sıralanacağını gösterir. Alan, çalışma zamanında dinamik olarak belirtilmiş olabilir. Puanlar. csv içindeki alanların, bir öğrencinin KIMLIK numarasını temsil ettiğini ve ardından bir dizi dört test puandığını varsayın.

### <a name="to-create-a-file-that-contains-data"></a>Veri içeren bir dosya oluşturmak için

Bu konudaki puanlarını. csv verilerini, [benzer dosyalardan (LINQ) (Visual Basic) Içerik ekleme](how-to-join-content-from-dissimilar-files-linq.md) ve çözüm klasörünüze kaydetme konularına kopyalayın.

## <a name="example"></a>Örnek

```vb
Class SortLines

    Shared Sub Main()
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Change this to any value from 0 to 4
        Dim sortField As Integer = 1

        Console.WriteLine("Sorted highest to lowest by field " & sortField)

        ' Demonstrates how to return query from a method.
        ' The query is executed here.
        For Each str As String In SortQuery(scores, sortField)
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Function SortQuery(
        ByVal source As IEnumerable(Of String),
        ByVal num As Integer) As IEnumerable(Of String)

        Dim scoreQuery = From line In source
                         Let fields = line.Split(New Char() {","})
                         Order By fields(num) Descending
                         Select line

        Return scoreQuery
    End Function
End Class
' Output:
' Sorted highest to lowest by field 1
' 116, 99, 86, 90, 94
' 120, 99, 82, 81, 79
' 111, 97, 92, 81, 60
' 114, 97, 89, 85, 82
' 121, 96, 85, 91, 60
' 122, 94, 92, 91, 91
' 117, 93, 92, 80, 87
' 118, 92, 90, 83, 78
' 113, 88, 94, 65, 91
' 112, 75, 84, 91, 39
' 119, 68, 79, 88, 92
' 115, 35, 72, 91, 70
```

Bu örnek ayrıca bir Işlevden nasıl sorgu değişkeni dönebileceğinizi gösterir.

## <a name="compile-the-code"></a>Kodu derle

`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
