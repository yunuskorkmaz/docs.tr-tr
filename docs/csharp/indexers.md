---
title: Dizin Oluşturucular
description: C# Dizin oluşturucular ve bunların bir veya daha fazla bağımsız değişken kullanılarak başvurulan özellikler olan dizinli özellikleri nasıl uygulayabileceği hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: e9b1cb18157982f068f1c1e4546e637f2bd707cb
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394695"
---
# <a name="indexers"></a>Dizin Oluşturucular

*Dizin oluşturucular* özelliklere benzerdir. Birçok şekilde, Dizin oluşturucular [Özellikler](properties.md)ile aynı dil özelliklerinde yapı oluşturur. Dizin oluşturucular *dizinli* özellikleri etkinleştirir: bir veya daha fazla bağımsız değişken kullanılarak başvurulan Özellikler. Bu bağımsız değişkenler, bazı değer toplamasına bir dizin sağlar.

## <a name="indexer-syntax"></a>Dizin Oluşturucu sözdizimi

Bir dizin oluşturucuya bir değişken adı ve köşeli ayraçlar aracılığıyla erişirsiniz. Dizin Oluşturucu bağımsız değişkenlerini köşeli ayraç içine yerleştirebilirsiniz:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

`this`Özellik adı olarak anahtar sözcüğünü kullanarak Dizin oluşturucular bildirir ve bağımsız değişkenleri köşeli ayraç içinde bildirir. Bu bildirim, önceki paragrafta gösterilen kullanımla eşleşir:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Bu ilk örnekte, Özellikler ve Dizin oluşturucular için sözdizimi arasındaki ilişkiyi görebilirsiniz. Bu benzerleme vurguladı, Dizin oluşturucular için sözdizimi kurallarının çoğunu taşır. Dizin oluşturucular geçerli erişim değiştiricilerine sahip olabilir (genel, korunan dahili, korunan, iç, özel veya özel korumalı). Mühürlü, sanal veya soyut olabilir. Özelliklerde olduğu gibi, bir dizin oluşturucuda get ve set erişimcileri için farklı erişim değiştiricileri belirtebilirsiniz.
Salt yazılır Dizin oluşturucular da (set erişimcisini atlayarak) veya salt yazılır Dizin oluşturucular (Get erişimcisini atlayarak) belirtebilirsiniz.

Özelliklerle birlikte çalışarak, dizin oluşturucularının bulunduğu neredeyse her şeyi uygulayabilirsiniz. Bu kuralın tek istisnası *Otomatik uygulanan özelliklerdir*. Derleyici, Dizin Oluşturucu için her zaman doğru depolama alanı oluşturamıyor.

Bir öğe kümesindeki bir öğeye başvuruda bulunmak için bağımsız değişkenlerin varlığı, dizin oluşturucularının özelliklerini ayırır. Her bir dizin oluşturucunun bağımsız değişken listeleri benzersiz olduğu sürece, bir tür üzerinde birden çok Dizin Oluşturucu tanımlayabilirsiniz. Bir sınıf tanımında bir veya daha fazla Dizin Oluşturucu kullanabileceğiniz farklı senaryolar araştıralım.

## <a name="scenarios"></a>Senaryolar

API 'sinin, bu koleksiyonun bağımsız değişkenlerini tanımladığınız bazı koleksiyonları modellediğinde, bu *Dizin* oluşturucuyu yazmanız gerekir. Dizin oluşturucular, .NET Core Framework 'ün parçası olan koleksiyon türleri ile doğrudan eşleşmeyebilir veya eşleşmeyebilir. Bir koleksiyonun modellenmesi ek olarak, türü başka sorumluluklara sahip olabilir.
Dizin oluşturucular, bu soyutlamalarda değerlerinin nasıl depolandığını veya hesaplanmadığını belirten iç ayrıntıları açığa çıkarmadan, türün soyutlamada eşleşen API 'yi sağlamanıza olanak tanır.

