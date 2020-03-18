---
title: Dizin Oluşturucular
description: C# dizinleyicileri ve bir veya daha fazla bağımsız değişken kullanılarak başvurulan özellikler olan dizinlenmiş özellikleri nasıl uyguladıkları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 8e583b8a7cedab61ea6fdd56587608907610b6b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145690"
---
# <a name="indexers"></a><span data-ttu-id="8dc39-103">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8dc39-103">Indexers</span></span>

<span data-ttu-id="8dc39-104">*Dizin leyiciler* özelliklere benzer.</span><span class="sxs-lookup"><span data-stu-id="8dc39-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="8dc39-105">Birçok yönden dizin oluşturicular [özellikleri](properties.md)olarak aynı dil özellikleri üzerine inşa.</span><span class="sxs-lookup"><span data-stu-id="8dc39-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="8dc39-106">*Dizinleyiciler dizinlenmiş* özellikleri etkinleştirin: bir veya daha fazla bağımsız değişken kullanılarak başvurulan özellikler.</span><span class="sxs-lookup"><span data-stu-id="8dc39-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="8dc39-107">Bu bağımsız değişkenler, bazı değer koleksiyonuna bir dizin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="8dc39-108">Dizinleyici Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dc39-108">Indexer Syntax</span></span>

<span data-ttu-id="8dc39-109">Bir dizin leyiciye değişken adı ve kare ayraçlar aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="8dc39-110">Dizinleyici bağımsız değişkenlerini köşeli ayraçların içine yerebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8dc39-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="8dc39-111">Dizin işaretçilerini `this` özellik adı olarak anahtar sözcüğü kullanarak ve bağımsız değişkenleri kare ayraçlar içinde bildirerek bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="8dc39-112">Bu bildirim, önceki paragrafta gösterilen kullanımla eşleşir:</span><span class="sxs-lookup"><span data-stu-id="8dc39-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="8dc39-113">Bu ilk örnekten, özellikler için sözdizimi ile dizinleyiciler arasındaki ilişkiyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="8dc39-114">Bu benzetme dizinleyiciler için sözdizimi kurallarının çoğunu taşır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="8dc39-115">Dizin leyicilerin geçerli erişim değiştiriciler (genel, korumalı dahili, korumalı, dahili, özel veya özel korumalı) olabilir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="8dc39-116">Bunlar mühürlü, sanal veya soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="8dc39-117">Özelliklerde olduğu gibi, bir dizin leyicide erişimve ayarlayıcılar için farklı erişim değiştiriciler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="8dc39-118">Salt okunur dizinleyiciler (ayarlanan erişimi atlayarak) veya yalnızca yazma dizinleyicileri (get accesser'ı atlayarak) da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="8dc39-119">Özelliklerle çalışmaktan dizin leyicilere kadar öğrendiğiniz hemen hemen her şeyi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="8dc39-120">Bu kuralın tek istisnası *otomatik uygulanan özelliklerdir.*</span><span class="sxs-lookup"><span data-stu-id="8dc39-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="8dc39-121">Derleyici her zaman bir dizin leyici için doğru depolama oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="8dc39-122">Bir öğekümesinde bir öğeye başvuru yapacak bağımsız değişkenlerin varlığı dizin leyicileri özelliklerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="8dc39-123">Her dizinleyici için bağımsız değişken listeleri benzersiz olduğu sürece, bir tür birden çok dizinleyici tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="8dc39-124">Sınıf tanımında bir veya daha fazla dizinleyici kullanabileceğiniz farklı senaryoları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="8dc39-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="8dc39-125">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="8dc39-125">Scenarios</span></span>

<span data-ttu-id="8dc39-126">ApI' si, bu koleksiyondaki bağımsız değişkenleri tanımladığınız bazı koleksiyonu modellediğinde, türünüzdeki *dizinleyicileri* tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8dc39-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="8dc39-127">Dizin oluşturilarınız doğrudan .NET çekirdek çerçevesinin bir parçası olan toplama türleri ile eşlenebilir veya eşlemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="8dc39-128">Türünüzün, bir koleksiyonu modellemeye ek olarak başka sorumlulukları da olabilir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="8dc39-129">Dizin leyiciler, bu soyutlama nın değerlerinin nasıl depolandırılabildiğini veya hesaplandırılmalarını ortaya çıkarmadan, türünüzle eşleşen API'yi sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="8dc39-130">*Dizin oluşturma*yı kullanmak için ortak senaryolardan bazılarını gözden geçirelim.</span><span class="sxs-lookup"><span data-stu-id="8dc39-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="8dc39-131">[Dizinleyiciler için örnek klasöre](https://github.com/dotnet/samples/tree/master/csharp/indexers)erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="8dc39-132">İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="8dc39-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="8dc39-133">Diziler ve Vektörler</span><span class="sxs-lookup"><span data-stu-id="8dc39-133">Arrays and Vectors</span></span>

