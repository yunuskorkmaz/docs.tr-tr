---
title: Dizin Oluşturucular
description: Hakkında bilgi edinin C# dizin oluşturucular ve nasıl uyguladıkları dizin oluşturulmuş başvurulan bir veya daha fazla bağımsız değişken kullanarak özellikleri olan özellikleri.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041147"
---
# <a name="indexers"></a>Dizin Oluşturucular

*Dizin oluşturucular* özelliklerine benzer. Dizin oluşturucular birçok yolla aynı dil özellikleri oluşturmak [özellikleri](properties.md). Etkinleştir Dizinleyicileri *dizine* özellikleri: bir veya daha fazla bağımsız değişken kullanarak başvurulan özellikleri. Bu bağımsız değişkenlerden bazı değerler koleksiyonu içinde bir dizin sağlar.

## <a name="indexer-syntax"></a>Dizin Oluşturucu sözdizimi

Bir dizin oluşturucu, bir değişken adı ve köşeli ayraçlar erişin. Dizin oluşturucu bağımsız değişkenleri köşeli ayraçlar içine yerleştirdiğiniz:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Dizin oluşturucular kullanarak bildirdiğiniz `this` özellik adı ve bağımsız değişkenler köşeli ayraç içinde bildirme as anahtar sözcüğü. Bu bildirim önceki paragrafta gösterilen kullanım eşleşmesi:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Bu ilk örnekte, dizin oluşturucular ve özellikler için söz dizimi arasındaki ilişkiyi görebilirsiniz. Çoğu dizin oluşturucular için söz dizimi kuralın aracılığıyla bu benzerleme taşır. Dizin Oluşturucular, herhangi bir geçerli erişim değiştiricileri olabilir (Genel, korumalı korumalı iç, korumalı, dahili, özel veya özel). Bunlar, korumalı, virtual veya abstract olabilir. Özellikleriyle yönteminde olduğu gibi get için farklı erişim değiştiricileri belirtmeniz ve set erişimcileri bir dizin oluşturucu.
(Set erişimcisine atlama tarafından) salt okunur dizin oluşturucuları veya salt yazılır dizin oluşturucular (get erişimcisine gt;(yok)) de belirtebilirsiniz.

Hemen dizin oluşturucular özelliklere ile çalışmaktan şunların her şeyi uygulayabilirsiniz. Bu kuralın tek özel durum *otomatik uygulanan Özellikler*. Derleyici, her zaman doğru depolama dizin oluşturucu için oluşturulamıyor.

Öğelerin kümesi bir öğeye başvuru için bağımsız değişken varlığını dizin oluşturucular özelliklerinden ayırır. Her dizin oluşturucu benzersiz için bağımsız değişken listeleri sürece bir tür üzerinde birden çok dizin oluşturucu tanımlayabilir. Bir veya daha fazla dizin oluşturucular sınıf tanımında burada kullanabileceğinize farklı senaryolar araştıralım. 

## <a name="scenarios"></a>Senaryolar

Tanımlayın *dizin oluşturucular* API'SİYLE burada tanımlarsınız bağımsız değişkenler bu koleksiyon için bazı koleksiyon modellediğinde, türü. Dizin oluşturucular olabilir veya .NET core framework parçası olan doğrudan koleksiyon türlerine eşleşmeyebilir. Türünüzün bir koleksiyon modelleme yanı sıra diğer sorumlulukları olabilir.
Dizin oluşturucular bu soyutlama değerlerini nasıl depolanan veya hesaplanan iç ayrıntılarını sokmadan, türün Özet eşleşen API'si sağlar.

