---
title: 'Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)'
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 0789dee28cc2be5e72d2f99e2265e0181e351d8a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584398"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="ed4c8-102">Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)</span><span class="sxs-lookup"><span data-stu-id="ed4c8-102">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>

<span data-ttu-id="ed4c8-103">Bu örnek, yeni türleri dizisine farklı kaynaklardan verileri birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="ed4c8-104">Bellek içi verileri veya veri, dosya sisteminde hala bir veritabanındaki verilerle katılın çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="ed4c8-105">Böyle etki alanları arası birleştirmeler farklı şekilde, birleştirme işlemleri veritabanı sorguları ve diğer kaynağı türleri için tanımlanabilir nedeniyle tanımlanmamış sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="ed4c8-106">Buna ek olarak, veritabanındaki veri miktarı yeterince büyük olduğunda bu tür bir işlem bellek yetersiz özel durum neden olabilecek bir riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="ed4c8-107">Bellek içi veriler bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve ardından birleştirme döndürülen koleksiyon üzerinde gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="ed4c8-108">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ed4c8-108">To create the data file</span></span>

<span data-ttu-id="ed4c8-109">Bölümünde anlatıldığı gibi names.csv ve scores.csv dosyaları proje klasörünüze kopyalayın [nasıl yapılır: Dosyalardan içerik (LINQ) katılın (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="ed4c8-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="ed4c8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed4c8-110">Example</span></span>

<span data-ttu-id="ed4c8-111">Aşağıdaki örnek, adlandırılmış tür işlemi gösterilir `Student` birleştirilen verilerin elektronik tablo verilerini .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonlardan depolamak için.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="ed4c8-112">Dizenin ilk koleksiyon kimlikleri ve Öğrenci adlarını ve ikinci koleksiyon Öğrenci Kimliği (ilk sütunda) ve dört sınavı puanları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="ed4c8-113">Kimlik, yabancı anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-113">The ID is used as the foreign key.</span></span>

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

<span data-ttu-id="ed4c8-114">İçinde [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi, bir nesne Başlatıcı her yeni örneği oluşturmak için kullanılan `Student` iki kaynaklardan gelen verileri kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-114">In the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="ed4c8-115">Bir sorgunun sonuçlarını depolamak yoksa, anonim türleri adlandırılmış türler daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="ed4c8-116">Sorgu sonuçları sorgunun yürütüldüğü yöntemi dışında geçirirseniz, adlandırılmış türler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="ed4c8-117">Aşağıdaki örnek önceki örnekle aynı görevi yürütür, ancak anonim türler yerine adlandırılmış türlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="ed4c8-117">The following example executes the same task as the previous example, but uses anonymous types instead of named types:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ed4c8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed4c8-118">See also</span></span>

- [<span data-ttu-id="ed4c8-119">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="ed4c8-119">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="ed4c8-120">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="ed4c8-120">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="ed4c8-121">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="ed4c8-121">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
