---
title: Dizin Oluşturucular
description: C# dizin oluşturucular ve bir veya daha fazla bağımsız değişken kullanarak başvurulan özelliklerdir Dizinli Özellikler nasıl uyguladıkları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 73f79f58cd20187a6fd0de29f53f1a31a269e0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="indexers"></a>Dizin Oluşturucular

*Dizin oluşturucular* özelliklerine benzer. Dizin oluşturucular birçok yolla aynı dil özellikleri oluşturmak [özellikleri](properties.md). Dizin oluşturucular etkinleştirmek *dizine* özellikleri: bağımsız değişkenlerden biri veya daha fazla kullanarak başvurulan özellikleri. Bu bağımsız değişkenlerden bazı değerleri koleksiyona bir dizin sağlayın.

## <a name="indexer-syntax"></a>Dizin Oluşturucu sözdizimi

Bir dizin oluşturucu, değişken adı ve köşeli erişebilirsiniz. Dizin oluşturucu bağımsız değişkenleri köşeli ayraçlar içinde koyun:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Dizin oluşturucular kullanma bildirme `this` özellik adı ve bağımsız değişkenleri köşeli ayraçlar içinde bildirme as anahtar sözcüğü. Bu bildirim önceki paragrafta gösterilen kullanım eşleşir:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Bu ilk örnekten özellikler ve dizin oluşturucular için söz dizimi arasındaki ilişkiyi görebilirsiniz. Dizin oluşturucular sözdizimi kurallarına çoğunu aracılığıyla bu benzerleme taşır. Dizin Oluşturucular, tüm geçerli erişim değiştiricileri olabilir (Genel, korumalı korumalı iç, korumalı, iç, özel veya özel). Bunlar, korumalı, sanal ya da soyut olabilir. Özellikleriyle olduğu gibi get için farklı erişim değiştiricileri belirtin ve accesssors bir dizin oluşturucu ayarlayın.
(Tarafından set erişimcisine atlayarak) salt okunur dizin oluşturucuları ya da salt yazılır dizin oluşturucular (get erişimcisine kaldırarak) de belirtebilir.

Neredeyse her dizin oluşturucular için özellikler ile çalışma hakkında bilgi edineceksiniz uygulayabilirsiniz. Bu kuralın tek özel durum *otomatik uygulanan Özellikler*. Derleyici her zaman bir dizin oluşturucu için doğru depolama oluşturulamıyor.

Bir öğeyi öğeleri kümesi başvurmak için bağımsız değişken varlığını dizin oluşturucular özelliklerinden ayırır. Her dizin oluşturucu benzersiz için bağımsız değişken listeleri sürece bir tür üzerinde birden çok dizin oluşturucu tanımlayabilir. Burada bir sınıf tanımı'nda bir veya daha fazla dizin oluşturucular kullanabilir farklı senaryolar inceleyelim. 

## <a name="scenarios"></a>Senaryolar

Tanımlayın *dizin oluşturucular* API'si tanımladığınız bağımsız değişkenler bu koleksiyon için bazı koleksiyonu modellediğinde, yazın. Dizin oluşturucular olabilir veya doğrudan .NET core framework parçası olan koleksiyon türleri için eşleşmeyebilir. Bir koleksiyon modelleme yanı sıra diğer sorumlulukları türünüz olabilir.
Dizin oluşturucular bu soyutlama değerlerini nasıl depolanır veya hesaplanan iç ayrıntılarını sokmadan türünüz ait Özet eşleşen API sağlamak etkinleştirin.