<span data-ttu-id="8dc39-134">Dizin oluşturanın en yaygın senaryolarından biri, türünüzbir dizi veya vektör modelini oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="8dc39-135">Sıralanmış bir veri listesini modellemek için bir dizin oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="8dc39-136">Kendi dizin oluşturucunuzu oluşturmanın avantajı, bu koleksiyonun depolama alanını gereksinimlerinize uyacak şekilde tanımlayabilmektir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="8dc39-137">Türün uzun zamandır aynı anda belleğe yüklenemeyecek kadar büyük verileri modellediği bir senaryo düşünün.</span><span class="sxs-lookup"><span data-stu-id="8dc39-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="8dc39-138">Kullanıma göre koleksiyonun bölümlerini yüklemeniz ve boşaltmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="8dc39-139">Aşağıdaki örnek bu davranışı modeller.</span><span class="sxs-lookup"><span data-stu-id="8dc39-139">The example following models this behavior.</span></span> <span data-ttu-id="8dc39-140">Kaç veri noktasının var olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-140">It reports on how many data points exist.</span></span> <span data-ttu-id="8dc39-141">Verilerin bölümlerini isteğe bağlı tutmak için sayfalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8dc39-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="8dc39-142">Daha yeni istekler tarafından gerekli sayfalara yer açmak için sayfaları bellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="8dc39-143">Tüm veri kümesini bellek içi bir koleksiyona yüklememek için iyi nedenlerin olduğu her türlü koleksiyonu modellemek için bu tasarım deyimini takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="8dc39-144">Sınıfın ortak `Page` arabirimin bir parçası olmayan özel iç içe ayrılmış bir sınıf olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8dc39-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="8dc39-145">Bu ayrıntılar bu sınıfın tüm kullanıcılarından gizlenir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="8dc39-146">Sözlükler</span><span class="sxs-lookup"><span data-stu-id="8dc39-146">Dictionaries</span></span>

<span data-ttu-id="8dc39-147">Başka bir yaygın senaryo, bir sözlük veya harita modellemeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="8dc39-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="8dc39-148">Bu senaryo, türünüzün değerleri genellikle metin tuşlarına göre depolayabOlmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="8dc39-149">Bu örnek, komut satırı bağımsız değişkenlerini bu seçenekleri yöneten [lambda ifadelerle](delegates-overview.md) eşleyen bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8dc39-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="8dc39-150">Aşağıdaki örnekte iki sınıf `ArgsActions` gösterilmektedir: komut satırı `Action` seçeneğini bir `ArgsProcessor` temsilciyle `ArgsActions` eşleyen `Action` bir sınıf ve bu seçenekle karşılaştığında her birini yürütmek için kullanan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="8dc39-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="8dc39-151">Bu örnekte, `ArgsAction` koleksiyon temel koleksiyona yakından eşler.</span><span class="sxs-lookup"><span data-stu-id="8dc39-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="8dc39-152">Belirli `get` bir seçeneğin yapılandırıp yapılandırılmamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8dc39-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="8dc39-153">Bu nedenle, bu `Action` seçenekle ilişkili döndürür.</span><span class="sxs-lookup"><span data-stu-id="8dc39-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="8dc39-154">Değilse, hiçbir şey `Action` yapmaz bir döner.</span><span class="sxs-lookup"><span data-stu-id="8dc39-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="8dc39-155">Ortak erişimci bir `set` erişimci içermez.</span><span class="sxs-lookup"><span data-stu-id="8dc39-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="8dc39-156">Bunun yerine, seçenekleri ayarlamak için ortak bir yöntem kullanarak tasarım.</span><span class="sxs-lookup"><span data-stu-id="8dc39-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="8dc39-157">Çok Boyutlu Haritalar</span><span class="sxs-lookup"><span data-stu-id="8dc39-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="8dc39-158">Birden çok bağımsız değişken kullanan dizin oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="8dc39-159">Buna ek olarak, bu bağımsız değişkenler aynı türde sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="8dc39-160">İki örnşeye bakalım.</span><span class="sxs-lookup"><span data-stu-id="8dc39-160">Let's look at two examples.</span></span>

