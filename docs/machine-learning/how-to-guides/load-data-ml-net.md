---
title: Dosyaları ve diğer kaynaklardan veri yükleme
description: Bu nasıl yapılır ML.NET içinde veri işleme ve eğitim için yükleme işlemini göstermektedir. Verileri özgün dosyalar veya veritabanları, JSON, XML veya bellek içi koleksiyonları gibi diğer veri kaynaklarında depolanır.
ms.date: 06/25/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: fafbe3fed9e3f0b509eda4f9d8967965bde19767
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397741"
---
# <a name="load-data-from-files-and-other-sources"></a>Dosyaları ve diğer kaynaklardan veri yükleme

Bu nasıl yapılır ML.NET içinde veri işleme ve eğitim için yükleme işlemini göstermektedir. Verileri özgün dosyalar veya veritabanları, JSON, XML veya bellek içi koleksiyonları gibi diğer veri kaynaklarında depolanır.

## <a name="create-the-data-model"></a>Veri modeli oluşturma

ML.NET sınıfları aracılığıyla veri modelleri tanımlamanıza olanak sağlar. Örneğin, aşağıdaki giriş verileri verilen:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Aşağıdaki kod parçacığında temsil eden bir veri modeli oluşturun:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Veri modeli sütunu özniteliklerle ek açıklama ekleme

Öznitelikleri ML.NET veri modeli ve veri kaynağı hakkında daha fazla bilgi verin.

[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Öznitelik özellikleri sütun dizinleri belirtir.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) olan yalnızca bir dosyadan verileri yüklenirken gereklidir.

Sütun olarak yükle: 
- Her bir sütun ister `Size` ve `CurrentPrices` içinde `HousingData` sınıfı.
- Bir vektör biçiminde bir zaman birden çok sütun ister `HistoricalPrices` içinde `HousingData` sınıfı.

Bir vektör özelliği varsa, uygulama [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) veri modelinizde özellik özniteliği. Vektördeki tüm öğeleri aynı türde olması gerektiğini unutmayın.

ML.NET Operates aracılığıyla sütun adları. Özellik adı dışında bir şey bir sütunun adını değiştirmek istiyorsanız, kullanın [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği. Bellek içi nesneleri oluştururken, yine de özellik adı'nı kullanarak nesne oluşturun. Ancak, veri işleme ve yapı makine öğrenimi modellerini, ML.NET geçersiz kılar ve sağlanan değerle özelliğine başvuruyor [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği.

## <a name="load-data-from-a-single-file"></a>Tek bir dosyadan veri yükleme

Bir dosya kullanımdan verileri yüklemek için [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) veri modeline yüklenen verilerin yanı sıra yöntemi. Bu yana `separatorChar` parametre varsayılan olarak sekmeyle, veri dosyanızın gerektiği gibi değiştirin. Üstbilgi dosyanız varsa Ayarla `hasHeader` parametresi `true` dosyanın ilk satırı yoksay ve ikinci satırında veri yüklemeye başlamak için.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Birden çok dosyadan veri yükleme

Aynı veri şemasını olduğu sürece, verilerinizi birden çok dosyasında depolanır, olay, ML.NET, veri ya da aynı dizinde olan birden çok dosya ya da birden çok dizini sağlar.

### <a name="load-from-files-in-a-single-directory"></a>Tek bir dizindeki dosyaları yükleme

Tüm veri dosyaları aynı dizinde olduğunda, joker [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemi.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Birden çok dizinlerde dosyaları yükleme

Birden çok dizinlerden verileri yüklemek için kullanmak [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemi oluşturmak için bir [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader). Ardından, [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemi ve (joker karakterler kullanılamaz) tek tek dosya yollarını belirtin.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a>Diğer kaynaklardan veri yükleme

ML.NET dosyalarında depolanan verileri yüklenirken yanı sıra dahil ancak bunlarla sınırlı olmayan kaynaklardan veri yükleme destekler:

- Bellek içi koleksiyonları
- JSON/XML
- Veritabanları

ML.NET kaynakları akış ile çalışırken, bir bellek içi koleksiyonun biçiminde olması için giriş girmeniz gerektiğini unutmayın. Bu nedenle, JSON/XML gibi kaynaklar ile çalışırken, bir bellek içi koleksiyona verilerin biçimlendirilmesi emin olun.

Şu bellek içi koleksiyonu verilen:

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

Bellek içi koleksiyona bir [ `IDataView` ](xref:Microsoft.ML.IDataView) ile [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemi:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
