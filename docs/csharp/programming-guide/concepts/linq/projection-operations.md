---
title: Projeksiyon Işlemleri (C#)
description: Projeksiyon işlemleri hakkında bilgi edinin. Bu işlemler, genellikle yalnızca daha sonra kullanılacak özelliklerden oluşan yeni bir forma nesne dönüştürür.
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 289100ac9afcfc0d5b93b5f963adc0a123e0a5af
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299168"
---
# <a name="projection-operations-c"></a><span data-ttu-id="196bf-104">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="196bf-104">Projection Operations (C#)</span></span>
<span data-ttu-id="196bf-105">Projeksiyon, bir nesneyi genellikle daha sonra kullanılacak olan özelliklerden oluşan yeni bir forma dönüştürme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="196bf-105">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="196bf-106">Projeksiyonu kullanarak her nesneden oluşturulan yeni bir tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="196bf-106">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="196bf-107">Bir özelliği proje üzerinde bir matematik işlevi de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="196bf-107">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="196bf-108">Özgün nesneyi değiştirmeden de proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="196bf-108">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="196bf-109">Yansıtmayı gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="196bf-109">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="196bf-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="196bf-110">Methods</span></span>  
  
|<span data-ttu-id="196bf-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="196bf-111">Method Name</span></span>|<span data-ttu-id="196bf-112">Description</span><span class="sxs-lookup"><span data-stu-id="196bf-112">Description</span></span>|<span data-ttu-id="196bf-113">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="196bf-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="196bf-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="196bf-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="196bf-115">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="196bf-115">Select</span></span>|<span data-ttu-id="196bf-116">Bir dönüşüm işlevine dayalı projeler değerleri.</span><span class="sxs-lookup"><span data-stu-id="196bf-116">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="196bf-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="196bf-117">SelectMany</span></span>|<span data-ttu-id="196bf-118">Bir dönüşüm işlevine dayalı ve sonra bunları tek bir sırayla düzleştirir.</span><span class="sxs-lookup"><span data-stu-id="196bf-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="196bf-119">Birden çok `from` yan tümce kullanma</span><span class="sxs-lookup"><span data-stu-id="196bf-119">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="196bf-120">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="196bf-120">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="196bf-121">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="196bf-121">Select</span></span>  
 <span data-ttu-id="196bf-122">Aşağıdaki örnek, `select` bir dize listesindeki her bir dizeden ilk harfi proje için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="196bf-122">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="196bf-123">SelectMany</span><span class="sxs-lookup"><span data-stu-id="196bf-123">SelectMany</span></span>  
 <span data-ttu-id="196bf-124">Aşağıdaki örnek, `from` her bir sözcüğü bir dize listesindeki her bir dizeden proje için birden çok yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="196bf-124">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="196bf-125">Select SelectMany</span><span class="sxs-lookup"><span data-stu-id="196bf-125">Select versus SelectMany</span></span>  
 <span data-ttu-id="196bf-126">Her ikisinin de işi `Select()` , `SelectMany()` kaynak değerlerinden bir sonuç değeri (veya değerler) üretmeniz.</span><span class="sxs-lookup"><span data-stu-id="196bf-126">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="196bf-127">`Select()`Her kaynak değer için bir sonuç değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="196bf-127">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="196bf-128">Bu nedenle, genel sonuç, kaynak koleksiyonuyla aynı sayıda öğeye sahip olan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="196bf-128">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="196bf-129">Buna karşılık, `SelectMany()` her kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="196bf-129">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="196bf-130">Bağımsız değişken olarak geçirilen dönüştürme işlevinin `SelectMany()` her kaynak değer için sıralanabilir bir değer dizisi döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="196bf-130">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="196bf-131">Bu sıralanabilir sıralar daha sonra `SelectMany()` bir büyük sıra oluşturmak için ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="196bf-131">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="196bf-132">Aşağıdaki iki çizimde, bu iki yöntemin eylemleri arasındaki kavramsal fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="196bf-132">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="196bf-133">Her durumda, seçici (dönüşüm) işlevinin her kaynak değerden çiçekler dizisini seçtiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="196bf-133">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="196bf-134">Bu çizimde, `Select()` kaynak koleksiyonuyla aynı sayıda öğeye sahip bir koleksiyonun nasıl döndürdüğü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="196bf-134">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Select&#40;&#41; eylemini gösteren grafik](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="196bf-136">Bu çizimde `SelectMany()` , dizi dizilerinin her bir ara dizideki her bir değeri içeren bir son sonuç değerine nasıl sıralanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="196bf-136">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![SelectMany&#40;&#41; eylemini gösteren grafik.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="196bf-138">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="196bf-138">Code Example</span></span>  
 <span data-ttu-id="196bf-139">Aşağıdaki örnek, ve davranışlarını karşılaştırır `Select()` `SelectMany()` .</span><span class="sxs-lookup"><span data-stu-id="196bf-139">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="196bf-140">Kod, kaynak koleksiyondaki her bir çiçek adı listesinden ilk iki öğeyi alarak çiçekler ' ın bir "Buquet" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="196bf-140">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="196bf-141">Bu örnekte, Transform işlevinin kullandığı "tek değer" değeri <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> bir değer koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="196bf-141">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="196bf-142">Bu, her bir `foreach` alt dizideki her bir dizeyi numaralandırmak için ek döngü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="196bf-142">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="196bf-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="196bf-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="196bf-144">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="196bf-144">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="196bf-145">select tümcesi</span><span class="sxs-lookup"><span data-stu-id="196bf-145">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="196bf-146">Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="196bf-146">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="196bf-147">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="196bf-147">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
