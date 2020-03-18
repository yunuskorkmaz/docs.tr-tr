---
title: Projeksiyon İşlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: f76eeeb779ab08a575e758a9d974573b700ae652
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168342"
---
# <a name="projection-operations-c"></a>Projeksiyon İşlemleri (C#)
Projeksiyon, bir nesneyi genellikle yalnızca daha sonra kullanılacak özelliklerden oluşan yeni bir forma dönüştürme işlemini ifade eder. Projeksiyon kullanarak, her nesneden oluşturulmuş yeni bir tür oluşturabilirsiniz. Bir özelliği projeleyebilir ve üzerinde matematiksel bir işlev gerçekleştirebilirsiniz. Özgün nesneyi değiştirmeden de yansıtabilirsiniz.  
  
 Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Şunu seçin:|Dönüştürme işlevine dayalı değerleri projeleri.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Selectmany|Dönüştürme işlevine dayanan değerler dizilerini projeleri ve bunları tek bir diziye düzleştirir.|Birden `from` çok yan tümce kullanma|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu İfadesözdizimi Örnekleri  
  
### <a name="select"></a>Şunu seçin:  
 Aşağıdaki örnek, `select` dizeleri listesinde her dize ilk harfi yansıtmak için yan tümceyi kullanır.  
  
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
  
### <a name="selectmany"></a>Selectmany  
 Aşağıdaki örnek, `from` dizeleri listesinde her dize her sözcüğü yansıtmak için birden çok yan tümce kullanır.  
  
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
  
## <a name="select-versus-selectmany"></a>SelectMany'a karşı seç  
 Her ikisinin `Select()` `SelectMany()` de çalışması ve kaynak değerlerinden bir sonuç değeri (veya değer) üretmektir. `Select()`her kaynak değeri için bir sonuç değeri üretir. Bu nedenle, genel sonuç, kaynak koleksiyonuyla aynı sayıda öğeye sahip bir koleksiyondur. Buna karşılık, `SelectMany()` her kaynak değerinden concatenated alt koleksiyonları içeren tek bir genel sonuç üretir. Her kaynak değer için sayısal `SelectMany()` değerler dizisi döndürmek için bir bağımsız değişken olarak geçirilen dönüştürme işlevi. Bu sayısal diziler daha sonra büyük bir `SelectMany()` dizi oluşturmak için biraraya getirmek için biraraya gelirse.  
  
 Aşağıdaki iki illüstrasyon, bu iki yöntemin eylemleri arasındaki kavramsal farkı göstermektedir. Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden çiçek dizisini seçtiğini varsayalım.  
  
 Bu resimde, `Select()` kaynak koleksiyonla aynı sayıda öğeye sahip bir koleksiyonun nasıl döndürgeldiği gösterilmiştir.  
  
 ![Select&#40;&#41;'nin eylemini gösteren grafik](./media/projection-operations/select-action-graphic.png)  
  
 Bu resimde, `SelectMany()` dizilerin ara sırasını, her ara diziden her bir değeri içeren bir nihai sonuç değerine nasıl dönüştüren gösterilmiştir.  
  
 ![SelectMany&#40;&#41; eylemini gösteren grafik.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnek, davranış `Select()` ve `SelectMany()`. Kod, kaynak koleksiyonundaki her çiçek adlarının her listesinden ilk iki öğeyi alarak bir "çiçek buketi" oluşturur. Bu örnekte, dönüştürme işlevinin <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullandığı "tek değer" kendisi bir değerler topluluğudur. Bu, her `foreach` alt dizideki her dizeyi numaralandırmak için fazladan döngü gerektirir.  
  
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
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [yan tümceyi seçin](../../../language-reference/keywords/select-clause.md)
- [Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Grupları kullanarak bir dosyayı birçok dosyaya bölme (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
