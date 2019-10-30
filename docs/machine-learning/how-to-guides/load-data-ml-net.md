---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir. Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 82a4d19a6296faa6d195e301016b1bf97d483a2c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040797"
---
# <a name="load-data-from-files-and-other-sources"></a>Dosyalardan ve diğer kaynaklardan veri yükleme

Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir. Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.

## <a name="create-the-data-model"></a>Veri modeli oluşturma

ML.NET, sınıflar aracılığıyla veri modelleri tanımlamanıza olanak sağlar. Örneğin, aşağıdaki giriş verileri verildiğinde:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Aşağıdaki kod parçacığını temsil eden bir veri modeli oluşturun:

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a>Sütun öznitelikleriyle veri modeline açıklama ekleme

Öznitelikler, veri modeli ve veri kaynağı hakkında ML.NET daha fazla bilgi verir.

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliği, özelliklerinin sütun dizinlerini belirtir.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) yalnızca bir dosyadan veri yüklenirken gereklidir.

Sütunları şu şekilde yükle:

- `HousingData` sınıfında `Size` ve `CurrentPrices` gibi bireysel sütunlar.
- `HousingData` sınıfında `HistoricalPrices` benzer bir vektör biçiminde tek seferde birden çok sütun.

Vektör özelliği varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinizdeki özelliğe uygulayın. Vektördeki tüm öğelerin aynı türde olması gerektiğini unutmayın. Sütunların ayrılmış tutulması, özellik mühendisliğinin kolaylığını ve esnekliğini sağlar, ancak çok fazla sayıda sütun için, bireysel sütunlarda çalışan eğitim hızında bir etkiye neden olur.

ML.NET, sütun adlarıyla çalışır. Bir sütunun adını özellik adı dışında bir şekilde değiştirmek istiyorsanız, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın. Bellek içi nesneler oluştururken, hala özellik adını kullanarak nesneler oluşturursunuz. Ancak, veri işleme ve makine öğrenimi modelleri oluşturma için ML.NET, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğinde belirtilen değeri geçersiz kılar ve özelliğe başvurur.

## <a name="load-data-from-a-single-file"></a>Tek bir dosyadaki verileri yükleme

Bir dosyadan veri yüklemek için, yüklenecek verilerin veri modeliyle birlikte [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemini kullanın. `separatorChar` parametre varsayılan olarak sekmeyle ayrılmış olduğundan, bunu veri dosyanız için gereken şekilde değiştirin. Dosyanızın bir üstbilgisi varsa, dosyadaki ilk satırı yoksaymak ve ikinci satırdan verileri yüklemeye başlamak için `hasHeader` parametresini `true` olarak ayarlayın.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Birden çok dosyadan veri yükleme

Verilerinizin birden çok dosyada depolandığından, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizinde bulunan birden çok dosyadan veri yüklemenize izin verir.

### <a name="load-from-files-in-a-single-directory"></a>Tek bir dizindeki dosyalardan yükleme

Tüm veri dosyalarınız aynı dizinde olduğunda, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yönteminde joker karakterler kullanın.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Birden çok dizindeki dosyalardan yükleme

Birden çok dizindeki verileri yüklemek için [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemi kullanarak bir [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)oluşturun. Sonra, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemini kullanın ve tek dosya yollarını belirtin (joker karakterler kullanılamaz).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>İlişkisel veritabanından veri yükleme

> [!NOTE]
> DatabaseLoader Şu anda önizleme aşamasındadır. [Microsoft. ml. deneysel](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) ve [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet paketlerine başvurarak kullanılabilir.

ML.NET, SQL Server, Azure SQL veritabanı, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve çok daha fazlasını içeren [`System.Data`](xref:System.Data) tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklenmesini destekler.

`House` adlı bir tabloya ve aşağıdaki şemaya sahip bir veritabanı verilirler:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Veriler `HouseData`gibi bir sınıfla modellenebilir.

```csharp
public class HouseData
{
    public float Size { get; set; }
    
    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Ardından, uygulamanızın içinde bir `DatabaseLoader`oluşturun.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu ve bir `DatabaseSource` örneği oluşturmayı tanımlayın. Bu örnek, bir LocalDB SQL Server veritabanını bir dosya yolu ile kullanır. Ancak DatabaseLoader, şirket içi ve buluttaki veritabanları için geçerli olan diğer bağlantı dizelerini destekler.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

[`Real`](xref:System.Data.SqlDbType) türünde olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType)dönüştürülecek olması gerekiyor. [`Real`](xref:System.Data.SqlDbType) türü tek duyarlıklı kayan nokta değeri veya [`Single`](xref:System.Single), ml.net algoritmaları tarafından beklenen giriş türü olarak temsil edilir. Bu örnekte, `NumBed` sütunu veritabanındaki bir tamsayıdır. `CAST` yerleşik işlevini kullanarak [`Real`](xref:System.Data.SqlDbType)dönüştürülür. `Price` özelliği zaten tür olduğundan [`Real`](xref:System.Data.SqlDbType) olduğu gibi yüklenir.

Verileri bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklemek için `Load` yöntemi kullanın.

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Diğer kaynaklardan veri yükleme

ML.NET, dosyalarda depolanan verileri yüklemeye ek olarak, dahil edilen ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:

- Bellek içi Koleksiyonlar
- JSON/XML

Akış kaynaklarıyla çalışırken ML.NET, girişin bellek içi koleksiyon biçiminde olmasını bekler. Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyonda biçimlediğinizden emin olun.

Aşağıdaki bellek içi koleksiyon verildiğinde:

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemi ile bir [`IDataView`](xref:Microsoft.ML.IDataView) bellek içi toplamayı yükleyin:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) , tarafından yüklendiği [`IEnumerable`](xref:System.Collections.IEnumerable) iş parçacığı açısından güvenli olduğunu varsayar.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Sonraki adımlar

Makine öğrenimi modelini eğiteiçin model Oluşturucu kullanıyorsanız bkz. [model Oluşturucu 'da eğitim verilerini yükleme](load-data-model-builder.md).
