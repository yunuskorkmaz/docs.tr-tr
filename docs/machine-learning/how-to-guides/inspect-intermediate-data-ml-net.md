---
title: ML.NET işleme sırasında ara verileri inceleyin
description: ML.NET ML.NET makine öğrenimi boru hattı yükleme, işleme ve model eğitim adımları sırasında ara verileri nasıl inceleyiyin öğrenin.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977100"
---
# <a name="inspect-intermediate-data-during-processing"></a>İşlemsırasında ara verileri inceleyin

ML.NET'da yükleme, işleme ve modelleme eğitim adımları sırasında ara verileri nasıl inceleyire öğrenin. Ara veriler, makine öğrenimi boru hattındaki her aşamanın çıktısI.

Aşağıda temsil edilen ve bir [`IDataView`](xref:Microsoft.ML.IDataView) alana yüklenen ara veriler ML.NET çeşitli şekillerde incelenebilir.

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

## <a name="convert-idataview-to-ienumerable"></a>IDataView'ı Ayrılmaz'a dönüştürün

Bir şeyi incelemenin en [`IDataView`](xref:Microsoft.ML.IDataView) hızlı yollarından biri, bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).'e dönüştürmektir. Bir [`IDataView`](xref:Microsoft.ML.IDataView) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) kullanmak için dönüştürmek için.

Performansı en iyi `reuseRowObject` `true`duruma getirmek için, 'ye ayarlayın. Bunu yapmak, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirildiği için aynı nesneyi geçerli satırın verileriyle dolduracaktır.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Tümesiyatif ile belirli endekslere erişim

Verilerin veya belirli endekslerin yalnızca bir kısmına erişmeniz gerekiyorsa, parametre `false` değerini kullanarak veri kümesindeki istenen satırların her biri için yeni bir nesne nin oluşturulmasını sağlamak için kullanın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve ayarlayın. `reuseRowObject` Ardından, bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) diziye veya listeye dönüştürün.

> [!WARNING]
> Bir dizi veya [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) listeye sonucu dönüştürme performansı etkileyebilecek [`IDataView`](xref:Microsoft.ML.IDataView) tüm istenen satırları belleğe yükler.

Koleksiyon oluşturulduktan sonra, veriler üzerinde işlemleri gerçekleştirebilirsiniz. Aşağıdaki kod parçacığı veri kümesindeki ilk üç satırı alır ve ortalama geçerli fiyatı hesaplar.

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

## <a name="inspect-values-in-a-single-column"></a>Değerleri tek bir sütunda denetleme

Model oluşturma işleminin herhangi bir noktasında, bir [`IDataView`](xref:Microsoft.ML.IDataView) [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntem kullanılarak tek bir sütundaki değerlere erişilebilir. Yöntem, [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) tek bir sütundaki tüm değerleri [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>IDataView değerlerini her seferinde bir satır da inceleyin

[`IDataView`](xref:Microsoft.ML.IDataView)tembelce değerlendirilir. Bu belgenin önceki bölümlerinde gösterildiği [`IDataView`](xref:Microsoft.ML.IDataView) gibi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir dönüştürme olmadan bir satır üzerinde yinelemek [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) için, [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemi kullanarak ve bir parametre [`IDataView`](xref:Microsoft.ML.IDataView) olarak [DataViewSchema](xref:Microsoft.ML.DataViewSchema) geçirerek bir oluşturun. Ardından, satırlar üzerinde yinelemek için [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) imleç yöntemini, sütunların her birinden ilgili değerleri ayıklamak için temsilcilerle [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) birlikte kullanın.

> [!IMPORTANT]
> Performans amacıyla, yerel koleksiyon [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) türleri yerine ML.NET kullanılan vektörler`float[]`(diğer bir deyişle). `Vector`

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Verilerin bir alt kümesi nde ön işleme veya eğitimin önizleme sonucu

> [!WARNING]
> Hata ayıklama amaçlı olduğundan ve performansı azaltabileceğinden üretim kodunda kullanmayın. `Preview`

Model oluşturma süreci deneysel ve yinelemeli. Bir makine öğrenme modelini verilerin bir alt kümesi üzerinde ön işlem veya eğitimden sonra verilerin nasıl görüneceğini önizlemek için, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) bir [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). Sonuç, hem bir `ColumnView` `RowView` sütuna hem [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) de satırda değerleri içeren ve özellikleri olan bir nesnedir. Dönüştürmeyi parametreyle birlikte uygulamak için `maxRows` satır sayısını belirtin.

![Veri Hata Ayıklama Önizleme Nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Bir [`IDataView`](xref:Microsoft.ML.IDataView) inceleme sonucu aşağıdaki gibi görünecekti:

![Veri Hata Ayıklama Önizleme Satır Görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