*Dizin oluşturucular*kullanmanın bazı yaygın senaryolarından bazılarını inceleyelim. [Dizin oluşturucular için örnek klasöre](https://github.com/dotnet/samples/tree/master/csharp/indexers)erişebilirsiniz. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Diziler ve vektörler

Dizin oluşturucular oluşturmak için en yaygın senaryolardan biri, türü bir diziyi veya bir vektörü modellediğinde olur. Sıralı bir veri listesini modellemek için bir Dizin Oluşturucu oluşturabilirsiniz.

Kendi dizin oluşturucuyu oluşturmanın avantajı, bu koleksiyonun depolama alanını gereksinimlerinize uyacak şekilde tanımlayabilmeniz. Aynı anda belleğe yüklenecek çok büyük geçmiş verileri modelleyen bir senaryoyu düşünün. Kullanım temelinde koleksiyonun bölümlerini yüklemeniz ve kaldırmanız gerekir. Aşağıdaki örnek, bu davranışı modelleyen bir örnektir. Bu, kaç veri noktasının var olduğunu bildirir. İsteğe bağlı verilerin bölümlerini tutacak sayfalar oluşturur. Daha yeni istekler için gereken sayfalar için yer açmak üzere sayfaları bellekten kaldırır.

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

Tüm veri kümesinin bellek içi bir koleksiyona yüklenmesinin iyi nedenleri olduğu durumlarda, herhangi bir koleksiyon sıralamasını modellemek için bu tasarım deyimlerini takip edebilirsiniz. `Page`Sınıfın, ortak arabirimin parçası olmayan bir özel iç içe sınıfı olduğuna dikkat edin. Bu ayrıntılar, bu sınıfın tüm kullanıcılarından gizlenir.

### <a name="dictionaries"></a>Sözlükler

Diğer bir yaygın senaryo, bir sözlüğü veya eşlemeyi modellemenize gerek duyduğunuzda olur. Bu senaryo, yazdığınız değerleri anahtar temelinde, genellikle metin anahtarlarına göre depoladığında olur. Bu örnek, komut satırı bağımsız değişkenlerini bu seçenekleri yöneten [lambda ifadelerine](delegates-overview.md) eşleyen bir sözlük oluşturur. Aşağıdaki örnek iki sınıf göstermektedir: bir `ArgsActions` komut satırı seçeneğini bir temsilci ile eşleyen bir sınıf `Action` ve bu `ArgsProcessor` `ArgsActions` seçenekle her karşılaştığında yürütmek için öğesini kullanır `Action` .

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

Bu örnekte, koleksiyon, `ArgsAction` temel alınan koleksiyona yakından eşlenir.
`get`Verilen bir seçeneğin yapılandırılıp yapılandırılmadığını belirler. Varsa, `Action` Bu seçenekle ilişkili öğesini döndürür. Aksi takdirde, `Action` hiçbir şey yapmaz. Ortak erişimci bir `set` erişimci içermez. Bunun yerine, seçenekleri ayarlamak için genel bir yöntem kullanan tasarım.

### <a name="multi-dimensional-maps"></a>Çok boyutlu haritalar

Birden çok bağımsız değişken kullanan Dizin oluşturucular oluşturabilirsiniz. Ayrıca, bu bağımsız değişkenler aynı türde olacak şekilde kısıtlanmaz. İki örneğe bakalım.

İlk örnek, bir Mandeli kümesi için değerler üreten bir sınıfı gösterir. Küme arkasında matematik hakkında daha fazla bilgi için [Bu makaleyi](https://en.wikipedia.org/wiki/Mandelbrot_set)okuyun.
Dizin Oluşturucu X, Y düzleinde bir noktayı tanımlamak için iki Double Double kullanır.
Get erişimcisi, bir noktanın küme içinde olmadığı belirlenene kadar yineleme sayısını hesaplar. En fazla yineleme ulaşılırsa, nokta ayarlanmıştır ve sınıfın Maxyinelemelerde değeri döndürülür. (Bilgisayar tarafından üretilen görüntüler Mandeli kümesi için populartı kümesi, bir noktanın kümenin dışında olduğunu belirlemek için gereken yineleme sayısı için renkleri tanımlar.

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

Mandelbrot kümesi, gerçek sayı değerleri için her (x, y) koordinatının değerlerini tanımlar.
Bu, sonsuz sayıda değer içerebilen bir sözlük tanımlar. Bu nedenle, küme arkasında depolama yok. Bunun yerine, kod erişimciyi çağırdığında, bu sınıf her bir noktanın değerini hesaplar `get` . Kullanılan temeldeki depolama alanı yok.

Dizin oluşturucunun, farklı türlerde birden çok bağımsız değişken aldığı dizin oluşturucularının bir son kullanımını inceleyelim. Geçmiş sıcaklık verilerini yöneten bir programı düşünün. Bu Dizin Oluşturucu, bu konum için yüksek ve düşük sıcaklıkları ayarlamak veya almak üzere bir şehir ve bir tarih kullanır:

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

Bu örnek, hava durumu verilerini iki farklı bağımsız değişkenle eşleyen bir dizin oluşturucu oluşturur: şehir (bir ile temsil edilir `string` ) ve bir tarih (ile temsil edilir `DateTime` ). İç depolama `Dictionary` iki boyutlu sözlüğü temsil etmek için iki sınıf kullanır. Ortak API artık temeldeki depolamayı temsil etmektedir. Bunun yerine, dizin oluşturucularının dil özellikleri, temeldeki depolamanın farklı çekirdek koleksiyon türlerini kullanması gerekir ancak, soyutlamasını temsil eden bir ortak arabirim oluşturmanıza olanak sağlar.

Bu kodun, bazı geliştiricilere alışkın olabilecek iki bölümü vardır. Bu iki `using` yönergeler:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

oluşturulan genel tür için bir *diğer ad* oluşturun. Bu deyimler, daha sonra, `DateMeasurements` `CityDateMeasurements` ve ' nin genel yapımı yerine daha açıklayıcı ve adların kullanılmasını sağlar `Dictionary<DateTime, Measurements>` `Dictionary<string, Dictionary<DateTime, Measurements> >` .
Bu yapı, işaretin sağ tarafında tam nitelikli tür adlarının kullanılmasını gerektirir `=` .

İkinci yöntem, `DateTime` koleksiyonlara dizin eklemek için kullanılan herhangi bir nesnenin zaman kısımlarını çıkaramadır. .NET yalnızca Tarih türünde bir tür içermez.
Geliştiriciler türünü kullanır `DateTime` , ancak `Date` `DateTime` Bu güne ait herhangi bir nesnenin eşit olduğundan emin olmak için özelliğini kullanın.

## <a name="summing-up"></a>Toplam

Sınıfınıza, bu özelliğin tek bir değer değil, her tekil öğenin bir dizi bağımsız değişken tarafından tanımlandığı bir değer koleksiyonu olmak üzere her zaman bir özellik benzeri öğe oluşturmanız gerekir. Bu bağımsız değişkenler koleksiyondaki hangi öğeye başvurulduğunu benzersiz şekilde tanımlayabilir.
Dizin oluşturucular, bir üyenin sınıfın dışından bir veri öğesi gibi davranılabileceği, ancak içindeki bir yöntem gibi ele alındığı [Özellikler](properties.md)kavramını genişletir. Dizin oluşturucular, bağımsız değişkenlerin bir öğe kümesini temsil eden özellikte tek bir öğe bulmasına izin verir.
