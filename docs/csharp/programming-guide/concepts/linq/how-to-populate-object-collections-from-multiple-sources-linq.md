---
title: Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)
description: C# ' de LINQ kullanarak farklı kaynaklardaki verileri yeni türler dizisine birleştirmeyi öğrenin. Bu örnekler hem anonim hem de adlandırılmış türleri kullanır.
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 9dc9f98ae09e0fe3437b5d2ccab32b3dbcd93714
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104718"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)

Bu örnekte, farklı kaynaklardaki verilerin yeni türler dizisine nasıl birleştiriyapılacağı gösterilmektedir.

> [!NOTE]
> Dosya sistemindeki bellek içi verileri veya verileri, hala veritabanında bulunan verilerle birleştirmeyi denemeyin. Bu tür etki alanları arası birleştirmeler, birleştirme işlemlerinin veritabanı sorguları ve diğer kaynak türleri için tanımlanabileceğinden farklı yollarla tanımsız sonuçlar verebilir. Ayrıca, veritabanındaki veri miktarı yeterince büyükse, bu tür bir işlemin bellek dışı bir özel duruma neden olabileceği bir risk vardır. Verileri bir veritabanından bellek içi verilere katmak için, önce veritabanı sorgusuna çağrı yapın `ToList` `ToArray` ve ardından döndürülen koleksiyonda JOIN işlemini gerçekleştirin.

## <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için

names.csv ve scores.csv dosyalarını, [benzer dosyalardaki (LINQ) (C#) içerik ekleme](./how-to-join-content-from-dissimilar-files-linq.md)bölümünde açıklandığı gibi proje klasörünüze kopyalayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Student` . csv biçiminde elektronik tablo verilerinin benzetimini yapan iki bellekteki iki bellek koleksiyonundan birleştirilmiş verileri depolamak için adlandırılmış bir türün nasıl kullanılacağını gösterir. İlk dize koleksiyonu, öğrenci adlarını ve kimliklerini temsil eder ve ikinci koleksiyon öğrenci KIMLIĞINI (ilk sütunda) ve dört sınav puanlarını temsil eder. KIMLIK yabancı anahtar olarak kullanılır.

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

[Select](../../../language-reference/keywords/select-clause.md) yan tümcesinde bir nesne Başlatıcısı, `Student` iki kaynaktaki verileri kullanarak her yeni nesnenin örneğini oluşturmak için kullanılır.

Bir sorgunun sonuçlarını depolamanız gerekmiyorsa, anonim türler adlandırılmış türlerden daha kullanışlı olabilir. Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin dışına geçirirseniz adlandırılmış türler gereklidir. Aşağıdaki örnek, önceki örnekle aynı görevi yürütür, ancak adlandırılmış türler yerine anonim türler kullanır:

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

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
