---
title: "Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3d3f0f9380e13addac38e32d4cc095d60e19bcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma
Bu örnek, verilerin farklı kaynaklardan yeni türleri dizisi nasıl birleştirileceğini gösterir.  
  
> [!NOTE]
>  Bir veritabanı hala verilerle dosya sistemindeki bellek içi veri ya da veri katılmaya çalışmayın. Bu tür etki alanları arası birleşimler, birleştirme işlemleri veritabanı sorguları ve diğer kaynakları türleri için tanımlanabilir farklı yolları nedeniyle tanımsız sonuçlara yol açabilir. Ayrıca, veritabanındaki veri miktarını yeterince büyük ise böyle bir işlem, bellek yetersiz özel durum neden olabilecek bir risk vardır. Bellek içi veri bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve birleştirme döndürülen koleksiyonda gerçekleştirin.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
-   Bölümünde açıklandığı gibi names.csv ve scores.csv dosyalarını proje klasörünüze kopyalayın [nasıl yapılır: içerik katılma öğesinden farklı dosyaları (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir adlandırılmış türü kullanmayı gösterir `Student` elektronik tablo verileri .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonundan birleştirilmiş verileri depolamak için. Dizeleri ilk koleksiyonu Öğrenci adları ve kimlikleri ve ikinci koleksiyon Öğrenci Kimliğini (ilk sütun) ve dört incelemesi puanlarını temsil eder. Yabancı anahtar olarak kullanılan kimliği.  
  
```csharp  
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
        // creation of a list of ints for the ExamScores member. We skip   
        // the first item in the split string because it is the student ID,   
        // not an exam score.  
        IEnumerable<Student> queryNamesScores =  
            from nameLine in names  
            let splitName = nameLine.Split(',')  
            from scoreLine in scores  
            let splitScoreLine = scoreLine.Split(',')  
            where splitName[2] == splitScoreLine[0]  
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
  
 İçinde [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi, nesne Başlatıcı her yeni örneğini oluşturmak için kullanılan `Student` iki kaynaktan verileri kullanarak nesne.  
  
 Bir sorgunun sonuçlarını depolamak yoksa anonim türler adlandırılmış türlerinden daha daha kullanışlı olabilir. Sorgu sonuçları sorgu yürütüldüğü yöntemi dışında geçirirseniz adlandırılmış türler gereklidir. Aşağıdaki örnek önceki örnekteki gibi aynı görevi gerçekleştirir, ancak yerine adlandırılmış türler anonim türler kullanır:  
  
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
    where splitName[2] == splitScoreLine[0]  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [Nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
