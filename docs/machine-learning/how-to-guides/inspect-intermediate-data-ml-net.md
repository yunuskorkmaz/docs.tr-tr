---
title: ML.NET işleme sırasında ara verileri İnceleme
description: ML.NET ' de ML.NET Machine Learning işlem hattı yükleme, işleme ve model oluşturma adımları sırasında ara verileri incelemeyi öğrenin.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977100"
---
# <a name="inspect-intermediate-data-during-processing"></a>İşlem sırasında ara verileri İncele

ML.NET ' de yükleme, işleme ve model eğitimi adımları sırasında ara verileri incelemeyi öğrenin. Ara veri, makine öğrenimi ardışık düzeninde her bir aşamanın çıktısıdır.

Aşağıda temsil edilen bir [`IDataView`](xref:Microsoft.ML.IDataView) gibi ara veriler, ml.NET içinde çeşitli yollarla incelenebilir.

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

## <a name="convert-idataview-to-ienumerable"></a>Idataview öğesini IEnumerable 'a Dönüştür

Bir [`IDataView`](xref:Microsoft.ML.IDataView) incelemeyi en hızlı yolu bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)dönüştürmelidir. Bir [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürmek için [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metodunu kullanın.

Performansı iyileştirmek için `reuseRowObject` `true`olarak ayarlayın. Bunun yapılması, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirilmekte olduğundan aynı nesneyi geçerli satırın verileriyle doldurgeç.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>IEnumerable ile belirli dizinlerine erişme

Yalnızca verilerin veya belirli dizinlerin bir kısmına erişmeniz gerekiyorsa [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) kullanın ve `reuseRowObject` parametre değerini `false` olarak ayarlayın. bu nedenle veri kümesindeki istenen her bir satır için yeni bir nesne oluşturulur. Ardından [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir diziye veya listeye dönüştürün.

> [!WARNING]
> [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) sonucunu bir diziye veya listeye dönüştürmek, istenen tüm [`IDataView`](xref:Microsoft.ML.IDataView) satırlarını belleğe yükler ve bu da performansı etkileyebilir.

Koleksiyon oluşturulduktan sonra, veriler üzerinde işlemler gerçekleştirebilirsiniz. Aşağıdaki kod parçacığı, veri kümesindeki ilk üç satırı alır ve ortalama geçerli fiyatı hesaplar.

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

## <a name="inspect-values-in-a-single-column"></a>Tek bir sütundaki değerleri İnceleme

Model oluşturma işlemindeki herhangi bir noktada, [`IDataView`](xref:Microsoft.ML.IDataView) tek bir sütunundaki değerlere [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi kullanılarak erişilebilir. [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi, tek bir sütundaki tüm değerleri [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)olarak döndürür.

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Idataview değerlerini tek seferde bir satır olarak İnceleme

[`IDataView`](xref:Microsoft.ML.IDataView) geç değerlendirilir. Bu belgenin önceki bölümlerinde gösterildiği gibi bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürmeden [`IDataView`](xref:Microsoft.ML.IDataView) satırlarını yinelemek için, [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemini kullanarak bir [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) oluşturun ve bir parametre olarak [`IDataView`](xref:Microsoft.ML.IDataView) [DataViewSchema](xref:Microsoft.ML.DataViewSchema) . Daha sonra, satırları yinelemek için, her sütundan ilgili değerleri ayıklamak üzere [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) temsilcilerle birlikte [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) Cursor metodunu kullanın.

> [!IMPORTANT]
> Performans amaçlarıyla, ML.NET içindeki vektörler yerel koleksiyon türleri yerine [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) kullanır (yani, `Vector`,`float[]`).

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Verilerin bir alt kümesinde ön işleme veya eğitime ilişkin önizleme sonucu

> [!WARNING]
> Hata ayıklama için tasarlanan ve performansı azaltabileceğinden üretim kodunda `Preview` kullanmayın.

Model oluşturma işlemi deneysel ve yinelemeli bir işlemdir. Bir makine öğrenimi modelini verilerin bir alt kümesinde ön işlemden sonra veya öğreticduktan sonra hangi verilerin göründüğünü önizlemek için, bir [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)döndüren [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini kullanın. Sonuç, hem [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) hem de belirli bir sütun veya satırdaki değerleri içeren `ColumnView` ve `RowView` özelliklerine sahip bir nesnedir. `maxRows` parametresine dönüşüm uygulanacak satır sayısını belirtin.

![Veri hata ayıklayıcısı önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Bir [`IDataView`](xref:Microsoft.ML.IDataView) inceleme sonucu aşağıdakine benzer olacaktır:

![Veri hata ayıklayıcısı önizleme satırı görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
