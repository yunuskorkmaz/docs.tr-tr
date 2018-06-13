---
title: Projeksiyon işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a044982c21246fd4e8c1cbdbb9801ae7b29d05c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335396"
---
# <a name="projection-operations-c"></a><span data-ttu-id="6e852-102">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="6e852-102">Projection Operations (C#)</span></span>
<span data-ttu-id="6e852-103">Projeksiyon genellikle daha sonra kullanılacak bu özelliklerini içeren yeni bir forma bir nesne dönüştürme işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6e852-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="6e852-104">Projeksiyon kullanarak her nesneden oluşturulmuş yeni bir türü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e852-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="6e852-105">Bir özellik proje ve matematiksel işlevi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6e852-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="6e852-106">Özgün nesne değiştirmeden da yansıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e852-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="6e852-107">Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e852-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e852-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e852-108">Methods</span></span>  
  
|<span data-ttu-id="6e852-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="6e852-109">Method Name</span></span>|<span data-ttu-id="6e852-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e852-110">Description</span></span>|<span data-ttu-id="6e852-111">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e852-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="6e852-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6e852-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6e852-113">Seçim</span><span class="sxs-lookup"><span data-stu-id="6e852-113">Select</span></span>|<span data-ttu-id="6e852-114">Bir dönüştürme işlevine dayalı projeleri değerleri.</span><span class="sxs-lookup"><span data-stu-id="6e852-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6e852-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="6e852-115">SelectMany</span></span>|<span data-ttu-id="6e852-116">Dönüşüm işlevi üzerinde temel alır ve bunları bir sıralı düzleştirir değerler projeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="6e852-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="6e852-117">Birden çok kullanmak `from` yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="6e852-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6e852-118">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="6e852-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="6e852-119">Seçim</span><span class="sxs-lookup"><span data-stu-id="6e852-119">Select</span></span>  
 <span data-ttu-id="6e852-120">Aşağıdaki örnek kullanır `select` dizelerinin listesini her dizesinde ilk harfinden projeye yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6e852-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="6e852-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="6e852-121">SelectMany</span></span>  
 <span data-ttu-id="6e852-122">Aşağıdaki örnek, birden çok kullanır `from` dizelerinin listesini her bir dizeden her sözcüğün projeye yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="6e852-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="6e852-123">SelectMany karşı seçin</span><span class="sxs-lookup"><span data-stu-id="6e852-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="6e852-124">Hem iş `Select()` ve `SelectMany()` sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="6e852-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="6e852-125">`Select()` Her kaynak değeri için bir sonuç değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e852-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="6e852-126">Genel sonuç bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="6e852-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="6e852-127">Buna karşılık, `SelectMany()` her kaynak değerinden birleştirilmiş alt koleksiyonları içeren tek bir genel sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="6e852-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="6e852-128">Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` değerleri her bir kaynak değer için numaralandırılabilir bir dizi döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e852-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="6e852-129">Bu numaralandırılabilir sıralarının tarafından birleşir `SelectMany()` bir büyük sıralı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6e852-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="6e852-130">Aşağıdaki iki çizimler bu iki yöntem Eylemler kavramsal birbirinden göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e852-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="6e852-131">Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden çiçekler dizisi seçer varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6e852-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="6e852-132">Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e852-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="6e852-133">![Select eylem kavramsal çizimi&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="6e852-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="6e852-134">Bu çizimde gösterilmektedir nasıl `SelectMany()` diziler ara sıra her ara dizisinden her değeri içeren bir sonuç değeri içine art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="6e852-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="6e852-135">![SelectMany eylemini gösteren grafik&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="6e852-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="6e852-136">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="6e852-136">Code Example</span></span>  
 <span data-ttu-id="6e852-137">Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="6e852-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="6e852-138">Kaynak koleksiyondaki her çiçek adları listesinden ilk iki öğenin gerçekleştirerek çiçek "demeti" kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e852-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="6e852-139">Bu örnekte, "tek değer", dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanımdır kendisini değerler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6e852-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="6e852-140">Bu ek gerektirir `foreach` her alt dizisindeki her dize numaralandırmak için döngü.</span><span class="sxs-lookup"><span data-stu-id="6e852-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e852-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e852-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6e852-142">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="6e852-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="6e852-143">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="6e852-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="6e852-144">Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma</span><span class="sxs-lookup"><span data-stu-id="6e852-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="6e852-145">Nasıl yapılır: bir dosya grupları (LINQ) (C#) kullanarak birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="6e852-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
