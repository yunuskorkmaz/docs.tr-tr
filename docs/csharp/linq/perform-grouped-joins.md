---
title: Gruplandırılmış birleştirmeler gerçekleştirme
description: Gruplandırılmış birleştirmeler gerçekleştirme.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288183"
---
# <a name="perform-grouped-joins"></a>Gruplandırılmış birleştirmeler gerçekleştirme

Group JOIN hiyerarşik veri yapılarını üretmek için yararlıdır. İlk koleksiyonun ikinci koleksiyondan ilişkili öğeleri kümesi ile her öğeden çiftleri.  
  
 Örneğin, bir sınıf veya adlı bir ilişkisel veritabanı tablo `Student` iki alanları içerebilir: `Id` ve `Name`. Adlı ikinci sınıf veya ilişkisel veritabanı tablosu `Course` iki alanları içerebilir: `StudentId` ve `CourseTitle`. Bir grup birleşimi, bu iki veri kaynaklarının dayalı eşleşen `Student.Id` ve `Course.StudentId`, her grup `Student` koleksiyonuyla `Course` (boş olabilir) nesneleri.  
  
> [!NOTE]
>  İlk koleksiyonun her öğesine bağlantılı öğeler ikinci koleksiyonda bulunup bağımsız olarak bir grup birleştirme sonuç kümesi görüntülenir. Bu öğe için ilişkili öğeleri dizisi ilişkili öğe bulunduğu durumda boştur. Sonuç Seçici bu nedenle ilk koleksiyonun her öğesine erişebilir. Bu ikinci koleksiyonda eşleşme olan ilk koleksiyon öğeleri erişemez bir grup olmayan birleştirme sonucu seçicide farklıdır.  
  
 Bu konudaki ilk örnek bir grup birleştirme gerçekleştirme gösterir. İkinci örnek bir grup birleştirme XML öğeleri oluşturmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
  
### <a name="group-join-example"></a>Grubu birleşim örneği  
 Aşağıdaki örnek nesne türü bir grup birleştirme gerçekleştirir `Person` ve `Pet` göre `Person` eşleşen `Pet.Owner` özelliği. Her eşleşen öğeleri çifti oluşturur, bir grup olmayan birleşimin aksine group JOIN olan bu örnekte ilk koleksiyonun her öğe için yalnızca bir sonuç nesnesi oluşturur. bir `Person` nesnesi. İkinci koleksiyon olan bu örnekte karşılık gelen öğeleri `Pet` nesneleri, bir koleksiyona gruplandırılır. Son olarak, sonuç Seçici işlevi oluşan her eşleşmesi için anonim bir tür oluşturur `Person.FirstName` ve koleksiyonu `Pet` nesneleri.  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="group-join-to-create-xml-example"></a>XML örneği oluşturmak için Grup birleştirme  
 Grup birleştirmeleri LINQ-XML kullanılarak XML oluşturmak için idealdir. Anonim türler oluşturmak yerine, sonuç Seçici işlevi birleştirilmiş nesneleri temsil XML öğeleri oluşturur aşağıdaki örnek önceki örneğe benzerdir.  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [İç birleşimler gerçekleştirme](perform-inner-joins.md)  
 [Sol dış birleştirmeler gerçekleştirme](perform-left-outer-joins.md)  
 [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)  
 
