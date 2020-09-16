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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="0fc20-103">İşlem sırasında ara verileri İncele</span><span class="sxs-lookup"><span data-stu-id="0fc20-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="0fc20-104">ML.NET ' de yükleme, işleme ve model eğitimi adımları sırasında ara verileri incelemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0fc20-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="0fc20-105">Ara veri, makine öğrenimi ardışık düzeninde her bir aşamanın çıktısıdır.</span><span class="sxs-lookup"><span data-stu-id="0fc20-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="0fc20-106">Aşağıda gösterildiği gibi, bir ' a yüklenmiş bir gibi ara veriler, [`IDataView`](xref:Microsoft.ML.IDataView) ml.NET içinde çeşitli yollarla incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc20-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="0fc20-107">Idataview öğesini IEnumerable 'a Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0fc20-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="0fc20-108">' Yi incelemeyi en hızlı yöntemlerinden biri bir ' a [`IDataView`](xref:Microsoft.ML.IDataView) dönüştürmelidir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="0fc20-109">' A dönüştürmek [`IDataView`](xref:Microsoft.ML.IDataView) için [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) yöntemini kullanın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method.</span></span>

<span data-ttu-id="0fc20-110">Performansı iyileştirmek için, `reuseRowObject` olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="0fc20-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="0fc20-111">Bunun yapılması, veri kümesindeki her satır için yeni bir nesne oluşturmak yerine değerlendirilmekte olduğundan aynı nesneyi geçerli satırın verileriyle doldurgeç.</span><span class="sxs-lookup"><span data-stu-id="0fc20-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="0fc20-112">IEnumerable ile belirli dizinlerine erişme</span><span class="sxs-lookup"><span data-stu-id="0fc20-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="0fc20-113">Yalnızca verilerin veya belirli dizinlerin bir kısmına erişmeniz gerekiyorsa, veri [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) `reuseRowObject` `false` kümesindeki istenen satırların her biri için yeni bir nesne oluşturulması için parametre değerini kullanın ve olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0fc20-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="0fc20-114">Ardından, öğesini [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) bir diziye veya listeye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="0fc20-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="0fc20-115">Sonucunu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) bir diziye veya listeye dönüştürmek, istenen tüm [`IDataView`](xref:Microsoft.ML.IDataView) satırları belleğe yükler ve bu da performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc20-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="0fc20-116">Koleksiyon oluşturulduktan sonra, veriler üzerinde işlemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc20-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="0fc20-117">Aşağıdaki kod parçacığı, veri kümesindeki ilk üç satırı alır ve ortalama geçerli fiyatı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0fc20-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="0fc20-118">Tek bir sütundaki değerleri İnceleme</span><span class="sxs-lookup"><span data-stu-id="0fc20-118">Inspect values in a single column</span></span>

<span data-ttu-id="0fc20-119">Model oluşturma işlemindeki herhangi bir noktada, tek bir sütunundaki değerlere [`IDataView`](xref:Microsoft.ML.IDataView) yöntemi kullanılarak erişilebilir [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method.</span></span> <span data-ttu-id="0fc20-120">[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A)Yöntemi, tek bir sütundaki tüm değerleri bir olarak döndürür [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="0fc20-121">Idataview değerlerini tek seferde bir satır olarak İnceleme</span><span class="sxs-lookup"><span data-stu-id="0fc20-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="0fc20-122">[`IDataView`](xref:Microsoft.ML.IDataView) geç değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0fc20-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="0fc20-123">[`IDataView`](xref:Microsoft.ML.IDataView)Bu belgenin önceki bölümlerinde gösterildiği gibi, bir öğesine dönüştürme yapmadan satırları yinelemek için [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) , [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) yöntemini kullanarak bir oluşturun ve bir [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) parametresi olarak [DataViewSchema](xref:Microsoft.ML.DataViewSchema) ' ı geçirin [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="0fc20-124">Daha sonra, satırları yinelemek için, [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) her bir sütundan ilgili değerleri ayıklamak üzere, imleç yöntemi ile birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fc20-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fc20-125">Performans amaçları için, yerel koleksiyon türleri yerine ML.NET kullanımdaki vektörler (yani, [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) `Vector` `float[]` ).</span><span class="sxs-lookup"><span data-stu-id="0fc20-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="0fc20-126">Verilerin bir alt kümesinde ön işleme veya eğitime ilişkin önizleme sonucu</span><span class="sxs-lookup"><span data-stu-id="0fc20-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="0fc20-127">`Preview`Hata ayıklama için tasarlanan ve performansı azaltabileceğinden üretim kodunda kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0fc20-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="0fc20-128">Model oluşturma işlemi deneysel ve yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="0fc20-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="0fc20-129">Verilerin bir alt kümesindeki bir makine öğrenimi modelini ön işlemden sonra veya öğreticduktan sonra, verilerin nasıl göründüğünü önizlemek için, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) döndüren yöntemini kullanın [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview) .</span><span class="sxs-lookup"><span data-stu-id="0fc20-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="0fc20-130">Sonuç, ve özelliklerine sahip olan `ColumnView` ve `RowView` belirli bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) sütun veya satırdaki değerleri içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="0fc20-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="0fc20-131">Parametreye, dönüşüme uygulanacak satır sayısını belirtin `maxRows` .</span><span class="sxs-lookup"><span data-stu-id="0fc20-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Veri hata ayıklayıcısı önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="0fc20-133">İnceleme sonucu aşağıdakine [`IDataView`](xref:Microsoft.ML.IDataView) benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="0fc20-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Veri hata ayıklayıcısı önizleme satırı görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
