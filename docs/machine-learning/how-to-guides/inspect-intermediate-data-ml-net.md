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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="9801a-103">İşlem sırasında ara verileri İncele</span><span class="sxs-lookup"><span data-stu-id="9801a-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="9801a-104">ML.NET ' de yükleme, işleme ve model eğitimi adımları sırasında ara verileri incelemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9801a-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="9801a-105">Ara veri, makine öğrenimi ardışık düzeninde her bir aşamanın çıktısıdır.</span><span class="sxs-lookup"><span data-stu-id="9801a-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="9801a-106">Aşağıda temsil edilen bir [`IDataView`](xref:Microsoft.ML.IDataView) gibi ara veriler, ml.NET içinde çeşitli yollarla incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="9801a-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="9801a-107">Idataview öğesini IEnumerable 'a Dönüştür</span><span class="sxs-lookup"><span data-stu-id="9801a-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="9801a-108">Bir [`IDataView`](xref:Microsoft.ML.IDataView) incelemeyi en hızlı yolu bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="9801a-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="9801a-109">Bir [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürmek için [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9801a-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="9801a-110">Performansı iyileştirmek için `reuseRowObject` `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9801a-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="9801a-111">Bunun yapılması, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirilmekte olduğundan aynı nesneyi geçerli satırın verileriyle doldurgeç.</span><span class="sxs-lookup"><span data-stu-id="9801a-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="9801a-112">IEnumerable ile belirli dizinlerine erişme</span><span class="sxs-lookup"><span data-stu-id="9801a-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="9801a-113">Yalnızca verilerin veya belirli dizinlerin bir kısmına erişmeniz gerekiyorsa [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) kullanın ve `reuseRowObject` parametre değerini `false` olarak ayarlayın. bu nedenle veri kümesindeki istenen her bir satır için yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9801a-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="9801a-114">Ardından [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir diziye veya listeye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9801a-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="9801a-115">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) sonucunu bir diziye veya listeye dönüştürmek, istenen tüm [`IDataView`](xref:Microsoft.ML.IDataView) satırlarını belleğe yükler ve bu da performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9801a-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="9801a-116">Koleksiyon oluşturulduktan sonra, veriler üzerinde işlemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9801a-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="9801a-117">Aşağıdaki kod parçacığı, veri kümesindeki ilk üç satırı alır ve ortalama geçerli fiyatı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9801a-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="9801a-118">Tek bir sütundaki değerleri İnceleme</span><span class="sxs-lookup"><span data-stu-id="9801a-118">Inspect values in a single column</span></span>

<span data-ttu-id="9801a-119">Model oluşturma işlemindeki herhangi bir noktada, [`IDataView`](xref:Microsoft.ML.IDataView) tek bir sütunundaki değerlere [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9801a-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="9801a-120">[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi, tek bir sütundaki tüm değerleri [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="9801a-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="9801a-121">Idataview değerlerini tek seferde bir satır olarak İnceleme</span><span class="sxs-lookup"><span data-stu-id="9801a-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="9801a-122">[`IDataView`](xref:Microsoft.ML.IDataView) geç değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9801a-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="9801a-123">Bu belgenin önceki bölümlerinde gösterildiği gibi bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürmeden [`IDataView`](xref:Microsoft.ML.IDataView) satırlarını yinelemek için, [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemini kullanarak bir [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) oluşturun ve bir parametre olarak [`IDataView`](xref:Microsoft.ML.IDataView) [DataViewSchema](xref:Microsoft.ML.DataViewSchema) .</span><span class="sxs-lookup"><span data-stu-id="9801a-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="9801a-124">Daha sonra, satırları yinelemek için, her sütundan ilgili değerleri ayıklamak üzere [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) temsilcilerle birlikte [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) Cursor metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9801a-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9801a-125">Performans amaçlarıyla, ML.NET içindeki vektörler yerel koleksiyon türleri yerine [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) kullanır (yani, `Vector`,`float[]`).</span><span class="sxs-lookup"><span data-stu-id="9801a-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="9801a-126">Verilerin bir alt kümesinde ön işleme veya eğitime ilişkin önizleme sonucu</span><span class="sxs-lookup"><span data-stu-id="9801a-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="9801a-127">Hata ayıklama için tasarlanan ve performansı azaltabileceğinden üretim kodunda `Preview` kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9801a-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="9801a-128">Model oluşturma işlemi deneysel ve yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9801a-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="9801a-129">Bir makine öğrenimi modelini verilerin bir alt kümesinde ön işlemden sonra veya öğreticduktan sonra hangi verilerin göründüğünü önizlemek için, bir [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)döndüren [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9801a-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="9801a-130">Sonuç, hem [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) hem de belirli bir sütun veya satırdaki değerleri içeren `ColumnView` ve `RowView` özelliklerine sahip bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9801a-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="9801a-131">`maxRows` parametresine dönüşüm uygulanacak satır sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="9801a-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Veri hata ayıklayıcısı önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="9801a-133">Bir [`IDataView`](xref:Microsoft.ML.IDataView) inceleme sonucu aşağıdakine benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="9801a-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Veri hata ayıklayıcısı önizleme satırı görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
