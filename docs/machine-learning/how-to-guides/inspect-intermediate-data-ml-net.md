---
title: ML.NET işleme sırasında ara verileri İnceleme
description: ML.NET ' de ML.NET Machine Learning işlem hattı yükleme, işleme ve model oluşturma adımları sırasında ara verileri incelemeyi öğrenin.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4f168653297594a604e6f381947f31cba5376178
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679631"
---
# <a name="inspect-intermediate-data-during-processing"></a>İşlem sırasında ara verileri İncele

ML.NET ' de yükleme, işleme ve model eğitimi adımları sırasında ara verileri incelemeyi öğrenin. Ara veri, makine öğrenimi ardışık düzeninde her bir aşamanın çıktısıdır.

Aşağıda gösterildiği gibi, bir ' a yüklenmiş bir gibi ara veriler, [`IDataView`](xref:Microsoft.ML.IDataView) ml.NET içinde çeşitli yollarla incelenebilir.

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

' Yi incelemeyi en hızlı yöntemlerinden biri bir ' a [`IDataView`](xref:Microsoft.ML.IDataView) dönüştürmelidir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) . ' A dönüştürmek [`IDataView`](xref:Microsoft.ML.IDataView) için [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) yöntemini kullanın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) .

Performansı iyileştirmek için, `reuseRowObject` olarak ayarlayın `true` . Bunun yapılması, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirilmekte olduğundan aynı nesneyi geçerli satırın verileriyle doldurgeç.

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

Yalnızca verilerin veya belirli dizinlerin bir kısmına erişmeniz gerekiyorsa, veri [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) `reuseRowObject` `false` kümesindeki istenen satırların her biri için yeni bir nesne oluşturulması için parametre değerini kullanın ve olarak ayarlayın. Ardından, öğesini [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir diziye veya listeye dönüştürün.

> [!WARNING]
> Sonucunu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) bir diziye veya listeye dönüştürmek, istenen tüm [`IDataView`](xref:Microsoft.ML.IDataView) satırları belleğe yükler ve bu da performansı etkileyebilir.

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

Model oluşturma işlemindeki herhangi bir noktada, tek bir sütunundaki değerlere [`IDataView`](xref:Microsoft.ML.IDataView) yöntemi kullanılarak erişilebilir [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) . [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A)Yöntemi, tek bir sütundaki tüm değerleri bir olarak döndürür [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) .

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Idataview değerlerini tek seferde bir satır olarak İnceleme

[`IDataView`](xref:Microsoft.ML.IDataView) geç değerlendirilir. [`IDataView`](xref:Microsoft.ML.IDataView)Bu belgenin önceki bölümlerinde gösterildiği gibi, bir öğesine dönüştürme yapmadan satırları yinelemek için [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) , [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) yöntemini kullanarak bir oluşturun ve bir [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) parametresi olarak [DataViewSchema](xref:Microsoft.ML.DataViewSchema) ' ı geçirin [`IDataView`](xref:Microsoft.ML.IDataView) . Daha sonra, satırları yinelemek için, [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) her bir sütundan ilgili değerleri ayıklamak üzere, imleç yöntemi ile birlikte kullanın.

> [!IMPORTANT]
> Performans amaçları için, yerel koleksiyon türleri yerine ML.NET kullanımdaki vektörler (yani, [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) `Vector` `float[]` ).

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
> `Preview`Hata ayıklama için tasarlanan ve performansı azaltabileceğinden üretim kodunda kullanmayın.

Model oluşturma işlemi deneysel ve yinelemeli bir işlemdir. Verilerin bir alt kümesindeki bir makine öğrenimi modelini ön işlemden sonra veya öğreticduktan sonra, verilerin nasıl göründüğünü önizlemek için, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) döndüren yöntemini kullanın [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview) . Sonuç, ve özelliklerine sahip olan `ColumnView` ve `RowView` belirli bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) sütun veya satırdaki değerleri içeren bir nesnedir. Parametreye, dönüşüme uygulanacak satır sayısını belirtin `maxRows` .

![Veri hata ayıklayıcısı önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

İnceleme sonucu aşağıdakine [`IDataView`](xref:Microsoft.ML.IDataView) benzer şekilde görünür:

![Veri hata ayıklayıcısı önizleme satırı görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
