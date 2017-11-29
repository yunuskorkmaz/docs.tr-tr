---
title: "Dizin Oluşturucular"
description: "C# dizin oluşturucular ve bir veya daha fazla bağımsız değişken kullanarak başvurulan özelliklerdir Dizinli Özellikler nasıl uyguladıkları hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 32e090524f414ef93b8481a8ad356b313191d8b9
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2017
---
# <a name="indexers"></a><span data-ttu-id="09bed-104">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="09bed-104">Indexers</span></span>

<span data-ttu-id="09bed-105">*Dizin oluşturucular* özelliklerine benzer.</span><span class="sxs-lookup"><span data-stu-id="09bed-105">*Indexers* are similar to properties.</span></span> <span data-ttu-id="09bed-106">Dizin oluşturucular birçok yolla aynı dil özellikleri oluşturmak [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="09bed-106">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="09bed-107">Dizin oluşturucular etkinleştirmek *dizine* özellikleri: bağımsız değişkenlerden biri veya daha fazla kullanarak başvurulan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="09bed-107">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="09bed-108">Bu bağımsız değişkenlerden bazı değerleri koleksiyona bir dizin sağlayın.</span><span class="sxs-lookup"><span data-stu-id="09bed-108">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="09bed-109">Dizin Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09bed-109">Indexer Syntax</span></span>

<span data-ttu-id="09bed-110">Bir dizin oluşturucu, değişken adı ve köşeli erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09bed-110">You access an indexer through a variable name and square brackets .</span></span> <span data-ttu-id="09bed-111">Dizin oluşturucu bağımsız değişkenleri köşeli ayraçlar içinde koyun:</span><span class="sxs-lookup"><span data-stu-id="09bed-111">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="09bed-112">Dizin oluşturucular kullanma bildirme `this` özellik adı ve bağımsız değişkenleri köşeli ayraçlar içinde bildirme as anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="09bed-112">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="09bed-113">Bu bildirim önceki paragrafta gösterilen kullanım eşleşir:</span><span class="sxs-lookup"><span data-stu-id="09bed-113">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="09bed-114">Bu ilk örnekten özellikler ve dizin oluşturucular için söz dizimi arasındaki ilişkiyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09bed-114">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="09bed-115">Dizin oluşturucular sözdizimi kurallarına çoğunu aracılığıyla bu benzerleme taşır.</span><span class="sxs-lookup"><span data-stu-id="09bed-115">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="09bed-116">Dizin Oluşturucular, tüm geçerli erişim değiştiricileri olabilir (Genel, korumalı korumalı iç, korumalı, iç, özel veya özel).</span><span class="sxs-lookup"><span data-stu-id="09bed-116">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="09bed-117">Bunlar, korumalı, sanal ya da soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-117">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="09bed-118">Özellikleriyle olduğu gibi get için farklı erişim değiştiricileri belirtin ve accesssors bir dizin oluşturucu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09bed-118">As with properties, you can specify different access modifiers for the get and set accesssors in an indexer.</span></span>
<span data-ttu-id="09bed-119">(Tarafından set erişimcisine atlayarak) salt okunur dizin oluşturucuları ya da salt yazılır dizin oluşturucular (get erişimcisine kaldırarak) de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-119">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="09bed-120">Neredeyse her dizin oluşturucular için özellikler ile çalışma hakkında bilgi edineceksiniz uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09bed-120">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="09bed-121">Bu kuralın tek özel durum *otomatik uygulanan Özellikler*.</span><span class="sxs-lookup"><span data-stu-id="09bed-121">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="09bed-122">Derleyici her zaman bir dizin oluşturucu için doğru depolama oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="09bed-122">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="09bed-123">Bir öğeyi öğeleri kümesi başvurmak için bağımsız değişken varlığını dizin oluşturucular özelliklerinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="09bed-123">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="09bed-124">Her dizin oluşturucu benzersiz için bağımsız değişken listeleri sürece bir tür üzerinde birden çok dizin oluşturucu tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-124">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="09bed-125">Burada bir sınıf tanımı'nda bir veya daha fazla dizin oluşturucular kullanabilir farklı senaryolar inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="09bed-125">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="09bed-126">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="09bed-126">Scenarios</span></span>

<span data-ttu-id="09bed-127">Tanımlayın *dizin oluşturucular* API'si tanımladığınız bağımsız değişkenler bu koleksiyon için bazı koleksiyonu modellediğinde, yazın.</span><span class="sxs-lookup"><span data-stu-id="09bed-127">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="09bed-128">Dizin oluşturucular olabilir veya doğrudan .NET core framework parçası olan koleksiyon türleri için eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-128">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="09bed-129">Bir koleksiyon modelleme yanı sıra diğer sorumlulukları türünüz olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-129">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="09bed-130">Dizin oluşturucular bu soyutlama değerlerini nasıl depolanır veya hesaplanan iç ayrıntılarını sokmadan türünüz ait Özet eşleşen API sağlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="09bed-130">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="09bed-131">Şimdi kullanmaya yönelik yaygın senaryolardan bazıları rehberlik *dizin oluşturucular*.</span><span class="sxs-lookup"><span data-stu-id="09bed-131">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="09bed-132">Erişebileceğiniz [dizin oluşturucular için örnek klasör](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="09bed-132">You can access the [sample folder for indexers](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers).</span></span> <span data-ttu-id="09bed-133">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="09bed-133">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="09bed-134">Diziler ve vektörler</span><span class="sxs-lookup"><span data-stu-id="09bed-134">Arrays and Vectors</span></span>

<span data-ttu-id="09bed-135">Dizin oluşturucular oluşturmak için en sık karşılaşılan senaryolardan biri, durum, bir dizi veya bir vektör türünüz modeller durumdur.</span><span class="sxs-lookup"><span data-stu-id="09bed-135">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="09bed-136">Model veri sıralı bir listesi için bir dizin oluşturucu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09bed-136">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="09bed-137">Kendi dizin oluşturucu oluşturma avantajı, gereksinimlerinize uygun olarak bu koleksiyon için depolama tanımlayabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="09bed-137">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="09bed-138">Burada türünüz belleğe aynı anda yüklemek için çok büyük geçmiş veri modelleri bir senaryoyu düşünün.</span><span class="sxs-lookup"><span data-stu-id="09bed-138">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="09bed-139">Yükleme ve kaldırma bölümlerini kullanıma dayalı koleksiyon gerekir.</span><span class="sxs-lookup"><span data-stu-id="09bed-139">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="09bed-140">Aşağıdaki örneğe bu davranışını modeller.</span><span class="sxs-lookup"><span data-stu-id="09bed-140">The example following models this behavior.</span></span> <span data-ttu-id="09bed-141">Bu, kaç tane veri noktalarını mevcut raporlar.</span><span class="sxs-lookup"><span data-stu-id="09bed-141">It reports on how many data points exist.</span></span> <span data-ttu-id="09bed-142">İstek üzerine veri bölümlerini tutmak için sayfaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09bed-142">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="09bed-143">Daha yeni istekleri tarafından gerekli sayfaları için yer açmak için bellek sayfaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09bed-143">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="09bed-144">Koleksiyon her tür model oluşturmak için bu tasarım deyim izleyebilirsiniz veri kümesinin tamamını bir bellek içi koleksiyona yüklenmemesine için iyi neden olduğu.</span><span class="sxs-lookup"><span data-stu-id="09bed-144">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="09bed-145">Dikkat `Page` ortak arabirimi parçası olmayan özel bir iç içe geçmiş sınıf bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="09bed-145">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="09bed-146">Bu ayrıntılar, bu sınıfın tüm kullanıcılardan gizlenir.</span><span class="sxs-lookup"><span data-stu-id="09bed-146">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="09bed-147">Sözlük</span><span class="sxs-lookup"><span data-stu-id="09bed-147">Dictionaries</span></span>

<span data-ttu-id="09bed-148">Bir sözlük veya bir harita model gerektiğinde başka bir yaygın senaryodur.</span><span class="sxs-lookup"><span data-stu-id="09bed-148">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="09bed-149">Bu senaryo, anahtarı, genellikle metnin anahtarları temel değerleri türünüz depolayan durumdur.</span><span class="sxs-lookup"><span data-stu-id="09bed-149">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="09bed-150">Bu örnek komut satırı bağımsız değişkenleri için eşleşen bir sözlük oluşturur [lamdba ifadeleri](delegates-overview.md) bu seçenekleri yönetin.</span><span class="sxs-lookup"><span data-stu-id="09bed-150">This example creates a dictionary that maps command line arguments to [lamdba expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="09bed-151">Aşağıdaki örnek, iki sınıf gösterir: bir `ArgsActions` bir komut satırı seçeneği eşleyen sınıfı bir `Action` temsilci ve bir `ArgsProcessor` kullanan `ArgsActions` her yürütmek için `Action` seçeneği karşılaştığında.</span><span class="sxs-lookup"><span data-stu-id="09bed-151">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="09bed-152">Bu örnekte, `ArgsAction` koleksiyonu eşlemeleri yakından temel koleksiyona.</span><span class="sxs-lookup"><span data-stu-id="09bed-152">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="09bed-153">`get` Belirli bir seçenek yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="09bed-153">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="09bed-154">Bu nedenle, döndürürse `Action` bu seçenek ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="09bed-154">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="09bed-155">Değilse, döndürürse, bir `Action` hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="09bed-155">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="09bed-156">Ortak erişimci içermemesi bir `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="09bed-156">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="09bed-157">Bunun yerine, seçenekleri ayarlamak için ortak bir yöntem kullanarak tasarımı.</span><span class="sxs-lookup"><span data-stu-id="09bed-157">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="09bed-158">Çok boyutlu eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="09bed-158">Multi-Dimensional Maps</span></span>

<span data-ttu-id="09bed-159">Birden çok bağımsız değişkenleri kullanma dizin oluşturucular oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09bed-159">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="09bed-160">Ayrıca, bu bağımsız değişkenlerden aynı türden olması için kısıtlanmıştır değil.</span><span class="sxs-lookup"><span data-stu-id="09bed-160">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="09bed-161">İki örnekler bakalım.</span><span class="sxs-lookup"><span data-stu-id="09bed-161">Let's look at two examples.</span></span>   

<span data-ttu-id="09bed-162">İlk örnek Mandelbrot kümesi için değerleri oluşturan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="09bed-162">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="09bed-163">Matematik kümesi arkasında hakkında daha fazla bilgi için okuma [bu makalede](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="09bed-163">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="09bed-164">Dizin Oluşturucu iki double X, bir noktayı tanımlamak için kullanır. Y düzlemi.</span><span class="sxs-lookup"><span data-stu-id="09bed-164">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="09bed-165">Bir noktayı kümesinde olmadığı belirlenir kadar get erişimcisine yineleme sayısını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="09bed-165">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="09bed-166">En fazla yineleme ulaşıldığında, kümesinde noktasıdır ve sınıfın maxIterations değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="09bed-166">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="09bed-167">(Bir nokta kümenin dışında olduğunu belirlemek için gereken yineleme sayısını renklerini Mandelbrot kümesi için popularized oluşturulan bilgisayar görüntülerinde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="09bed-167">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="09bed-168">Değerleri Mandelbrot kümesi tanımlar her (x, y) için gerçek sayı değerlerini koordinatı.</span><span class="sxs-lookup"><span data-stu-id="09bed-168">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="09bed-169">Bu değerleri sonsuz sayıda içeren bir sözlüğü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="09bed-169">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="09bed-170">Bu nedenle, hiçbir depolama kümesi arkasında yoktur.</span><span class="sxs-lookup"><span data-stu-id="09bed-170">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="09bed-171">Bunun yerine, bu sınıfın her nokta değeri hesaplar kodu çağırdığında `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="09bed-171">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="09bed-172">Temel alınan depolama alanı kullanılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="09bed-172">There's no underlying storage used.</span></span>

<span data-ttu-id="09bed-173">Dizin Oluşturucular, burada dizin oluşturucu farklı türlerde birden fazla bağımsız değişken almayan bir son kullanımını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="09bed-173">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="09bed-174">Geçmiş sıcaklık verileri yöneten bir program göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="09bed-174">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="09bed-175">Bu dizin oluşturucu ayarlayın veya bu konumda yüksek ve düşük etme almak için bir şehir ve bir tarih kullanır:</span><span class="sxs-lookup"><span data-stu-id="09bed-175">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="09bed-176">Bu örnek, iki farklı bağımsız hava durumu verilerini eşleyen bir dizin oluşturucu oluşturur: bir şehir (tarafından temsil edilen bir `string`) ve bir tarih (tarafından temsil edilen bir `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="09bed-176">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="09bed-177">İki iç depolama kullanan `Dictionary` sınıfları iki boyutlu sözlüğünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09bed-177">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="09bed-178">Genel API, temel alınan depolama alanı artık temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09bed-178">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="09bed-179">Bunun yerine, dizin oluşturucular dil özelliklerini temel alınan depolama farklı çekirdek koleksiyon türleri kullanmalısınız olsa da, Özet temsil eden ortak bir arabirim oluşturmak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="09bed-179">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="09bed-180">Bazı geliştiriciler için tanınmayan bu kod iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="09bed-180">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="09bed-181">Bu iki `using` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="09bed-181">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="09bed-182">oluşturma bir *diğer* oluşturulan genel bir tür için.</span><span class="sxs-lookup"><span data-stu-id="09bed-182">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="09bed-183">Daha sonra daha açıklayıcı kullanmak için kodu bu deyimleri etkinleştirmek `DateMeasurements` ve `CityDateMeasurements` adları genel yapımı yerine `Dictionary<DateTime, Measurements>` ve `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="09bed-183">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="09bed-184">Bu yapıyı tam olarak nitelenmiş tür adları sağ tarafında kullanmak için gerekli `=` oturum.</span><span class="sxs-lookup"><span data-stu-id="09bed-184">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="09bed-185">İkinci zaman bölümlerini herhangi bir çıkarabilmesi tekniktir `DateTime` kullanılan nesnesi koleksiyonlara dizin.</span><span class="sxs-lookup"><span data-stu-id="09bed-185">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="09bed-186">.NET framework tarih yalnızca türünü içermiyor.</span><span class="sxs-lookup"><span data-stu-id="09bed-186">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="09bed-187">Geliştiricilerin `DateTime` yazın, ancak kullanmak `Date` herhangi emin olmak için özellik `DateTime` o gün nesnesinden eşit.</span><span class="sxs-lookup"><span data-stu-id="09bed-187">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="09bed-188">Özetle</span><span class="sxs-lookup"><span data-stu-id="09bed-188">Summing Up</span></span>

<span data-ttu-id="09bed-189">Bu özellik tek bir değer değil, ancak bunun yerine her öğeyle bağımsız değişkenler kümesine göre burada tanımlanan değerleri koleksiyonunu temsil ettiği sınıfınızda bir özellik benzeri öğesi sahip herhangi bir zamanda dizin oluşturucular oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="09bed-189">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="09bed-190">Bu bağımsız değişkenlerden koleksiyonda hangi öğenin başvurulması benzersiz şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-190">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="09bed-191">Dizin oluşturucular genişletmek kavramı [özellikleri](properties.md), sınıf dışında bir veri öğesi gibi ancak bir yöntem tarafında gibi üyesi olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="09bed-191">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="09bed-192">Dizin oluşturucular bir öğe kümesini temsil eden bir özellikte tek bir öğe bulmak bağımsız değişkenler izin verir.</span><span class="sxs-lookup"><span data-stu-id="09bed-192">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