Şimdi kullanmaya yönelik yaygın senaryolardan bazıları rehberlik *dizin oluşturucular*. Erişebileceğiniz [dizin oluşturucular için örnek klasör](https://github.com/dotnet/samples/tree/master/csharp/indexers). Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Diziler ve vektörler

Dizin oluşturucular oluşturmak için en sık karşılaşılan senaryolardan biri, durum, bir dizi veya bir vektör türünüz modeller durumdur. Model veri sıralı bir listesi için bir dizin oluşturucu oluşturabilirsiniz. 

Kendi dizin oluşturucu oluşturma avantajı, gereksinimlerinize uygun olarak bu koleksiyon için depolama tanımlayabilirsiniz olmasıdır. Burada türünüz belleğe aynı anda yüklemek için çok büyük geçmiş veri modelleri bir senaryoyu düşünün. Yükleme ve kaldırma bölümlerini kullanıma dayalı koleksiyon gerekir. Aşağıdaki örneğe bu davranışını modeller. Bu, kaç tane veri noktalarını mevcut raporlar. İstek üzerine veri bölümlerini tutmak için sayfaları oluşturur. Daha yeni istekleri tarafından gerekli sayfaları için yer açmak için bellek sayfaları kaldırır.

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

Koleksiyon her tür model oluşturmak için bu tasarım deyim izleyebilirsiniz veri kümesinin tamamını bir bellek içi koleksiyona yüklenmemesine için iyi neden olduğu. Dikkat `Page` ortak arabirimi parçası olmayan özel bir iç içe geçmiş sınıf bir sınıftır. Bu ayrıntılar, bu sınıfın tüm kullanıcılardan gizlenir.

### <a name="dictionaries"></a>Sözlük

Bir sözlük veya bir harita model gerektiğinde başka bir yaygın senaryodur. Bu senaryo, anahtarı, genellikle metnin anahtarları temel değerleri türünüz depolayan durumdur. Bu örnek komut satırı bağımsız değişkenleri için eşleşen bir sözlük oluşturur [lamdba ifadeleri](delegates-overview.md) bu seçenekleri yönetin. Aşağıdaki örnek, iki sınıf gösterir: bir `ArgsActions` bir komut satırı seçeneği eşleyen sınıfı bir `Action` temsilci ve bir `ArgsProcessor` kullanan `ArgsActions` her yürütmek için `Action` seçeneği karşılaştığında.

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

Bu örnekte, `ArgsAction` koleksiyonu eşlemeleri yakından temel koleksiyona.
`get` Belirli bir seçenek yapılandırılıp yapılandırılmadığını belirler. Bu nedenle, döndürürse `Action` bu seçenek ile ilişkili. Değilse, döndürürse, bir `Action` hiçbir şey yapmaz. Ortak erişimci içermemesi bir `set` erişimcisi. Bunun yerine, seçenekleri ayarlamak için ortak bir yöntem kullanarak tasarımı.

### <a name="multi-dimensional-maps"></a>Çok boyutlu eşlemeleri

Birden çok bağımsız değişkenleri kullanma dizin oluşturucular oluşturabilirsiniz. Ayrıca, bu bağımsız değişkenlerden aynı türden olması için kısıtlanmıştır değil. İki örnekler bakalım.   

İlk örnek Mandelbrot kümesi için değerleri oluşturan bir sınıfı gösterir. Matematik kümesi arkasında hakkında daha fazla bilgi için okuma [bu makalede](https://en.wikipedia.org/wiki/Mandelbrot_set). Dizin Oluşturucu iki double X, bir noktayı tanımlamak için kullanır. Y düzlemi.
Bir noktayı kümesinde olmadığı belirlenir kadar get erişimcisine yineleme sayısını hesaplar. En fazla yineleme ulaşıldığında, kümesinde noktasıdır ve sınıfın maxIterations değeri döndürülür. (Bir nokta kümenin dışında olduğunu belirlemek için gereken yineleme sayısını renklerini Mandelbrot kümesi için popularized oluşturulan bilgisayar görüntülerinde tanımlayın.

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

Değerleri Mandelbrot kümesi tanımlar her (x, y) için gerçek sayı değerlerini koordinatı.
Bu değerleri sonsuz sayıda içeren bir sözlüğü tanımlar. Bu nedenle, hiçbir depolama kümesi arkasında yoktur. Bunun yerine, bu sınıfın her nokta değeri hesaplar kodu çağırdığında `get` erişimcisi. Temel alınan depolama alanı kullanılan yoktur.

Dizin Oluşturucular, burada dizin oluşturucu farklı türlerde birden fazla bağımsız değişken almayan bir son kullanımını inceleyelim. Geçmiş sıcaklık verileri yöneten bir program göz önünde bulundurun. Bu dizin oluşturucu ayarlayın veya bu konumda yüksek ve düşük etme almak için bir şehir ve bir tarih kullanır:

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

Bu örnek, iki farklı bağımsız hava durumu verilerini eşleyen bir dizin oluşturucu oluşturur: bir şehir (tarafından temsil edilen bir `string`) ve bir tarih (tarafından temsil edilen bir `DateTime`). İki iç depolama kullanan `Dictionary` sınıfları iki boyutlu sözlüğünü temsil eder. Genel API, temel alınan depolama alanı artık temsil eder. Bunun yerine, dizin oluşturucular dil özelliklerini temel alınan depolama farklı çekirdek koleksiyon türleri kullanmalısınız olsa da, Özet temsil eden ortak bir arabirim oluşturmak olanak sağlar.

Bazı geliştiriciler için tanınmayan bu kod iki bölümü vardır. Bu iki `using` deyimleri:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

oluşturma bir *diğer* oluşturulan genel bir tür için. Daha sonra daha açıklayıcı kullanmak için kodu bu deyimleri etkinleştirmek `DateMeasurements` ve `CityDateMeasurements` adları genel yapımı yerine `Dictionary<DateTime, Measurements>` ve `Dictionary<string, Dictionary<DateTime, Measurements> >`. Bu yapıyı tam olarak nitelenmiş tür adları sağ tarafında kullanmak için gerekli `=` oturum.

İkinci zaman bölümlerini herhangi bir çıkarabilmesi tekniktir `DateTime` kullanılan nesnesi koleksiyonlara dizin. .NET framework tarih yalnızca türünü içermiyor.
Geliştiricilerin `DateTime` yazın, ancak kullanmak `Date` herhangi emin olmak için özellik `DateTime` o gün nesnesinden eşit.

## <a name="summing-up"></a>Özetle

Bu özellik tek bir değer değil, ancak bunun yerine her öğeyle bağımsız değişkenler kümesine göre burada tanımlanan değerleri koleksiyonunu temsil ettiği sınıfınızda bir özellik benzeri öğesi sahip herhangi bir zamanda dizin oluşturucular oluşturmanız gerekir. Bu bağımsız değişkenlerden koleksiyonda hangi öğenin başvurulması benzersiz şekilde tanımlayabilir.
Dizin oluşturucular genişletmek kavramı [özellikleri](properties.md), sınıf dışında bir veri öğesi gibi ancak bir yöntem tarafında gibi üyesi olduğu kabul edilir. Dizin oluşturucular bir öğe kümesini temsil eden bir özellikte tek bir öğe bulmak bağımsız değişkenler izin verir.
