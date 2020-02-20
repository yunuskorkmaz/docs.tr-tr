---
title: Dizin Oluşturucular
description: Dizin oluşturucular C# ve bunların, bir veya daha fazla bağımsız değişken kullanılarak başvurulan özellikler olan dizinli özellikleri nasıl uygulayabileceği hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 966483e80d8dd0421dce1b7fabdb0d443d73a0fc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450888"
---
# <a name="indexers"></a><span data-ttu-id="7b108-103">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7b108-103">Indexers</span></span>

<span data-ttu-id="7b108-104">*Dizin oluşturucular* özelliklere benzerdir.</span><span class="sxs-lookup"><span data-stu-id="7b108-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="7b108-105">Birçok şekilde, Dizin oluşturucular [Özellikler](properties.md)ile aynı dil özelliklerinde yapı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b108-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="7b108-106">Dizin oluşturucular *dizinli* özellikleri etkinleştirir: bir veya daha fazla bağımsız değişken kullanılarak başvurulan Özellikler.</span><span class="sxs-lookup"><span data-stu-id="7b108-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="7b108-107">Bu bağımsız değişkenler, bazı değer toplamasına bir dizin sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b108-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="7b108-108">Dizin Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b108-108">Indexer Syntax</span></span>

<span data-ttu-id="7b108-109">Bir dizin oluşturucuya bir değişken adı ve köşeli ayraçlar aracılığıyla erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="7b108-110">Dizin Oluşturucu bağımsız değişkenlerini köşeli ayraç içine yerleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b108-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="7b108-111">Özellik adı olarak `this` anahtar sözcüğünü kullanarak Dizin oluşturucular bildirir ve bağımsız değişkenleri köşeli ayraç içinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="7b108-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="7b108-112">Bu bildirim, önceki paragrafta gösterilen kullanımla eşleşir:</span><span class="sxs-lookup"><span data-stu-id="7b108-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="7b108-113">Bu ilk örnekte, Özellikler ve Dizin oluşturucular için sözdizimi arasındaki ilişkiyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="7b108-114">Bu benzerleme vurguladı, Dizin oluşturucular için sözdizimi kurallarının çoğunu taşır.</span><span class="sxs-lookup"><span data-stu-id="7b108-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="7b108-115">Dizin oluşturucular geçerli erişim değiştiricilerine sahip olabilir (genel, korunan dahili, korunan, iç, özel veya özel korumalı).</span><span class="sxs-lookup"><span data-stu-id="7b108-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="7b108-116">Mühürlü, sanal veya soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b108-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="7b108-117">Özelliklerde olduğu gibi, bir dizin oluşturucuda get ve set erişimcileri için farklı erişim değiştiricileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="7b108-118">Salt yazılır Dizin oluşturucular da (set erişimcisini atlayarak) veya salt yazılır Dizin oluşturucular (Get erişimcisini atlayarak) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="7b108-119">Özelliklerle birlikte çalışarak, dizin oluşturucularının bulunduğu neredeyse her şeyi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="7b108-120">Bu kuralın tek istisnası *Otomatik uygulanan özelliklerdir*.</span><span class="sxs-lookup"><span data-stu-id="7b108-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="7b108-121">Derleyici, Dizin Oluşturucu için her zaman doğru depolama alanı oluşturamıyor.</span><span class="sxs-lookup"><span data-stu-id="7b108-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="7b108-122">Bir öğe kümesindeki bir öğeye başvuruda bulunmak için bağımsız değişkenlerin varlığı, dizin oluşturucularının özelliklerini ayırır.</span><span class="sxs-lookup"><span data-stu-id="7b108-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="7b108-123">Her bir dizin oluşturucunun bağımsız değişken listeleri benzersiz olduğu sürece, bir tür üzerinde birden çok Dizin Oluşturucu tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="7b108-124">Bir sınıf tanımında bir veya daha fazla Dizin Oluşturucu kullanabileceğiniz farklı senaryolar araştıralım.</span><span class="sxs-lookup"><span data-stu-id="7b108-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="7b108-125">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="7b108-125">Scenarios</span></span>

<span data-ttu-id="7b108-126">API 'sinin, bu koleksiyonun bağımsız değişkenlerini tanımladığınız bazı koleksiyonları modellediğinde, bu *Dizin* oluşturucuyu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b108-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="7b108-127">Dizin oluşturucular, .NET Core Framework 'ün parçası olan koleksiyon türleri ile doğrudan eşleşmeyebilir veya eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7b108-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="7b108-128">Bir koleksiyonun modellenmesi ek olarak, türü başka sorumluluklara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b108-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="7b108-129">Dizin oluşturucular, bu soyutlamalarda değerlerinin nasıl depolandığını veya hesaplanmadığını belirten iç ayrıntıları açığa çıkarmadan, türün soyutlamada eşleşen API 'yi sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7b108-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="7b108-130">*Dizin oluşturucular*kullanmanın bazı yaygın senaryolarından bazılarını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="7b108-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="7b108-131">[Dizin oluşturucular için örnek klasöre](https://github.com/dotnet/samples/tree/master/csharp/indexers)erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="7b108-132">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="7b108-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="7b108-133">Diziler ve vektörler</span><span class="sxs-lookup"><span data-stu-id="7b108-133">Arrays and Vectors</span></span>

