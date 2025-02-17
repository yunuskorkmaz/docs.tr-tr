---
title: Gruplanmış birleşimler gerçekleştirme (C# üzerinde LINQ)
description: C# ' de LINQ kullanarak gruplanmış birleşimler gerçekleştirmeyi öğrenin.
ms.date: 04/22/2020
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 6411479c5fe6cb0ee79a0cd3df6de2f4d42c26a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542815"
---
# <a name="perform-grouped-joins"></a>Gruplanmış birleşimler gerçekleştirme

Grup birleştirmesi, hiyerarşik veri yapıları üretmek için yararlıdır. İkinci koleksiyondaki bağıntılı öğeler kümesiyle ilk koleksiyondaki her öğeyi çiftler.

Örneğin, adlı bir sınıf veya ilişkisel veritabanı tablosu `Student` iki alan içerebilir: `Id` ve `Name` . Adlı ikinci bir sınıf veya ilişkisel veritabanı tablosu `Course` iki alan içerebilir: `StudentId` ve `CourseTitle` . Bu iki veri kaynağına, eşleştirmeye göre bir grup birleşimi `Student.Id` `Course.StudentId` , her birini `Student` bir `Course` nesne koleksiyonu (boş olabilir) ile gruplandırmalıdır.

> [!NOTE]
> İlk koleksiyonun her öğesi, bir grup birleşimi sonuç kümesinde, bağıntılı öğelerin ikinci koleksiyonda bulunup bulunamadığına bakılmaksızın görünür. Bağıntılı öğelerin bulunamadığı durumda, bu öğe için bağıntılı öğelerin sırası boştur. Bu nedenle, sonuç seçicisinin ilk koleksiyonun her öğesine erişimi vardır. Bu, ikinci koleksiyonda eşleşmesi olmayan ilk koleksiyondaki öğelere erişemeyen, grup olmayan bir birleşimde elde edilen sonuç seçiciden farklıdır.

> [!WARNING]
> <xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType> geleneksel ilişkisel veritabanı koşullarında doğrudan eşdeğer değildir. Ancak, bu yöntem, İç birleştirmeler ve sol dış birleşimlerin bir üst kümesini uygular. Bu işlemlerin her ikisi de gruplanmış bir JOIN bakımından yazılabilir. Daha fazla bilgi için bkz. [JOIN işlemleri](../programming-guide/concepts/linq/join-operations.md) ve [Entity Framework Core, groupjoın](/ef/core/querying/complex-query-operators#groupjoin).

Bu makaledeki ilk örnekte, Grup birleştirmesini nasıl gerçekleştireceğiniz gösterilmektedir. İkinci örnek, bir grup birleştirmenin XML öğeleri oluşturmak için nasıl kullanılacağını gösterir.

## <a name="example---group-join"></a>Örnek-gruba ekleme

Aşağıdaki örnek, türüyle `Person` `Pet` eşleşen ve özelliğine dayalı olarak nesne grubuna bir grup birleşimi uygular `Person` `Pet.Owner` . Her eşleşme için bir öğe çifti üreten grup olmayan bir birleştirmenin aksine, Group JOIN, ilk koleksiyondaki her öğe için yalnızca bir sonuç nesnesi oluşturur, bu örnekte bir `Person` nesnedir. Bu örnekte nesneler olan ikinci koleksiyondaki karşılık gelen öğeler `Pet` , bir koleksiyon halinde gruplandırılır. Son olarak, sonuç Seçicisi işlevi bir nesne koleksiyonundan oluşan her bir eşleşme için anonim bir tür oluşturur `Person.FirstName` `Pet` .

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Örnek-XML oluşturmak için gruba ekleme

Grup birleşimleri, LINQ to XML kullanarak XML oluşturmak için idealdir. Aşağıdaki örnek, anonim türler oluşturmak yerine bir önceki örneğe benzerdir, sonuç Seçici işlevi de birleştirilmiş nesneleri temsil eden XML öğeleri oluşturur.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [İç birleşimler gerçekleştirme](perform-inner-joins.md)
- [Sol dış birleşimler gerçekleştirme](perform-left-outer-joins.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
