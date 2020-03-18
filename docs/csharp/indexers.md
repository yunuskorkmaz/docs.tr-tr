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
# <a name="indexers"></a>Dizin Oluşturucular

*Dizin leyiciler* özelliklere benzer. Birçok yönden dizin oluşturicular [özellikleri](properties.md)olarak aynı dil özellikleri üzerine inşa. *Dizinleyiciler dizinlenmiş* özellikleri etkinleştirin: bir veya daha fazla bağımsız değişken kullanılarak başvurulan özellikler. Bu bağımsız değişkenler, bazı değer koleksiyonuna bir dizin sağlar.

## <a name="indexer-syntax"></a>Dizinleyici Sözdizimi

Bir dizin leyiciye değişken adı ve kare ayraçlar aracılığıyla erişebilirsiniz. Dizinleyici bağımsız değişkenlerini köşeli ayraçların içine yerebilirsiniz:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Dizin işaretçilerini `this` özellik adı olarak anahtar sözcüğü kullanarak ve bağımsız değişkenleri kare ayraçlar içinde bildirerek bildirirsiniz. Bu bildirim, önceki paragrafta gösterilen kullanımla eşleşir:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Bu ilk örnekten, özellikler için sözdizimi ile dizinleyiciler arasındaki ilişkiyi görebilirsiniz. Bu benzetme dizinleyiciler için sözdizimi kurallarının çoğunu taşır. Dizin leyicilerin geçerli erişim değiştiriciler (genel, korumalı dahili, korumalı, dahili, özel veya özel korumalı) olabilir. Bunlar mühürlü, sanal veya soyut olabilir. Özelliklerde olduğu gibi, bir dizin leyicide erişimve ayarlayıcılar için farklı erişim değiştiriciler belirtebilirsiniz.
Salt okunur dizinleyiciler (ayarlanan erişimi atlayarak) veya yalnızca yazma dizinleyicileri (get accesser'ı atlayarak) da belirtebilirsiniz.

Özelliklerle çalışmaktan dizin leyicilere kadar öğrendiğiniz hemen hemen her şeyi uygulayabilirsiniz. Bu kuralın tek istisnası *otomatik uygulanan özelliklerdir.* Derleyici her zaman bir dizin leyici için doğru depolama oluşturamaz.

Bir öğekümesinde bir öğeye başvuru yapacak bağımsız değişkenlerin varlığı dizin leyicileri özelliklerden ayırır. Her dizinleyici için bağımsız değişken listeleri benzersiz olduğu sürece, bir tür birden çok dizinleyici tanımlayabilirsiniz. Sınıf tanımında bir veya daha fazla dizinleyici kullanabileceğiniz farklı senaryoları inceleyelim.

## <a name="scenarios"></a>Senaryolar

ApI' si, bu koleksiyondaki bağımsız değişkenleri tanımladığınız bazı koleksiyonu modellediğinde, türünüzdeki *dizinleyicileri* tanımlarsınız. Dizin oluşturilarınız doğrudan .NET çekirdek çerçevesinin bir parçası olan toplama türleri ile eşlenebilir veya eşlemeyebilir. Türünüzün, bir koleksiyonu modellemeye ek olarak başka sorumlulukları da olabilir.
Dizin leyiciler, bu soyutlama nın değerlerinin nasıl depolandırılabildiğini veya hesaplandırılmalarını ortaya çıkarmadan, türünüzle eşleşen API'yi sağlamanıza olanak tanır.

*Dizin oluşturma*yı kullanmak için ortak senaryolardan bazılarını gözden geçirelim. [Dizinleyiciler için örnek klasöre](https://github.com/dotnet/samples/tree/master/csharp/indexers)erişebilirsiniz. İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

### <a name="arrays-and-vectors"></a>Diziler ve Vektörler

Dizin oluşturanın en yaygın senaryolarından biri, türünüzbir dizi veya vektör modelini oluşturmasıdır. Sıralanmış bir veri listesini modellemek için bir dizin oluşturabilirsiniz.

Kendi dizin oluşturucunuzu oluşturmanın avantajı, bu koleksiyonun depolama alanını gereksinimlerinize uyacak şekilde tanımlayabilmektir. Türün uzun zamandır aynı anda belleğe yüklenemeyecek kadar büyük verileri modellediği bir senaryo düşünün. Kullanıma göre koleksiyonun bölümlerini yüklemeniz ve boşaltmanız gerekir. Aşağıdaki örnek bu davranışı modeller. Kaç veri noktasının var olduğunu bildirir. Verilerin bölümlerini isteğe bağlı tutmak için sayfalar oluşturur. Daha yeni istekler tarafından gerekli sayfalara yer açmak için sayfaları bellekten kaldırır.

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

Tüm veri kümesini bellek içi bir koleksiyona yüklememek için iyi nedenlerin olduğu her türlü koleksiyonu modellemek için bu tasarım deyimini takip edebilirsiniz. Sınıfın ortak `Page` arabirimin bir parçası olmayan özel iç içe ayrılmış bir sınıf olduğuna dikkat edin. Bu ayrıntılar bu sınıfın tüm kullanıcılarından gizlenir.

### <a name="dictionaries"></a>Sözlükler

Başka bir yaygın senaryo, bir sözlük veya harita modellemeniz gerektiğinde. Bu senaryo, türünüzün değerleri genellikle metin tuşlarına göre depolayabOlmasıdır. Bu örnek, komut satırı bağımsız değişkenlerini bu seçenekleri yöneten [lambda ifadelerle](delegates-overview.md) eşleyen bir sözlük oluşturur. Aşağıdaki örnekte iki sınıf `ArgsActions` gösterilmektedir: komut satırı `Action` seçeneğini bir `ArgsProcessor` temsilciyle `ArgsActions` eşleyen `Action` bir sınıf ve bu seçenekle karşılaştığında her birini yürütmek için kullanan bir sınıf.

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

Bu örnekte, `ArgsAction` koleksiyon temel koleksiyona yakından eşler.
Belirli `get` bir seçeneğin yapılandırıp yapılandırılmamadığını belirler. Bu nedenle, bu `Action` seçenekle ilişkili döndürür. Değilse, hiçbir şey `Action` yapmaz bir döner. Ortak erişimci bir `set` erişimci içermez. Bunun yerine, seçenekleri ayarlamak için ortak bir yöntem kullanarak tasarım.

### <a name="multi-dimensional-maps"></a>Çok Boyutlu Haritalar

Birden çok bağımsız değişken kullanan dizin oluşturabilirsiniz. Buna ek olarak, bu bağımsız değişkenler aynı türde sınırlı değildir. İki örnşeye bakalım.

İlk örnek, Mandelbrot kümesi için değerler üreten bir sınıf gösterir. Setin arkasındaki matematik hakkında daha fazla bilgi için [bu makaleyi](https://en.wikipedia.org/wiki/Mandelbrot_set)okuyun.
Dizinleyici, X, Y düzleminde bir noktayı tanımlamak için iki çift kullanır.
Get erişimcisi, bir nokta kümede olmadığı belirlenene kadar yineleme sayısını hesaplar. En büyük yinelemelere ulaşılırsa, nokta kümededir ve sınıfın maxIterations değeri döndürülür. (Mandelbrot kümesi için popüler hale getirilen bilgisayar, bir noktanın kümenin dışında olduğunu belirlemek için gerekli yineleme sayısı için renkleri tanımlar.

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

Mandelbrot Kümesi, gerçek sayı değerleri için her (x,y) koordinatındaki değerleri tanımlar.
Bu, sonsuz sayıda değer içerebilecek bir sözlük tanımlar. Bu nedenle, kümenin arkasında depolama alanı yoktur. Bunun yerine, bu sınıf, kod erişime gireni aradığında her noktanın `get` değerini hesaplar. Temel depolama alanı kullanılmaz.

Dizinleyicinin farklı türde birden çok bağımsız değişken aldığı dizinleyicilerin son bir kullanımını inceleyelim. Geçmiş sıcaklık verilerini yöneten bir program düşünün. Bu dizinleyici, o konum için yüksek ve düşük sıcaklıkları ayarlamak veya elde etmek için bir şehir ve tarih kullanır:

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

Bu örnek, hava durumu verilerini iki farklı bağımsız değişkenüzerinde eşleyen `string`bir dizin oluşturucu oluşturur: bir şehir (a ile temsil edilir) ve bir tarih (bir `DateTime`ile temsil edilir). İç depolama iki `Dictionary` boyutlu sözlüğü temsil etmek için iki sınıf kullanır. Genel API artık temel depolamayı temsil etmez. Bunun yerine, dizin oluşturi erlerin dil özellikleri, temel depolama alanı farklı çekirdek toplama türleri kullanmanız gerekse bile soyutlamanızı temsil eden ortak bir arabirim oluşturmanıza olanak tanır.

Bu kodun bazı geliştiricileriçin yabancı olabilecek iki bölümü vardır. Bu `using` iki ifade:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

oluşturulmuş genel bir tür için bir *takma ad* oluşturun. Bu ifadeler kodun daha sonra genel yapı `DateMeasurements` `CityDateMeasurements` yerine daha açıklayıcı ve `Dictionary<DateTime, Measurements>` `Dictionary<string, Dictionary<DateTime, Measurements> >`adları kullanmasını sağlar ve.
Bu `=` yapı, işaretin sağ tarafında tam nitelikli tür adlarının kullanılmasını gerektirir.

İkinci teknik, koleksiyonları dizine dizine `DateTime` dizin lemek için kullanılan herhangi bir nesnenin zaman bölümlerini şeritlemektir. .NET yalnızca tarih türü içermez.
Geliştiriciler `DateTime` türü kullanır, ancak `Date` o güne `DateTime` ait herhangi bir nesnenin eşit olduğundan emin olmak için özelliği kullanır.

## <a name="summing-up"></a>Özetleme

Sınıfınızda, bu özelliğin tek bir değeri değil, her bir öğenin bir dizi bağımsız değişkentarafından tanımlandığı değerler koleksiyonunu temsil ettiği özellik benzeri bir öğeye sahip olduğunuz her zaman dizin oluşturmalısınız. Bu bağımsız değişkenler, koleksiyondaki hangi öğeye başvurulması gerektiğini benzersiz olarak belirleyebilir.
Dizin [leyiciler,](properties.md)bir üyenin sınıfın dışından gelen bir veri öğesi gibi, ancak içerideki bir yöntem gibi muamele gördüğü özellikler kavramını genişletir. Dizin leyiciler, bağımsız değişkenlerin bir öğe kümesini temsil eden bir özellikte tek bir öğe bulmasına izin verir.
