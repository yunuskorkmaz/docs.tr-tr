---
title: (C# üzerinde LINQ) gruplandırılmış birleştirmeler gerçekleştirme
description: C# içinde LINQ kullanarak gruplandırılmış birleştirmeler gerçekleştirme konusunda bilgi edinin.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689144"
---
# <a name="perform-grouped-joins"></a>Gruplanmış birleşimler gerçekleştirme

Grup birleştirme hiyerarşik veri yapıları üretmek için kullanışlıdır. Bu, her öğeden ilk koleksiyonun ikinci koleksiyondan ilişkili öğeleri kümesi ile eşleşmesini.

Örneğin, bir sınıf veya adlı bir ilişkisel veritabanı tablo `Student` iki alanları içerebilir: `Id` ve `Name`. Adlı ikinci bir sınıf veya ilişkisel veritabanı tablo `Course` iki alanları içerebilir: `StudentId` ve `CourseTitle`. Bu iki veri kaynağı grubu birleşimi tabanlı eşleşen `Student.Id` ve `Course.StudentId`, her grup `Student` koleksiyonuyla `Course` (boş olabilir) nesneleri.

> [!NOTE]
> Sonuç kümesinde ilişkili öğeleri ikinci koleksiyonda bulunup bakılmaksızın, bir grup birleşimin ilk koleksiyonun her öğesine görünür. Bağlantılı öğe bulunduğu durumlarda, o öğe için bağlantılı öğe dizisi boştur. Sonuç Seçici, bu nedenle ilk koleksiyonun her öğesine erişimi vardır. Bu ikinci koleksiyonda eşleşme olan ilk koleksiyondan öğeler erişilemiyor bir grup olmayan birleştirme sonucu seçicide farklıdır.

Bu makalede ilk örnekte grubuna katılma işlemi gösterilmektedir. İkinci örnek XML öğeleri oluşturmak için bir grup birleştirme kullanmayı gösterir.

## <a name="example---group-join"></a>Örnek - Group JOIN

Aşağıdaki örnek, bir grup birleşim türünde nesne gerçekleştirir `Person` ve `Pet` göre `Person` eşleşen `Pet.Owner` özelliği. Her bir eşleştirmeyi çiftlerini oluşturur, bir grup olmayan birleşimin aksine group JOIN olan bu örnekte ilk koleksiyonun her öğe için yalnızca bir sonuç nesnesi oluşturur. bir `Person` nesne. Olan bu örnekte ikinci koleksiyon karşılık gelen öğeleri `Pet` nesneleri, bir koleksiyona gruplandırılır. Son olarak, sonuç Seçici işlevi içeren her bir eşleşme için anonim bir tür oluşturur `Person.FirstName` ve koleksiyonu `Pet` nesneleri.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Örnek - Group JOIN XML dosyası oluşturmak için

Grup birleştirmeleri, LINQ to XML kullanarak XML oluşturmak için idealdir. Aşağıdaki örnek, anonim türler oluşturmak yerine, sonuç Seçici işlevi katılan nesnelerini temsil eden bir XML öğeleri oluşturur dışında önceki örneğe benzerdir.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [İç birleşimler gerçekleştirme](perform-inner-joins.md)
- [Sol dış birleştirmeler gerçekleştirme](perform-left-outer-joins.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
