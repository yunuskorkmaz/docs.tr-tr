---
title: ML.NET işleme sırasında ara veri değerlerini İnceleme
description: Ardışık Düzen işleme öğrenme ML.NET makine sırasında gerçek ara veri değerlerini incelemek hakkında bilgi edinin
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 06c4a473841db62a10dfc24025f842df7ae2c583
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063511"
---
# <a name="inspect-intermediate-data-values-during-processing"></a>İşleme sırasında ara veri değerlerini İnceleme

Yükleniyor, işleme ve ML.NET eğitim adımları sırasında değerlerini İnceleme öğrenin.

İster temsil edilen bir veri uygulamasına yüklendiği aşağıda bir [ `IDataView` ](xref:Microsoft.ML.IDataView) ML.NET çeşitli şekillerde inceledi.
 
```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a>IDataView IEnumerable öğesine dönüştürme

Değerlerini incelemek için hızlı şekilde bir [ `IDataView` ](xref:Microsoft.ML.IDataView) öğesine dönüştürmek için olan bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601). Dönüştürülecek bir [ `IDataView` ](xref:Microsoft.ML.IDataView) için [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) kullanın [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi. 

Performansı iyileştirmek için değerini ayarlamak `reuseRowObject` için `true`. Bunun yapılması her satır için yeni bir nesne içinde veri kümesi oluşturma yerine değerlendiriliyor gibi gevşek aynı nesneyi geçerli satırın verilerle dolduracaksınız.

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

Yalnızca bir kısmı veriler veya belirli dizinleri erişmeniz kullanırsanız [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve `reuseRowObject` parametre değerine `false` için istenen satır kümesindeki her biri için yeni bir nesne oluşturulur. Ardından, dönüştürme [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) bir dizi veya listesi.

> [!WARNING]
> Dönüştürme sonucunu [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) bir dizi veya listesini yükler istenen [ `IDataView` ](xref:Microsoft.ML.IDataView) satırları belleğe performansı etkilenebilir.

Koleksiyon oluşturulduktan sonra veriler üzerinde işlemler gerçekleştirebilir. Aşağıdaki kod parçacığında, kümesinde ilk üç satır alır ve ortalama geçerli fiyat hesaplar.

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
``` 

## <a name="inspect-values-in-a-single-column"></a>Tek bir sütunda bulunan değerleri inceleyin

Modeldeki herhangi bir noktada oluşturma işlemi, değerler tek bir sütunda bir [ `IDataView` ](xref:Microsoft.ML.IDataView) kullanılarak erişilebilir [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi. [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Yöntemi tek bir sütundaki tüm değerleri döndürür bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Aynı anda IDataView değerleri bir satır inceleyin

[`IDataView`](xref:Microsoft.ML.IDataView) Gevşek değerlendirilir. Satırları yinelemek için bir [ `IDataView` ](xref:Microsoft.ML.IDataView) dönüştürme olmadan bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) bu belgenin önceki bölümlerde gösterildiği gibi oluşturun bir [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) kullanarak [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemi ve geçirmeye [DataViewSchema](xref:Microsoft.ML.DataViewSchema) , uygulamanızın [ `IDataView` ](xref:Microsoft.ML.IDataView) bir parametre olarak. Ardından satırları yineleme yapmak için kullanın [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) imleç yöntemi ile birlikte [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) her sütun ilgili değerlerini ayıklamak için temsilci.

> [!IMPORTANT]
> ML.NET kullanımda performans amacıyla vektörlerine [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) yerel koleksiyon türleri yerine (diğer bir deyişle, `Vector`,`float[]`). 

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);
    
    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Önizleme sonuçlarını ön işleme veya verilerin bir alt kümesi üzerinde eğitim

> [!WARNING]
> Kullanmayın `Preview` üretim aşamasında hata ayıklama için tasarlanmıştır ve performansını düşürebilir, çünkü kod.

Oluşturma işlemi Deneysel ve yinelemeli modelidir. Hangi veri ön işleme sonra görünmesi mi makine öğrenimi modeli verilerin bir alt kümesi üzerinde kullanmak önizlemek için [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) döndüren yöntemi bir [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview). Sonuç ile bir nesnedir `ColumnView` ve `RowView` her ikisi de özellikleri bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) ve belirli bir sütun veya satır değerler içermelidir. Dönüşüm ile uygulamak için satır sayısını belirtin `maxRows` parametresi.

![Veri hata ayıklayıcı Önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

İnceleme sonucunu bir [ `IDataView` ](xref:Microsoft.ML.IDataView) aşağıdakine benzer olacaktır:

![Veri hata ayıklayıcı Önizleme satır görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
