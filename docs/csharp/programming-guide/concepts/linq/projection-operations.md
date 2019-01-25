---
title: Projeksiyon işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: fa9b1d2a0dc63be89e8a93fd5d234f131a2943e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723959"
---
# <a name="projection-operations-c"></a><span data-ttu-id="374e4-102">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="374e4-102">Projection Operations (C#)</span></span>
<span data-ttu-id="374e4-103">Projeksiyon bir nesne, genellikle daha sonra kullanılacak olan bu özelliklerini içeren yeni bir biçime dönüştürme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="374e4-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="374e4-104">Yansıtma kullanarak her nesneden yerleşik yeni bir türünü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="374e4-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="374e4-105">Proje bir özelliği ve bir matematiksel işlev üzerinde gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="374e4-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="374e4-106">Ayrıca, değişiklik yapmadan özgün nesneye yansıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="374e4-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="374e4-107">Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="374e4-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="374e4-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="374e4-108">Methods</span></span>  
  
|<span data-ttu-id="374e4-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="374e4-109">Method Name</span></span>|<span data-ttu-id="374e4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="374e4-110">Description</span></span>|<span data-ttu-id="374e4-111">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="374e4-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="374e4-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="374e4-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="374e4-113">Seçim</span><span class="sxs-lookup"><span data-stu-id="374e4-113">Select</span></span>|<span data-ttu-id="374e4-114">Bir dönüştürme işlevine dayalı projeler değerleri.</span><span class="sxs-lookup"><span data-stu-id="374e4-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="374e4-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="374e4-115">SelectMany</span></span>|<span data-ttu-id="374e4-116">Projeleri dizileri değeri bir dönüştürme işlevi üzerinde temel alır ve ardından bunları bir dizi düzleştirir.</span><span class="sxs-lookup"><span data-stu-id="374e4-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="374e4-117">Birden çok kullanın `from` yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="374e4-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="374e4-118">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="374e4-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="374e4-119">Seçim</span><span class="sxs-lookup"><span data-stu-id="374e4-119">Select</span></span>  
 <span data-ttu-id="374e4-120">Aşağıdaki örnekte `select` dizelerinin listesini her bir dizenin ilk harfinden projeye yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="374e4-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="374e4-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="374e4-121">SelectMany</span></span>  
 <span data-ttu-id="374e4-122">Aşağıdaki örnek, birden çok kullanır `from` her bir sözcüğü her bir dizenin bir dize listesi içinde proje için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="374e4-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="374e4-123">SelectMany karşı seçin</span><span class="sxs-lookup"><span data-stu-id="374e4-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="374e4-124">Hem iş `Select()` ve `SelectMany()` bir sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="374e4-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="374e4-125">`Select()` Her kaynak değeri için bir sonuç değerini veriyor.</span><span class="sxs-lookup"><span data-stu-id="374e4-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="374e4-126">Genel sonuç, bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon olur.</span><span class="sxs-lookup"><span data-stu-id="374e4-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="374e4-127">Buna karşılık, `SelectMany()` her bir kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="374e4-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="374e4-128">Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` numaralandırılabilir dizisi için her kaynak değeri değerlerinin döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="374e4-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="374e4-129">Bu numaralandırılabilir dizileri tarafından bitiştirilir `SelectMany()` büyük bir dizi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="374e4-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="374e4-130">Aşağıdaki iki çizimler eylemleri, bu iki yöntem arasındaki kavramsal farkı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="374e4-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="374e4-131">Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden satmanın dizisi seçer varsayılır.</span><span class="sxs-lookup"><span data-stu-id="374e4-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="374e4-132">Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="374e4-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="374e4-133">![Seçme eylemini kavramsal çizimi&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="374e4-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="374e4-134">Bu çizimde gösterilmektedir nasıl `SelectMany()` her ara diziden her değeri içeren bir sonuç değeri diziler Ara dizisine art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="374e4-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="374e4-135">![SelectMany eylemini gösteren grafik&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="374e4-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="374e4-136">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="374e4-136">Code Example</span></span>  
 <span data-ttu-id="374e4-137">Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="374e4-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="374e4-138">Bu kod, kaynak koleksiyonda çiçek adları her iki listesinden ilk iki öğeyi alarak çiçek "demeti" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="374e4-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="374e4-139">Bu örnekte, "değer tek" Bu dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanır, kendisi değerler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="374e4-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="374e4-140">Bu ek gerektirir `foreach` döngü, her alt dizideki her bir dizenin numaralandırmak için.</span><span class="sxs-lookup"><span data-stu-id="374e4-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="374e4-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="374e4-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="374e4-142">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="374e4-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="374e4-143">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="374e4-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
- [<span data-ttu-id="374e4-144">Nasıl yapılır: (LINQ) birden fazla kaynaktan nesne koleksiyonları doldurma (C#)</span><span class="sxs-lookup"><span data-stu-id="374e4-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="374e4-145">Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="374e4-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