<span data-ttu-id="7b108-134">Dizin oluşturucular oluşturmak için en yaygın senaryolardan biri, türü bir diziyi veya bir vektörü modellediğinde olur.</span><span class="sxs-lookup"><span data-stu-id="7b108-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="7b108-135">Sıralı bir veri listesini modellemek için bir Dizin Oluşturucu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="7b108-136">Kendi dizin oluşturucuyu oluşturmanın avantajı, bu koleksiyonun depolama alanını gereksinimlerinize uyacak şekilde tanımlayabilmeniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="7b108-137">Aynı anda belleğe yüklenecek çok büyük geçmiş verileri modelleyen bir senaryoyu düşünün.</span><span class="sxs-lookup"><span data-stu-id="7b108-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="7b108-138">Kullanım temelinde koleksiyonun bölümlerini yüklemeniz ve kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b108-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="7b108-139">Aşağıdaki örnek, bu davranışı modelleyen bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="7b108-139">The example following models this behavior.</span></span> <span data-ttu-id="7b108-140">Bu, kaç veri noktasının var olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7b108-140">It reports on how many data points exist.</span></span> <span data-ttu-id="7b108-141">İsteğe bağlı verilerin bölümlerini tutacak sayfalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b108-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="7b108-142">Daha yeni istekler için gereken sayfalar için yer açmak üzere sayfaları bellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7b108-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

<span data-ttu-id="7b108-143">Tüm veri kümesinin bellek içi bir koleksiyona yüklenmesinin iyi nedenleri olduğu durumlarda, herhangi bir koleksiyon sıralamasını modellemek için bu tasarım deyimlerini takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="7b108-144">`Page` sınıfının, ortak arabirimin parçası olmayan özel bir iç içe sınıf olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7b108-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="7b108-145">Bu ayrıntılar, bu sınıfın tüm kullanıcılarından gizlenir.</span><span class="sxs-lookup"><span data-stu-id="7b108-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="7b108-146">Sözlükler</span><span class="sxs-lookup"><span data-stu-id="7b108-146">Dictionaries</span></span>

<span data-ttu-id="7b108-147">Diğer bir yaygın senaryo, bir sözlüğü veya eşlemeyi modellemenize gerek duyduğunuzda olur.</span><span class="sxs-lookup"><span data-stu-id="7b108-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="7b108-148">Bu senaryo, yazdığınız değerleri anahtar temelinde, genellikle metin anahtarlarına göre depoladığında olur.</span><span class="sxs-lookup"><span data-stu-id="7b108-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="7b108-149">Bu örnek, komut satırı bağımsız değişkenlerini bu seçenekleri yöneten [lambda ifadelerine](delegates-overview.md) eşleyen bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b108-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="7b108-150">Aşağıdaki örnekte iki sınıf gösterilmektedir: bir komut satırı seçeneğini bir `Action` temsilcisine eşleyen `ArgsActions` sınıfı ve bu seçenekle karşılaştığında her `Action` yürütmek için `ArgsActions` kullanan bir `ArgsProcessor`.</span><span class="sxs-lookup"><span data-stu-id="7b108-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

<span data-ttu-id="7b108-151">Bu örnekte `ArgsAction` koleksiyonu, temel alınan koleksiyona yakından eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7b108-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="7b108-152">`get`, verilen bir seçeneğin yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7b108-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="7b108-153">Bu durumda, bu seçenekle ilişkili `Action` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b108-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="7b108-154">Aksi takdirde, hiçbir şey olmayan bir `Action` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b108-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="7b108-155">Ortak erişimci bir `set` erişimcisi içermez.</span><span class="sxs-lookup"><span data-stu-id="7b108-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="7b108-156">Bunun yerine, seçenekleri ayarlamak için genel bir yöntem kullanan tasarım.</span><span class="sxs-lookup"><span data-stu-id="7b108-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="7b108-157">Çok boyutlu haritalar</span><span class="sxs-lookup"><span data-stu-id="7b108-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="7b108-158">Birden çok bağımsız değişken kullanan Dizin oluşturucular oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b108-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="7b108-159">Ayrıca, bu bağımsız değişkenler aynı türde olacak şekilde kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="7b108-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="7b108-160">İki örneğe bakalım.</span><span class="sxs-lookup"><span data-stu-id="7b108-160">Let's look at two examples.</span></span>   

