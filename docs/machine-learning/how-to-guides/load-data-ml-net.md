---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: API'yi kullanarak ML.NET işlemek ve işlemek için verileri nasıl yükleyeceğimiz öğrenin. Veriler dosyalarda, veritabanlarında, JSON'da, XML'de veya bellek içi koleksiyonlarda depolanır.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344749"
---
# <a name="load-data-from-files-and-other-sources"></a>Dosyalardan ve diğer kaynaklardan veri yükleme

API'yi kullanarak ML.NET işlemek ve işlemek için verileri nasıl yükleyeceğimiz öğrenin. Veriler başlangıçta dosyalarda veya veritabanları, JSON, XML veya bellek içi koleksiyonlar gibi diğer veri kaynaklarında depolanır.

Model Oluşturucu kullanıyorsanız, [Model Oluşturucu'ya Yük eğitim verilerine](load-data-model-builder.md)bakın.

## <a name="create-the-data-model"></a>Veri modelini oluşturma

ML.NET, sınıflar aracılığıyla veri modellerini tanımlamanızı sağlar. Örneğin, aşağıdaki giriş verileri göz önüne alındığında:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Aşağıdaki parçacığı temsil eden bir veri modeli oluşturun:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Veri modelini sütun öznitelikleriyle açıklama

Öznitelikler ML.NET veri modeli ve veri kaynağı hakkında daha fazla bilgi verir.

Öznitelik, [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) özelliklerinizin sütun dizinlerini belirtir.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)yalnızca bir dosyadan veri yüklerken gereklidir.

Sütunları şu şekilde yükleyin:

- Sınıf gibi `Size` `CurrentPrices` ve sınıfta ki tek tek sütunlar. `HousingData`
- `HousingData` Sınıftaki gibi `HistoricalPrices` bir vektör şeklinde bir seferde birden çok sütun.

Bir vektör özelliğiniz varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliği veri modelinizdeki özelliğe uygulayın. Vektördeki tüm elementlerin aynı türde olması gerektiğini unutmayın. Sütunları ayrı tutmak özellik mühendisliğinin kolaylığı ve esnekliğini sağlar, ancak çok sayıda sütun için, tek tek sütunlar üzerinde çalışma eğitim hızı üzerinde bir etkiye neden olur.

ML.NET Sütun adları aracılığıyla çalışır. Bir sütunun adını özellik adından başka bir şeyle değiştirmek [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) istiyorsanız, özniteliği kullanın. Bellek içi nesneler oluştururken, özellik adını kullanarak nesneler oluşturmaya devam edebebilirsiniz. Ancak, veri işleme ve makine öğrenme modelleri oluşturmak için, ML.NET geçersiz [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) kılar ve öznitelik sağlanan değeri ile özelliği başvurur.

## <a name="load-data-from-a-single-file"></a>Tek bir dosyadan veri yükleme

Bir dosyadan veri yüklemek [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) için yüklenecek veriler için veri modeli ile birlikte yöntemi kullanın. `separatorChar` Parametre varsayılan olarak sekme delimited olduğundan, gerektiğinde veri dosyanız için değiştirin. Dosyanızın üstbilgisi varsa, parametreyi `hasHeader` `true` dosyadaki ilk satırı yoksayacak şekilde ayarlayın ve ikinci satırdan veri yüklemeye başlayın.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Birden çok dosyadan veri yükleme

Verilerinizin birden çok dosyada depolandığı durumlarda, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizindeki birden çok dosyadan veri yüklemenize olanak tanır.

### <a name="load-from-files-in-a-single-directory"></a>Dosyalardan tek bir dizindeki yükleme

Tüm veri dosyalarınız aynı dizinde olduğunda, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemde joker karakterleri kullanın.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Birden çok dizindeki dosyalardan yükleme

Birden çok dizinden veri [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yüklemek için, [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)bir . Ardından, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemi kullanın ve tek tek dosya yollarını belirtin (joker karakterler kullanılamaz).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>İlişkisel bir veritabanından veri yükleme

ML.NET, SQL Server, Azure SQL Database, [`System.Data`](xref:System.Data) Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve daha birçok kişi tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklemeyi destekler.

> [!NOTE]
> `DatabaseLoader` [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet paketini kullanmak için başvuru.

Adlı `House` bir tablo ve aşağıdaki şema ile bir veritabanı verilmiştir:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Veriler gibi `HouseData`bir sınıf tarafından modellenebilir.

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Daha sonra, uygulamanızın içinde, bir `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu `DatabaseSource` tanımlayın ve bir örnek oluşturun. Bu örnek, dosya yolu olan bir LocalDB SQL Server veritabanı kullanır. Ancak, DatabaseLoader veritabanları için şirket içinde ve bulutta başka geçerli bağlantı dizesini destekler.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Türü [`Real`](xref:System.Data.SqlDbType) olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType). Tür, [`Real`](xref:System.Data.SqlDbType) tek duyarlıklı kayan nokta değeri [`Single`](xref:System.Single)veya ML.NET algoritmaları tarafından beklenen giriş türü olarak temsil edilir. Bu örnekte, `NumBed` sütun veritabanında bir tamsayıdır. `CAST` Yerleşik işlevi kullanılarak, [`Real`](xref:System.Data.SqlDbType)'ye dönüştürülür. `Price` Özellik zaten tür [`Real`](xref:System.Data.SqlDbType) olduğundan olduğu gibi yüklenir.

Verileri `Load` bir [`IDataView`](xref:Microsoft.ML.IDataView)'e yüklemek için yöntemi kullanın.

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Diğer kaynaklardan gelen verileri yükleme

Dosyalarda depolanan verileri yüklemenin yanı sıra, ML.NET aşağıdakileri içeren ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:

- Bellek içi koleksiyonlar
- JSON/XML

Akış kaynaklarıyla çalışırken, ML.NET girişin bellek içi bir koleksiyon biçiminde olmasını beklediğini unutmayın. Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyona biçimlendirdiğinizden emin olun.

Aşağıdaki bellek içi koleksiyon göz önüne alındığında:

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

Bellek içi koleksiyonu yöntemle [`IDataView`](xref:Microsoft.ML.IDataView) bir [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yönteme yükleyin:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)yüklerinin [`IEnumerable`](xref:System.Collections.IEnumerable) iş parçacığı için güvenli olduğunu varsayar.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Sonraki adımlar

- Verileri temizlemek veya başka bir şekilde işlemek [için](prepare-data-ml-net.md)bkz.
- Bir model oluşturmaya hazır olduğunuzda, [Train'e bakın ve bir modeli değerlendirin.](train-machine-learning-model-ml-net.md)
