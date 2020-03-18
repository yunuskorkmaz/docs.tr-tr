---
title: Gruplanmış birleştirmeleri gerçekleştirin (LinQ C#'da)
description: C#'da LINQ kullanarak gruplu birleştirmeleri nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689144"
---
# <a name="perform-grouped-joins"></a>Gruplanmış birleşimler gerçekleştirme

Grup birleştirme hiyerarşik veri yapıları üretmek için yararlıdır. İlk koleksiyondaki her öğeyi ikinci koleksiyondaki ilişkili öğeler kümesiyle eşler.

Örneğin, bir sınıf veya ilişkisel `Student` veritabanı tablosu adlı `Id` `Name`iki alan içerebilir: ve . İkinci sınıf veya ilişkisel `Course` veritabanı tablosu adlı `StudentId` `CourseTitle`iki alan içerebilir: ve . Bu iki veri kaynağının grup birleşimi, `Student.Id` eşleştirmeye dayalıdır `Course.StudentId`ve her birini `Student` bir `Course` nesne koleksiyonuyla gruplar (boş olabilir).

> [!NOTE]
> İlk koleksiyonun her öğesi, ikinci koleksiyonda ilişkili öğelerin bulunup bulunmadığına bakılmaksızın bir grup birleştirme sonucu kümesinde görünür. İlişkili öğelerin bulunmadığı durumlarda, bu öğe için ilişkili öğelerin sırası boştur. Sonuç seçici bu nedenle ilk koleksiyonun her öğesine erişebilir. Bu, ikinci koleksiyonda eşleşmesi olmayan ilk koleksiyondaki öğelere erişemeyen grup dışı bir birleştirmedeki sonuç seçiciden farklıdır.

Bu makaledeki ilk örnek, bir grup birleştirme gerçekleştirmek için nasıl gösterir. İkinci örnek, XML öğeleri oluşturmak için bir grup birliğini nasıl kullanacağınızı gösterir.

## <a name="example---group-join"></a>Örnek - Grup birleştirme

Aşağıdaki örnek, `Person` tür nesnelerin birgrup birleştirme `Pet` gerçekleştirir `Person` ve `Pet.Owner` özelliği eşleşen dayalı. Her eşleşme için bir çift öğe üretecek olan grup dışı birbirleştirmenin aksine, grup birleştirme, bu örnekte bir nesne `Person` olan ilk koleksiyonun her öğesi için yalnızca bir sonuç nesnesi üretir. Bu örnekte `Pet` nesneler olan ikinci koleksiyondaki karşılık gelen öğeler bir koleksiyonda gruplandırılır. Son olarak, sonuç seçici işlevi, nesnelerin oluşan `Person.FirstName` ve oluşan her `Pet` maç için anonim bir tür oluşturur.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Örnek - XML oluşturmak için grup birleştirme

Grup birleştirmeleri, LINQ'dan XML'e kadar kullanarak XML oluşturmak için idealdir. Aşağıdaki örnek, anonim türler oluşturmak yerine, sonuç seçici işlevinin birleştirilmiş nesneleri temsil eden XML öğeleri oluşturması dışında önceki örneğe benzer.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [İç birleşimler gerçekleştirme](perform-inner-joins.md)
- [Sol dış birleşimler gerçekleştirme](perform-left-outer-joins.md)
- [Anonim türleri](../programming-guide/classes-and-structs/anonymous-types.md)
