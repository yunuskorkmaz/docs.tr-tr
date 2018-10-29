---
title: Dizin Oluşturucular
description: Hakkında bilgi edinin C# dizin oluşturucular ve nasıl uyguladıkları dizin oluşturulmuş başvurulan bir veya daha fazla bağımsız değişken kullanarak özellikleri olan özellikleri.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197606"
---
# <a name="indexers"></a><span data-ttu-id="7ab4f-103">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7ab4f-103">Indexers</span></span>

<span data-ttu-id="7ab4f-104">*Dizin oluşturucular* özelliklerine benzer.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="7ab4f-105">Dizin oluşturucular birçok yolla aynı dil özellikleri oluşturmak [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="7ab4f-106">Etkinleştir Dizinleyicileri *dizine* özellikleri: bir veya daha fazla bağımsız değişken kullanarak başvurulan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="7ab4f-107">Bu bağımsız değişkenlerden bazı değerler koleksiyonu içinde bir dizin sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="7ab4f-108">Dizin Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ab4f-108">Indexer Syntax</span></span>

<span data-ttu-id="7ab4f-109">Bir dizin oluşturucu, bir değişken adı ve köşeli ayraçlar erişin.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="7ab4f-110">Dizin oluşturucu bağımsız değişkenleri köşeli ayraçlar içine yerleştirdiğiniz:</span><span class="sxs-lookup"><span data-stu-id="7ab4f-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="7ab4f-111">Dizin oluşturucular kullanarak bildirdiğiniz `this` özellik adı ve bağımsız değişkenler köşeli ayraç içinde bildirme as anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="7ab4f-112">Bu bildirim önceki paragrafta gösterilen kullanım eşleşmesi:</span><span class="sxs-lookup"><span data-stu-id="7ab4f-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="7ab4f-113">Bu ilk örnekte, dizin oluşturucular ve özellikler için söz dizimi arasındaki ilişkiyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="7ab4f-114">Çoğu dizin oluşturucular için söz dizimi kuralın aracılığıyla bu benzerleme taşır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="7ab4f-115">Dizin Oluşturucular, herhangi bir geçerli erişim değiştiricileri olabilir (Genel, korumalı korumalı iç, korumalı, dahili, özel veya özel).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="7ab4f-116">Bunlar, korumalı, virtual veya abstract olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="7ab4f-117">Özellikleriyle yönteminde olduğu gibi get için farklı erişim değiştiricileri belirtmeniz ve set erişimcileri bir dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="7ab4f-118">(Set erişimcisine atlama tarafından) salt okunur dizin oluşturucuları veya salt yazılır dizin oluşturucular (get erişimcisine gt;(yok)) de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="7ab4f-119">Hemen dizin oluşturucular özelliklere ile çalışmaktan şunların her şeyi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="7ab4f-120">Bu kuralın tek özel durum *otomatik uygulanan Özellikler*.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="7ab4f-121">Derleyici, her zaman doğru depolama dizin oluşturucu için oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="7ab4f-122">Öğelerin kümesi bir öğeye başvuru için bağımsız değişken varlığını dizin oluşturucular özelliklerinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="7ab4f-123">Her dizin oluşturucu benzersiz için bağımsız değişken listeleri sürece bir tür üzerinde birden çok dizin oluşturucu tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="7ab4f-124">Bir veya daha fazla dizin oluşturucular sınıf tanımında burada kullanabileceğinize farklı senaryolar araştıralım.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="7ab4f-125">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="7ab4f-125">Scenarios</span></span>

<span data-ttu-id="7ab4f-126">Tanımlayın *dizin oluşturucular* API'SİYLE burada tanımlarsınız bağımsız değişkenler bu koleksiyon için bazı koleksiyon modellediğinde, türü.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="7ab4f-127">Dizin oluşturucular olabilir veya .NET core framework parçası olan doğrudan koleksiyon türlerine eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="7ab4f-128">Türünüzün bir koleksiyon modelleme yanı sıra diğer sorumlulukları olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="7ab4f-129">Dizin oluşturucular bu soyutlama değerlerini nasıl depolanan veya hesaplanan iç ayrıntılarını sokmadan, türün Özet eşleşen API'si sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="7ab4f-130">Şimdi kullanmaya yönelik yaygın senaryolardan bazıları yol *dizin oluşturucular*.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="7ab4f-131">Erişebildiğiniz [örnek klasörüne dizin oluşturucular için](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="7ab4f-132">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="7ab4f-133">Diziler ve vektörleri</span><span class="sxs-lookup"><span data-stu-id="7ab4f-133">Arrays and Vectors</span></span>

<span data-ttu-id="7ab4f-134">Türünüzün bir dizi veya bir vektör modellediğinde dizin oluşturucular oluşturmak için en sık karşılaşılan senaryolardan biridir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="7ab4f-135">Model verileri sıralı bir listesi için bir dizin oluşturucu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="7ab4f-136">Kendi dizin oluşturucu oluşturma avantajı, depolama ihtiyaçlarınıza uyacak şekilde bu koleksiyon için tanımlayabileceğiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="7ab4f-137">Burada türünüzü tek seferde belleğe yüklemek için çok büyük geçmiş veri modelleri bir senaryo düşünün.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="7ab4f-138">Yükleme ve kaldırma kullanımını temel alarak koleksiyon bölümlerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="7ab4f-139">Bu davranışı aşağıdaki örneğe modeller.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-139">The example following models this behavior.</span></span> <span data-ttu-id="7ab4f-140">Kaç tane veri noktalarının mevcut üzerinde rapor.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-140">It reports on how many data points exist.</span></span> <span data-ttu-id="7ab4f-141">Verilerin isteğe bağlı olarak bölümlerde tutacak sayfaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="7ab4f-142">Tarafından daha yeni istekler gerekeceğinden sayfaları için yer açmak için bellek sayfaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="7ab4f-143">Bu tasarım deyim herhangi bir tür koleksiyonun modellemek için izleyebileceğiniz bulunduğu veri kümesinin tamamını bir bellek içi koleksiyona yüklemeyecek için iyi nedenler vardır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="7ab4f-144">Dikkat `Page` ortak arabiriminin bir parçası değil özel, iç içe geçmiş bir sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="7ab4f-145">Bu ayrıntılar, bu sınıfın tüm kullanıcılardan gizlenir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="7ab4f-146">sözlükler</span><span class="sxs-lookup"><span data-stu-id="7ab4f-146">Dictionaries</span></span>

<span data-ttu-id="7ab4f-147">Bir sözlüğün veya bir map model gerektiğinde başka bir yaygın senaryodur.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="7ab4f-148">Bu senaryo genellikle metin anahtarları anahtarını temel alan değerleri türünüz depolar andır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="7ab4f-149">Bu örnek komut satırı bağımsız değişkenleri eşleyen sözlük oluşturur [lambda ifadeleri](delegates-overview.md) bu seçenekleri yönetin.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="7ab4f-150">Aşağıdaki örnek, iki sınıf gösterir: bir `ArgsActions` eşleyen bir komut satırı seçeneğini sınıfı bir `Action` temsilcisi ve bir `ArgsProcessor` kullanan `ArgsActions` her yürütülecek `Action` seçeneği karşılaştığında.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="7ab4f-151">Bu örnekte, `ArgsAction` koleksiyon temel toplulukta yakından eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="7ab4f-152">`get` Belirli bir seçenek yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="7ab4f-153">Bu nedenle, döndürürse, `Action` bu seçenek ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="7ab4f-154">Değilse, döndürürse, bir `Action` hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="7ab4f-155">Genel erişimci içermemesi bir `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="7ab4f-156">Bunun yerine, seçeneklerini ayarlama için genel bir yöntem kullanılarak tasarım.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="7ab4f-157">Çok boyutlu eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="7ab4f-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="7ab4f-158">Birden çok bağımsız değişkenler kullanan dizin oluşturucular oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="7ab4f-159">Ayrıca, bu bağımsız değişkenler aynı türde olacak şekilde kısıtlanır değil.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="7ab4f-160">İki örneklere göz atalım.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-160">Let's look at two examples.</span></span>   

<span data-ttu-id="7ab4f-161">İlk örnek için Mandelbrot değerleri üreten bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="7ab4f-162">Matematik arkasında kümesi hakkında daha fazla bilgi için okuma [bu makalede](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="7ab4f-163">Dizin Oluşturucu iki çiftten X, bir noktayı tanımlamak için kullanır. Y düzlemleriyle.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="7ab4f-164">Bir nokta kümesinde olmadığı belirlenir kadar get erişimcisine yineleme sayısını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="7ab4f-165">En fazla yineleme ulaşıldığında, kümede noktasıdır ve sınıfın maxIterations değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="7ab4f-166">(Mandelbrot kümesi için popüler bilgisayar tarafından oluşturulan görüntüleri bir nokta kümesi dışında olduğunu belirlemek gerekli olan yineleme sayısı için renk tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="7ab4f-167">Değerlerinde Mandelbrot tanımlar her (x, y) için gerçek sayı değerlerini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="7ab4f-168">Bu değerleri sonsuz sayıda içerebilen bir sözlüğü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="7ab4f-169">Bu nedenle, hiçbir depolama kümesi arkasında yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="7ab4f-170">Bunun yerine, kodu çağırdığında bu sınıfın her bir noktası değerini hesaplar `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="7ab4f-171">Temel alınan depolama alanı kullanılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-171">There's no underlying storage used.</span></span>

<span data-ttu-id="7ab4f-172">Dizin oluşturucular için burada dizin oluşturucuyu farklı türlerde birden çok bağımsız değişkeni alır, bir son kullanımını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="7ab4f-173">Geçmiş sıcaklık verileri yöneten bir program göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="7ab4f-174">Bu dizin oluşturucu ayarlayın veya bu konumda için yüksek ve düşük Sıcaklıkların almak için bir şehir ve bir tarih kullanır:</span><span class="sxs-lookup"><span data-stu-id="7ab4f-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="7ab4f-175">Bu örnek, iki farklı bağımsız değişken hava durumu verilerine eşleyen bir dizin oluşturur: Bir şehrin (tarafından temsil edilen bir `string`) ve bir tarihi (tarafından temsil edilen bir `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="7ab4f-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="7ab4f-176">İki iç depolama kullanan `Dictionary` sınıflar için iki boyutlu sözlüğünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="7ab4f-177">Genel API, temel alınan depolama artık temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="7ab4f-178">Bunun yerine, dizin oluşturucular dil özelliklerinin temel alınan depolama farklı çekirdek koleksiyon türleri kullanmalısınız olsa bile, soyutlamayı temsil eder bir ortak arabirim oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="7ab4f-179">Bazı geliştiriciler için tanınmayan bu kod, iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="7ab4f-180">Bu iki `using` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="7ab4f-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="7ab4f-181">oluşturma bir *diğer* için oluşturulmuş bir genel türü.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="7ab4f-182">Bu ifadeler, daha sonra daha açıklayıcı kullanmak için kodu sağlar `DateMeasurements` ve `CityDateMeasurements` adları yerine genel oluşumu `Dictionary<DateTime, Measurements>` ve `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="7ab4f-183">Tento konstruktor je sağ tarafında tam olarak nitelenmiş tür adlarını kullanarak gerektiren `=` oturum.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="7ab4f-184">İkinci yöntem zaman bölümlerini herhangi Şerit göstermektir `DateTime` kullanılan nesne koleksiyonlara dizin.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="7ab4f-185">.NET framework yalnızca tarih türü içermez.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-185">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="7ab4f-186">Geliştiricilerin `DateTime` yazın, ancak kullanmak `Date` herhangi emin olmak için özellik `DateTime` o gün nesneden eşit.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="7ab4f-187">Özetle</span><span class="sxs-lookup"><span data-stu-id="7ab4f-187">Summing Up</span></span>

<span data-ttu-id="7ab4f-188">Sınıfınızdaki bu özellik tek bir değer değil, ancak bunun yerine her bir öğe tarafından bağımsız değişken kümesinin burada tanımlanan değerleri koleksiyonunu temsil ettiği bir özellik benzeri öğesine sahip herhangi bir zamanda, dizin oluşturucular oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="7ab4f-189">Bu bağımsız değişkenlerden hangi öğe koleksiyonda başvurulan benzersiz şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="7ab4f-190">Dizin oluşturucular genişletmek kavramını [özellikleri](properties.md), sınıf dışında bir veri öğesi gibi ancak tarafındaki bir yöntemi gibi bir üye olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="7ab4f-191">Dizin oluşturucular bir öğe kümesini temsil eden bir özelliği tek bir öğeyi bulmak bağımsız değişkenler izin verir.</span><span class="sxs-lookup"><span data-stu-id="7ab4f-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
