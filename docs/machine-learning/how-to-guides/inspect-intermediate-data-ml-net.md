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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="29bd7-103">İşlemsırasında ara verileri inceleyin</span><span class="sxs-lookup"><span data-stu-id="29bd7-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="29bd7-104">ML.NET'da yükleme, işleme ve modelleme eğitim adımları sırasında ara verileri nasıl inceleyire öğrenin.</span><span class="sxs-lookup"><span data-stu-id="29bd7-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="29bd7-105">Ara veriler, makine öğrenimi boru hattındaki her aşamanın çıktısI.</span><span class="sxs-lookup"><span data-stu-id="29bd7-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="29bd7-106">Aşağıda temsil edilen ve bir [`IDataView`](xref:Microsoft.ML.IDataView) alana yüklenen ara veriler ML.NET çeşitli şekillerde incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="29bd7-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="29bd7-107">IDataView'ı Ayrılmaz'a dönüştürün</span><span class="sxs-lookup"><span data-stu-id="29bd7-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="29bd7-108">Bir şeyi incelemenin en [`IDataView`](xref:Microsoft.ML.IDataView) hızlı yollarından biri, bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).'e dönüştürmektir.</span><span class="sxs-lookup"><span data-stu-id="29bd7-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="29bd7-109">Bir [`IDataView`](xref:Microsoft.ML.IDataView) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) kullanmak için dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="29bd7-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="29bd7-110">Performansı en iyi `reuseRowObject` `true`duruma getirmek için, 'ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29bd7-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="29bd7-111">Bunu yapmak, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirildiği için aynı nesneyi geçerli satırın verileriyle dolduracaktır.</span><span class="sxs-lookup"><span data-stu-id="29bd7-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="29bd7-112">Tümesiyatif ile belirli endekslere erişim</span><span class="sxs-lookup"><span data-stu-id="29bd7-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="29bd7-113">Verilerin veya belirli endekslerin yalnızca bir kısmına erişmeniz gerekiyorsa, parametre `false` değerini kullanarak veri kümesindeki istenen satırların her biri için yeni bir nesne nin oluşturulmasını sağlamak için kullanın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve ayarlayın. `reuseRowObject`</span><span class="sxs-lookup"><span data-stu-id="29bd7-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="29bd7-114">Ardından, bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) diziye veya listeye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="29bd7-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="29bd7-115">Bir dizi veya [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) listeye sonucu dönüştürme performansı etkileyebilecek [`IDataView`](xref:Microsoft.ML.IDataView) tüm istenen satırları belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="29bd7-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="29bd7-116">Koleksiyon oluşturulduktan sonra, veriler üzerinde işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29bd7-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="29bd7-117">Aşağıdaki kod parçacığı veri kümesindeki ilk üç satırı alır ve ortalama geçerli fiyatı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="29bd7-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="29bd7-118">Değerleri tek bir sütunda denetleme</span><span class="sxs-lookup"><span data-stu-id="29bd7-118">Inspect values in a single column</span></span>

<span data-ttu-id="29bd7-119">Model oluşturma işleminin herhangi bir noktasında, bir [`IDataView`](xref:Microsoft.ML.IDataView) [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntem kullanılarak tek bir sütundaki değerlere erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="29bd7-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="29bd7-120">Yöntem, [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) tek bir sütundaki tüm değerleri [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="29bd7-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="29bd7-121">IDataView değerlerini her seferinde bir satır da inceleyin</span><span class="sxs-lookup"><span data-stu-id="29bd7-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="29bd7-122">[`IDataView`](xref:Microsoft.ML.IDataView)tembelce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="29bd7-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="29bd7-123">Bu belgenin önceki bölümlerinde gösterildiği [`IDataView`](xref:Microsoft.ML.IDataView) gibi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir dönüştürme olmadan bir satır üzerinde yinelemek [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) için, [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemi kullanarak ve bir parametre [`IDataView`](xref:Microsoft.ML.IDataView) olarak [DataViewSchema](xref:Microsoft.ML.DataViewSchema) geçirerek bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="29bd7-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="29bd7-124">Ardından, satırlar üzerinde yinelemek için [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) imleç yöntemini, sütunların her birinden ilgili değerleri ayıklamak için temsilcilerle [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="29bd7-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29bd7-125">Performans amacıyla, yerel koleksiyon [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) türleri yerine ML.NET kullanılan vektörler`float[]`(diğer bir deyişle). `Vector`</span><span class="sxs-lookup"><span data-stu-id="29bd7-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="29bd7-126">Verilerin bir alt kümesi nde ön işleme veya eğitimin önizleme sonucu</span><span class="sxs-lookup"><span data-stu-id="29bd7-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="29bd7-127">Hata ayıklama amaçlı olduğundan ve performansı azaltabileceğinden üretim kodunda kullanmayın. `Preview`</span><span class="sxs-lookup"><span data-stu-id="29bd7-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="29bd7-128">Model oluşturma süreci deneysel ve yinelemeli.</span><span class="sxs-lookup"><span data-stu-id="29bd7-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="29bd7-129">Bir makine öğrenme modelini verilerin bir alt kümesi üzerinde ön işlem veya eğitimden sonra verilerin nasıl görüneceğini önizlemek için, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) bir [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="29bd7-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="29bd7-130">Sonuç, hem bir `ColumnView` `RowView` sütuna hem [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) de satırda değerleri içeren ve özellikleri olan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="29bd7-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="29bd7-131">Dönüştürmeyi parametreyle birlikte uygulamak için `maxRows` satır sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="29bd7-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Veri Hata Ayıklama Önizleme Nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="29bd7-133">Bir [`IDataView`](xref:Microsoft.ML.IDataView) inceleme sonucu aşağıdaki gibi görünecekti:</span><span class="sxs-lookup"><span data-stu-id="29bd7-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Veri Hata Ayıklama Önizleme Satır Görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