<span data-ttu-id="7b108-161">İlk örnek, bir Mandeli kümesi için değerler üreten bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b108-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="7b108-162">Küme arkasında matematik hakkında daha fazla bilgi için [Bu makaleyi](https://en.wikipedia.org/wiki/Mandelbrot_set)okuyun.</span><span class="sxs-lookup"><span data-stu-id="7b108-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="7b108-163">Dizin Oluşturucu X, Y düzleinde bir noktayı tanımlamak için iki Double Double kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b108-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="7b108-164">Get erişimcisi, bir noktanın küme içinde olmadığı belirlenene kadar yineleme sayısını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7b108-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="7b108-165">En fazla yineleme ulaşılırsa, nokta ayarlanmıştır ve sınıfın Maxyinelemelerde değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7b108-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="7b108-166">(Bilgisayar tarafından üretilen görüntüler Mandeli kümesi için populartı kümesi, bir noktanın kümenin dışında olduğunu belirlemek için gereken yineleme sayısı için renkleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b108-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

<span data-ttu-id="7b108-167">Mandelbrot kümesi, gerçek sayı değerleri için her (x, y) koordinatının değerlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b108-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="7b108-168">Bu, sonsuz sayıda değer içerebilen bir sözlük tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b108-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="7b108-169">Bu nedenle, küme arkasında depolama yok.</span><span class="sxs-lookup"><span data-stu-id="7b108-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="7b108-170">Bunun yerine, kod `get` erişimcisini çağırdığında, bu sınıf her bir noktanın değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7b108-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="7b108-171">Kullanılan temeldeki depolama alanı yok.</span><span class="sxs-lookup"><span data-stu-id="7b108-171">There's no underlying storage used.</span></span>

<span data-ttu-id="7b108-172">Dizin oluşturucunun, farklı türlerde birden çok bağımsız değişken aldığı dizin oluşturucularının bir son kullanımını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="7b108-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="7b108-173">Geçmiş sıcaklık verilerini yöneten bir programı düşünün.</span><span class="sxs-lookup"><span data-stu-id="7b108-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="7b108-174">Bu Dizin Oluşturucu, bu konum için yüksek ve düşük sıcaklıkları ayarlamak veya almak üzere bir şehir ve bir tarih kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b108-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

```csharp
using DateMeasurements = 
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = 
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

<span data-ttu-id="7b108-175">Bu örnek, hava durumu verilerini iki farklı bağımsız değişkenle eşleyen bir dizin oluşturucu oluşturur: bir şehir (bir `string`tarafından temsil edilir) ve Tarih (bir `DateTime`tarafından temsil edilir).</span><span class="sxs-lookup"><span data-stu-id="7b108-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="7b108-176">İç depolama iki boyutlu sözlüğü temsil etmek için iki `Dictionary` sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b108-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="7b108-177">Ortak API artık temeldeki depolamayı temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b108-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="7b108-178">Bunun yerine, dizin oluşturucularının dil özellikleri, temeldeki depolamanın farklı çekirdek koleksiyon türlerini kullanması gerekir ancak, soyutlamasını temsil eden bir ortak arabirim oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b108-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="7b108-179">Bu kodun, bazı geliştiricilere alışkın olabilecek iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="7b108-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="7b108-180">Bu iki `using` deyimi:</span><span class="sxs-lookup"><span data-stu-id="7b108-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="7b108-181">oluşturulan genel tür için bir *diğer ad* oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b108-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="7b108-182">Bu deyimler daha sonra kodu daha sonra `Dictionary<DateTime, Measurements>` ve `Dictionary<string, Dictionary<DateTime, Measurements> >`genel yapımı yerine daha açıklayıcı `DateMeasurements` ve `CityDateMeasurements` adlarını kullanacak şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7b108-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="7b108-183">Bu yapı, `=` işaretinin sağ tarafında tam nitelikli tür adlarının kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b108-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="7b108-184">İkinci yöntem, koleksiyonlara dizin eklemek için kullanılan herhangi bir `DateTime` nesnesinin zaman kısımlarını bir kez çıkaramadır.</span><span class="sxs-lookup"><span data-stu-id="7b108-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="7b108-185">.NET yalnızca Tarih türünde bir tür içermez.</span><span class="sxs-lookup"><span data-stu-id="7b108-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="7b108-186">Geliştiriciler `DateTime` türünü kullanır, ancak bu gündeki herhangi bir `DateTime` nesnesinin eşit olduğundan emin olmak için `Date` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b108-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="7b108-187">Toplam</span><span class="sxs-lookup"><span data-stu-id="7b108-187">Summing Up</span></span>

<span data-ttu-id="7b108-188">Sınıfınıza, bu özelliğin tek bir değer değil, her tekil öğenin bir dizi bağımsız değişken tarafından tanımlandığı bir değer koleksiyonu olmak üzere her zaman bir özellik benzeri öğe oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b108-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="7b108-189">Bu bağımsız değişkenler koleksiyondaki hangi öğeye başvurulduğunu benzersiz şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7b108-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="7b108-190">Dizin oluşturucular, bir üyenin sınıfın dışından bir veri öğesi gibi davranılabileceği, ancak içindeki bir yöntem gibi ele alındığı [Özellikler](properties.md)kavramını genişletir.</span><span class="sxs-lookup"><span data-stu-id="7b108-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="7b108-191">Dizin oluşturucular, bağımsız değişkenlerin bir öğe kümesini temsil eden özellikte tek bir öğe bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7b108-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
