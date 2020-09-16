---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: API kullanarak ML.NET 'ye işleme ve eğitimle ilgili verileri yüklemeyi öğrenin. Veriler dosyalar, veritabanları, JSON, XML veya bellek içi koleksiyonlar halinde depolanır.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: edcb1c4d00a09ba8404b08ddc3ca3447a52a81b6
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679592"
---
# <a name="load-data-from-files-and-other-sources"></a>Dosyalardan ve diğer kaynaklardan veri yükleme

API kullanarak ML.NET 'ye işleme ve eğitimle ilgili verileri yüklemeyi öğrenin. Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.

Model Oluşturucu kullanıyorsanız bkz. [model Oluşturucu 'da eğitim verilerini yükleme](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Veri modelini oluşturma

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

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)Öznitelik, özelliklerinin sütun dizinlerini belirtir.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) yalnızca bir dosyadan veri yüklenirken gereklidir.

Sütunları şu şekilde yükle:

- Sınıfında ve gibi ayrı sütunlar `Size` `CurrentPrices` `HousingData` .
- Sınıf gibi bir vektör biçiminde tek seferde birden çok sütun `HistoricalPrices` `HousingData` .

Vektör özelliği varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinizdeki özelliğe uygulayın. Vektördeki tüm öğelerin aynı türde olması gerektiğini unutmayın. Sütunların ayrılmış tutulması, özellik mühendisliğinin kolaylığını ve esnekliğini sağlar, ancak çok fazla sayıda sütun için, bireysel sütunlarda çalışan eğitim hızında bir etkiye neden olur.

ML.NET, sütun adlarıyla çalışır. Bir sütunun adını özellik adı dışında bir şekilde değiştirmek istiyorsanız, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın. Bellek içi nesneler oluştururken, hala özellik adını kullanarak nesneler oluşturursunuz. Ancak, veri işleme ve makine öğrenimi modelleri oluşturma için, ML.NET geçersiz kılar ve özelliği özniteliğinde belirtilen değerle başvurur [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .

## <a name="load-data-from-a-single-file"></a>Tek bir dosyadaki verileri yükleme

Bir dosyadan veri yüklemek için [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini, yüklenecek verilerin veri modeliyle birlikte kullanın. `separatorChar`Parametre varsayılan olarak sekmeyle ayrılmış olduğundan, bunu veri dosyanız için gereken şekilde değiştirin. Dosyanızın bir üstbilgisi varsa, `hasHeader` parametresini `true` dosyadaki ilk satırı yoksayacak şekilde ayarlayın ve ikinci satırdan verileri yüklemeye başlayın.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Birden çok dosyadan veri yükleme

Verilerinizin birden çok dosyada depolandığından, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizinde bulunan birden çok dosyadan veri yüklemenize izin verir.

### <a name="load-from-files-in-a-single-directory"></a>Tek bir dizindeki dosyalardan yükleme

Tüm veri dosyalarınız aynı dizinde olduğunda, yönteminde joker karakterler kullanın [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Birden çok dizindeki dosyalardan yükleme

Birden çok dizindeki verileri yüklemek için [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) yöntemini kullanarak bir oluşturun [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) . Ardından, yöntemini kullanın [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) ve tek dosya yollarını belirtin (joker karakterler kullanılamaz).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>İlişkisel veritabanından veri yükleme

ML.NET [`System.Data`](xref:System.Data) , SQL Server, Azure SQL veritabanı, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve çok daha fazlasını içeren, tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklenmesini destekler.

> [!NOTE]
> Kullanmak için `DatabaseLoader` [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet paketine başvurun.

Adlı bir tablo ve aşağıdaki şemaya sahip bir veritabanı verildi `House` :

```sql
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Veriler, gibi bir sınıfa göre modellenebilir `HouseData` .

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Ardından, uygulamanızın içinde bir oluşturun `DatabaseLoader` .

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu ve bir örnek oluşturmayı tanımlayın `DatabaseSource` . Bu örnek, bir LocalDB SQL Server veritabanını bir dosya yolu ile kullanır. Ancak DatabaseLoader, şirket içi ve buluttaki veritabanları için geçerli olan diğer bağlantı dizelerini destekler.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Türünde olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType) dönüştürülecek olması gerekiyor [`Real`](xref:System.Data.SqlDbType) . [`Real`](xref:System.Data.SqlDbType)Tür tek duyarlıklı kayan nokta değeri veya [`Single`](xref:System.Single) ml.net algoritmaları tarafından beklenen giriş türü olarak temsil edilir. Bu örnekte, `NumBed` sütunu veritabanındaki bir tamsayıdır. `CAST`Yerleşik işlevi kullanılarak, öğesine dönüştürülür [`Real`](xref:System.Data.SqlDbType) . Özelliği zaten olduğu için, `Price` özelliği [`Real`](xref:System.Data.SqlDbType) olduğu gibi yüklenmiş.

' `Load` A veri yüklemek için yöntemini kullanın [`IDataView`](xref:Microsoft.ML.IDataView) .

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

Bellek içi toplamayı, yöntemiyle bir öğesine yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) :

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) , ' [`IEnumerable`](xref:System.Collections.IEnumerable) den yüklendiği varsayılmaktadır, iş parçacığı güvenlidir.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Sonraki adımlar

- Verileri temizlemek veya başka bir şekilde işlemek için bkz. [model oluşturmak için veri hazırlama](prepare-data-ml-net.md).
- Model oluşturmaya hazırsanız, bkz. [modeli eğitme ve değerlendirme](train-machine-learning-model-ml-net.md).
