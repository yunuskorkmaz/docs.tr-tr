---
title: Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 3d841e5ca25afde94674af0fedc9a824c382be5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345752"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma

Bu örnek, farklı kaynaklardan gelen verileri yeni türler dizisiyle nasıl birleştiriler gösterilmektedir.

> [!NOTE]
> Hala bir veritabanında bulunan verilerle dosya sistemindeki bellek içi verileri veya verileri birleştirmeyi denemeyin. Bu tür etki alanları arası birleştirmeler, veritabanı sorguları ve diğer kaynak türleri için birleştirme işlemlerinin tanımlanabileceği farklı yollardan dolayı tanımlanmamış sonuçlar verebilir. Ayrıca, veritabanındaki veri miktarı yeterince büyükse, böyle bir işlemin bellek dışı bir özel duruma neden olabileceği riski de vardır. Veritabanından bellek içi verilere veri katılmak için, önce arama `ToList` veya `ToArray` veritabanı sorgusunda ve ardından iade edilen koleksiyonda birleştirme gerçekleştirin.

## <a name="to-create-the-data-file"></a>Veri dosyasını oluşturmak için

[Farklı dosyalardan (LINQ) (C#) içerik birleştirme nasıl](./how-to-join-content-from-dissimilar-files-linq.md)açıklandığı gibi, names.csv ve scores.csv dosyalarını proje klasörünüze kopyalayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, elektronik tablo verilerini `Student` .csv biçiminde simüle eden iki bellek içi dize koleksiyonundan birleştirilmiş verileri depolamak için adlandırılmış bir türün nasıl kullanılacağını gösterir. Dizeleri ilk koleksiyonu öğrenci adları ve kimlikleri temsil eder ve ikinci koleksiyon öğrenci kimliği (ilk sütunda) ve dört sınav puanları temsil eder. Kimlik yabancı anahtar olarak kullanılır.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int ID { get; set; }
    public List<int> ExamScores { get; set; }
}

class PopulateCollection
{
    static void Main()
    {
        // These data files are defined in How to join content from
        // dissimilar files (LINQ).

        // Each line of names.csv consists of a last name, a first name, and an
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");

        // Each line of scores.csv consists of an ID number and four test
        // scores, separated by commas. For example, 111, 97, 92, 81, 60
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");

        // Merge the data sources using a named type.
        // var could be used instead of an explicit type. Note the dynamic
        // creation of a list of ints for the ExamScores member. The first item
        // is skipped in the split string because it is the student ID,
        // not an exam score.
        IEnumerable<Student> queryNamesScores =
            from nameLine in names
            let splitName = nameLine.Split(',')
            from scoreLine in scores
            let splitScoreLine = scoreLine.Split(',')
            where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
            select new Student()
            {
                FirstName = splitName[0],
                LastName = splitName[1],
                ID = Convert.ToInt32(splitName[2]),
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                              select Convert.ToInt32(scoreAsText)).
                              ToList()
            };

        // Optional. Store the newly created student objects in memory
        // for faster access in future queries. This could be useful with
        // very large data files.
        List<Student> students = queryNamesScores.ToList();

        // Display each student's name and exam score average.
        foreach (var student in students)
        {
            Console.WriteLine("The average score of {0} {1} is {2}.",
                student.FirstName, student.LastName,
                student.ExamScores.Average());
        }

        //Keep console window open in debug mode
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/* Output:
    The average score of Omelchenko Svetlana is 82.5.
    The average score of O'Donnell Claire is 72.25.
    The average score of Mortensen Sven is 84.5.
    The average score of Garcia Cesar is 88.25.
    The average score of Garcia Debra is 67.
    The average score of Fakhouri Fadi is 92.25.
    The average score of Feng Hanying is 88.
    The average score of Garcia Hugo is 85.75.
    The average score of Tucker Lance is 81.75.
    The average score of Adams Terry is 85.25.
    The average score of Zabokritski Eugene is 83.
    The average score of Tucker Michael is 92.
 */
```

[Select](../../../language-reference/keywords/select-clause.md) yan tümcesinde, iki kaynaktan gelen verileri kullanarak `Student` her yeni nesneyi anında anetmek için bir nesne baş harfer kullanılır.

Bir sorgunun sonuçlarını depolamanız yoksa, anonim türler adlandırılmış türlerden daha kullanışlı olabilir. Sorgu sonuçlarını sorgunun yürütüldedildiği yöntemin dışına geçerseniz adlandırılmış türler gereklidir. Aşağıdaki örnek, önceki örnekle aynı görevi yürütür, ancak adlandırılmış türler yerine anonim türleri kullanır:

```csharp
// Merge the data sources by using an anonymous type.
// Note the dynamic creation of a list of ints for the
// ExamScores member. We skip 1 because the first string
// in the array is the student ID, not an exam score.
var queryNamesScores2 =
    from nameLine in names
    let splitName = nameLine.Split(',')
    from scoreLine in scores
    let splitScoreLine = scoreLine.Split(',')
    where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
    select new
    {
        First = splitName[0],
        Last = splitName[1],
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                      select Convert.ToInt32(scoreAsText))
                      .ToList()
    };

// Display each student's name and exam score average.
foreach (var student in queryNamesScores2)
{
    Console.WriteLine("The average score of {0} {1} is {2}.",
        student.First, student.Last, student.ExamScores.Average());
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
