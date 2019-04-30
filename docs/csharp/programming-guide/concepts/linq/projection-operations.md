---
title: Projeksiyon işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 74792c1a58aa17c65f3a153216d50c672e0b6cf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681760"
---
# <a name="projection-operations-c"></a>Projeksiyon işlemleri (C#)
Projeksiyon bir nesne, genellikle daha sonra kullanılacak olan bu özelliklerini içeren yeni bir biçime dönüştürme işlemini ifade eder. Yansıtma kullanarak her nesneden yerleşik yeni bir türünü oluşturabilirsiniz. Proje bir özelliği ve bir matematiksel işlev üzerinde gerçekleştirin. Ayrıca, değişiklik yapmadan özgün nesneye yansıtabilirsiniz.  
  
 Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Seçim|Bir dönüştürme işlevine dayalı projeler değerleri.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projeleri dizileri değeri bir dönüştürme işlevi üzerinde temel alır ve ardından bunları bir dizi düzleştirir.|Birden çok kullanın `from` yan tümceleri|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
  
### <a name="select"></a>Seçim  
 Aşağıdaki örnekte `select` dizelerinin listesini her bir dizenin ilk harfinden projeye yan tümcesi.  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a>SelectMany  
 Aşağıdaki örnek, birden çok kullanır `from` her bir sözcüğü her bir dizenin bir dize listesi içinde proje için yan tümcesi.  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a>SelectMany karşı seçin  
 Hem iş `Select()` ve `SelectMany()` bir sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu. `Select()` Her kaynak değeri için bir sonuç değerini veriyor. Genel sonuç, bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon olur. Buna karşılık, `SelectMany()` her bir kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonucu üretir. Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` numaralandırılabilir dizisi için her kaynak değeri değerlerinin döndürmelidir. Bu numaralandırılabilir dizileri tarafından bitiştirilir `SelectMany()` büyük bir dizi oluşturmak için.  
  
 Aşağıdaki iki çizimler eylemleri, bu iki yöntem arasındaki kavramsal farkı göstermektedir. Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden satmanın dizisi seçer varsayılır.  
  
 Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.  
  
 ![Seçme eylemini gösteren grafik&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Bu çizimde gösterilmektedir nasıl `SelectMany()` her ara diziden her değeri içeren bir sonuç değeri diziler Ara dizisine art arda ekler.  
  
 ![SelectMany eylemini gösteren grafik&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`. Bu kod, kaynak koleksiyonda çiçek adları her iki listesinden ilk iki öğeyi alarak çiçek "demeti" oluşturur. Bu örnekte, "değer tek" Bu dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanır, kendisi değerler koleksiyonu. Bu ek gerektirir `foreach` döngü, her alt dizideki her bir dizenin numaralandırmak için.  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md)
- [Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