<span data-ttu-id="8dc39-161">İlk örnek, Mandelbrot kümesi için değerler üreten bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="8dc39-162">Setin arkasındaki matematik hakkında daha fazla bilgi için [bu makaleyi](https://en.wikipedia.org/wiki/Mandelbrot_set)okuyun.</span><span class="sxs-lookup"><span data-stu-id="8dc39-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="8dc39-163">Dizinleyici, X, Y düzleminde bir noktayı tanımlamak için iki çift kullanır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="8dc39-164">Get erişimcisi, bir nokta kümede olmadığı belirlenene kadar yineleme sayısını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="8dc39-165">En büyük yinelemelere ulaşılırsa, nokta kümededir ve sınıfın maxIterations değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8dc39-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="8dc39-166">(Mandelbrot kümesi için popüler hale getirilen bilgisayar, bir noktanın kümenin dışında olduğunu belirlemek için gerekli yineleme sayısı için renkleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="8dc39-167">Mandelbrot Kümesi, gerçek sayı değerleri için her (x,y) koordinatındaki değerleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="8dc39-168">Bu, sonsuz sayıda değer içerebilecek bir sözlük tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="8dc39-169">Bu nedenle, kümenin arkasında depolama alanı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8dc39-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="8dc39-170">Bunun yerine, bu sınıf, kod erişime gireni aradığında her noktanın `get` değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8dc39-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="8dc39-171">Temel depolama alanı kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8dc39-171">There's no underlying storage used.</span></span>

<span data-ttu-id="8dc39-172">Dizinleyicinin farklı türde birden çok bağımsız değişken aldığı dizinleyicilerin son bir kullanımını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="8dc39-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="8dc39-173">Geçmiş sıcaklık verilerini yöneten bir program düşünün.</span><span class="sxs-lookup"><span data-stu-id="8dc39-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="8dc39-174">Bu dizinleyici, o konum için yüksek ve düşük sıcaklıkları ayarlamak veya elde etmek için bir şehir ve tarih kullanır:</span><span class="sxs-lookup"><span data-stu-id="8dc39-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="8dc39-175">Bu örnek, hava durumu verilerini iki farklı bağımsız değişkenüzerinde eşleyen `string`bir dizin oluşturucu oluşturur: bir şehir (a ile temsil edilir) ve bir tarih (bir `DateTime`ile temsil edilir).</span><span class="sxs-lookup"><span data-stu-id="8dc39-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="8dc39-176">İç depolama iki `Dictionary` boyutlu sözlüğü temsil etmek için iki sınıf kullanır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="8dc39-177">Genel API artık temel depolamayı temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="8dc39-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="8dc39-178">Bunun yerine, dizin oluşturi erlerin dil özellikleri, temel depolama alanı farklı çekirdek toplama türleri kullanmanız gerekse bile soyutlamanızı temsil eden ortak bir arabirim oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="8dc39-179">Bu kodun bazı geliştiricileriçin yabancı olabilecek iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="8dc39-180">Bu `using` iki ifade:</span><span class="sxs-lookup"><span data-stu-id="8dc39-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="8dc39-181">oluşturulmuş genel bir tür için bir *takma ad* oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8dc39-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="8dc39-182">Bu ifadeler kodun daha sonra genel yapı `DateMeasurements` `CityDateMeasurements` yerine daha açıklayıcı ve `Dictionary<DateTime, Measurements>` `Dictionary<string, Dictionary<DateTime, Measurements> >`adları kullanmasını sağlar ve.</span><span class="sxs-lookup"><span data-stu-id="8dc39-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="8dc39-183">Bu `=` yapı, işaretin sağ tarafında tam nitelikli tür adlarının kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="8dc39-184">İkinci teknik, koleksiyonları dizine dizine `DateTime` dizin lemek için kullanılan herhangi bir nesnenin zaman bölümlerini şeritlemektir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="8dc39-185">.NET yalnızca tarih türü içermez.</span><span class="sxs-lookup"><span data-stu-id="8dc39-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="8dc39-186">Geliştiriciler `DateTime` türü kullanır, ancak `Date` o güne `DateTime` ait herhangi bir nesnenin eşit olduğundan emin olmak için özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="8dc39-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="8dc39-187">Özetleme</span><span class="sxs-lookup"><span data-stu-id="8dc39-187">Summing Up</span></span>

<span data-ttu-id="8dc39-188">Sınıfınızda, bu özelliğin tek bir değeri değil, her bir öğenin bir dizi bağımsız değişkentarafından tanımlandığı değerler koleksiyonunu temsil ettiği özellik benzeri bir öğeye sahip olduğunuz her zaman dizin oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8dc39-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="8dc39-189">Bu bağımsız değişkenler, koleksiyondaki hangi öğeye başvurulması gerektiğini benzersiz olarak belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="8dc39-190">Dizin [leyiciler,](properties.md)bir üyenin sınıfın dışından gelen bir veri öğesi gibi, ancak içerideki bir yöntem gibi muamele gördüğü özellikler kavramını genişletir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="8dc39-191">Dizin leyiciler, bağımsız değişkenlerin bir öğe kümesini temsil eden bir özellikte tek bir öğe bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8dc39-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