Şimdi kullanmaya yönelik yaygın senaryolardan bazıları yol *dizin oluşturucular*. Erişebildiğiniz [örnek klasörüne dizin oluşturucular için](https://github.com/dotnet/samples/tree/master/csharp/indexers). Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Diziler ve vektörleri

Türünüzün bir dizi veya bir vektör modellediğinde dizin oluşturucular oluşturmak için en sık karşılaşılan senaryolardan biridir. Model verileri sıralı bir listesi için bir dizin oluşturucu oluşturabilirsiniz. 

Kendi dizin oluşturucu oluşturma avantajı, depolama ihtiyaçlarınıza uyacak şekilde bu koleksiyon için tanımlayabileceğiniz olmasıdır. Burada türünüzü tek seferde belleğe yüklemek için çok büyük geçmiş veri modelleri bir senaryo düşünün. Yükleme ve kaldırma kullanımını temel alarak koleksiyon bölümlerini gerekir. Bu davranışı aşağıdaki örneğe modeller. Kaç tane veri noktalarının mevcut üzerinde rapor. Verilerin isteğe bağlı olarak bölümlerde tutacak sayfaları oluşturur. Tarafından daha yeni istekler gerekeceğinden sayfaları için yer açmak için bellek sayfaları kaldırır.

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

Bu tasarım deyim herhangi bir tür koleksiyonun modellemek için izleyebileceğiniz bulunduğu veri kümesinin tamamını bir bellek içi koleksiyona yüklemeyecek için iyi nedenler vardır. Dikkat `Page` ortak arabiriminin bir parçası değil özel, iç içe geçmiş bir sınıfı. Bu ayrıntılar, bu sınıfın tüm kullanıcılardan gizlenir.

### <a name="dictionaries"></a>sözlükler

Bir sözlüğün veya bir map model gerektiğinde başka bir yaygın senaryodur. Bu senaryo genellikle metin anahtarları anahtarını temel alan değerleri türünüz depolar andır. Bu örnek komut satırı bağımsız değişkenleri eşleyen sözlük oluşturur [lambda ifadeleri](delegates-overview.md) bu seçenekleri yönetin. Aşağıdaki örnek, iki sınıf gösterir: bir `ArgsActions` eşleyen bir komut satırı seçeneğini sınıfı bir `Action` temsilcisi ve bir `ArgsProcessor` kullanan `ArgsActions` her yürütülecek `Action` seçeneği karşılaştığında.

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

Bu örnekte, `ArgsAction` koleksiyon temel toplulukta yakından eşlenir.
`get` Belirli bir seçenek yapılandırılıp yapılandırılmadığını belirler. Bu nedenle, döndürürse, `Action` bu seçenek ile ilişkilendirilmiş. Değilse, döndürürse, bir `Action` hiçbir şey yapmaz. Genel erişimci içermemesi bir `set` erişimcisi. Bunun yerine, seçeneklerini ayarlama için genel bir yöntem kullanılarak tasarım.

### <a name="multi-dimensional-maps"></a>Çok boyutlu eşlemeleri

Birden çok bağımsız değişkenler kullanan dizin oluşturucular oluşturabilir. Ayrıca, bu bağımsız değişkenler aynı türde olacak şekilde kısıtlanır değil. İki örneklere göz atalım.   

İlk örnek için Mandelbrot değerleri üreten bir sınıfı gösterir. Matematik arkasında kümesi hakkında daha fazla bilgi için okuma [bu makalede](https://en.wikipedia.org/wiki/Mandelbrot_set). Dizin Oluşturucu iki çiftten X, bir noktayı tanımlamak için kullanır. Y düzlemleriyle.
Bir nokta kümesinde olmadığı belirlenir kadar get erişimcisine yineleme sayısını hesaplar. En fazla yineleme ulaşıldığında, kümede noktasıdır ve sınıfın maxIterations değeri döndürülür. (Mandelbrot kümesi için popüler bilgisayar tarafından oluşturulan görüntüleri bir nokta kümesi dışında olduğunu belirlemek gerekli olan yineleme sayısı için renk tanımlar.

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

Değerlerinde Mandelbrot tanımlar her (x, y) için gerçek sayı değerlerini koordine edin.
Bu değerleri sonsuz sayıda içerebilen bir sözlüğü tanımlar. Bu nedenle, hiçbir depolama kümesi arkasında yoktur. Bunun yerine, kodu çağırdığında bu sınıfın her bir noktası değerini hesaplar `get` erişimcisi. Temel alınan depolama alanı kullanılan yoktur.

Dizin oluşturucular için burada dizin oluşturucuyu farklı türlerde birden çok bağımsız değişkeni alır, bir son kullanımını inceleyelim. Geçmiş sıcaklık verileri yöneten bir program göz önünde bulundurun. Bu dizin oluşturucu ayarlayın veya bu konumda için yüksek ve düşük Sıcaklıkların almak için bir şehir ve bir tarih kullanır:

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

Bu örnek, iki farklı bağımsız değişken hava durumu verilerine eşleyen bir dizin oluşturur: Bir şehrin (tarafından temsil edilen bir `string`) ve bir tarihi (tarafından temsil edilen bir `DateTime`). İki iç depolama kullanan `Dictionary` sınıflar için iki boyutlu sözlüğünü temsil eder. Genel API, temel alınan depolama artık temsil eder. Bunun yerine, dizin oluşturucular dil özelliklerinin temel alınan depolama farklı çekirdek koleksiyon türleri kullanmalısınız olsa bile, soyutlamayı temsil eder bir ortak arabirim oluşturmanıza olanak sağlar.

Bazı geliştiriciler için tanınmayan bu kod, iki bölümü vardır. Bu iki `using` ifadeleri:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

oluşturma bir *diğer* için oluşturulmuş bir genel türü. Bu ifadeler, daha sonra daha açıklayıcı kullanmak için kodu sağlar `DateMeasurements` ve `CityDateMeasurements` adları yerine genel oluşumu `Dictionary<DateTime, Measurements>` ve `Dictionary<string, Dictionary<DateTime, Measurements> >`. Tento konstruktor je sağ tarafında tam olarak nitelenmiş tür adlarını kullanarak gerektiren `=` oturum.

İkinci yöntem zaman bölümlerini herhangi Şerit göstermektir `DateTime` kullanılan nesne koleksiyonlara dizin. .NET framework yalnızca tarih türü içermez.
Geliştiricilerin `DateTime` yazın, ancak kullanmak `Date` herhangi emin olmak için özellik `DateTime` o gün nesneden eşit.

## <a name="summing-up"></a>Özetle

Sınıfınızdaki bu özellik tek bir değer değil, ancak bunun yerine her bir öğe tarafından bağımsız değişken kümesinin burada tanımlanan değerleri koleksiyonunu temsil ettiği bir özellik benzeri öğesine sahip herhangi bir zamanda, dizin oluşturucular oluşturmanız gerekir. Bu bağımsız değişkenlerden hangi öğe koleksiyonda başvurulan benzersiz şekilde tanımlayabilir.
Dizin oluşturucular genişletmek kavramını [özellikleri](properties.md), sınıf dışında bir veri öğesi gibi ancak tarafındaki bir yöntemi gibi bir üye olduğu kabul edilir. Dizin oluşturucular bir öğe kümesini temsil eden bir özelliği tek bir öğeyi bulmak bağımsız değişkenler izin verir.
