---
title: 'Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)'
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: a40ff5ddcf606b0de8a1f41d96523526dc849462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571343"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)

Bu örnek, yeni türleri dizisine farklı kaynaklardan verileri birleştirme gösterilmektedir.

> [!NOTE]
> Bellek içi verileri veya veri, dosya sisteminde hala bir veritabanındaki verilerle katılın çalışmayın. Böyle etki alanları arası birleştirmeler farklı şekilde, birleştirme işlemleri veritabanı sorguları ve diğer kaynağı türleri için tanımlanabilir nedeniyle tanımlanmamış sonuçlara yol açabilir. Buna ek olarak, veritabanındaki veri miktarı yeterince büyük olduğunda bu tür bir işlem bellek yetersiz özel durum neden olabilecek bir riski yoktur. Bellek içi veriler bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve ardından birleştirme döndürülen koleksiyon üzerinde gerçekleştirin.

## <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için

Bölümünde anlatıldığı gibi names.csv ve scores.csv dosyaları proje klasörünüze kopyalayın [nasıl yapılır: Dosyalardan içerik (LINQ) katılın (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, adlandırılmış tür işlemi gösterilir `Student` birleştirilen verilerin elektronik tablo verilerini .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonlardan depolamak için. Dizenin ilk koleksiyon kimlikleri ve Öğrenci adlarını ve ikinci koleksiyon Öğrenci Kimliği (ilk sütunda) ve dört sınavı puanları temsil eder. Kimlik, yabancı anahtar olarak kullanılır.

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
        // These data files are defined in How to: Join Content from
        // Dissimilar Files (LINQ).

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

İçinde [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi, bir nesne Başlatıcı her yeni örneği oluşturmak için kullanılan `Student` iki kaynaklardan gelen verileri kullanarak nesne.

Bir sorgunun sonuçlarını depolamak yoksa, anonim türleri adlandırılmış türler daha kullanışlı olabilir. Sorgu sonuçları sorgunun yürütüldüğü yöntemi dışında geçirirseniz, adlandırılmış türler gereklidir. Aşağıdaki örnek önceki örnekle aynı görevi yürütür, ancak anonim türler yerine adlandırılmış türlerini kullanır:

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

## <a name="compiling-the-code"></a>Kod derleme

Oluşturun ve aşağıdaki seçeneklerden birini hedefleyen bir proje derleme:

- .NET framework sürüm 3.5 System.Core.dll öğesine başvuru ile.
- .NET framework sürüm 4.0 veya üzeri.
- .NET core sürüm 1.0 veya üzeri.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [Anonim Tipler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
