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
# <a name="inspect-intermediate-data-values-during-processing"></a><span data-ttu-id="044fd-103">İşleme sırasında ara veri değerlerini İnceleme</span><span class="sxs-lookup"><span data-stu-id="044fd-103">Inspect intermediate data values during processing</span></span>

<span data-ttu-id="044fd-104">Yükleniyor, işleme ve ML.NET eğitim adımları sırasında değerlerini İnceleme öğrenin.</span><span class="sxs-lookup"><span data-stu-id="044fd-104">Learn how to inspect values during loading, processing and training steps in ML.NET.</span></span>

<span data-ttu-id="044fd-105">İster temsil edilen bir veri uygulamasına yüklendiği aşağıda bir [ `IDataView` ](xref:Microsoft.ML.IDataView) ML.NET çeşitli şekillerde inceledi.</span><span class="sxs-lookup"><span data-stu-id="044fd-105">Data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>
 
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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="044fd-106">IDataView IEnumerable öğesine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="044fd-106">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="044fd-107">Değerlerini incelemek için hızlı şekilde bir [ `IDataView` ](xref:Microsoft.ML.IDataView) öğesine dönüştürmek için olan bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="044fd-107">One of the quickest ways to inspect the values of an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="044fd-108">Dönüştürülecek bir [ `IDataView` ](xref:Microsoft.ML.IDataView) için [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) kullanın [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="044fd-108">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span> 

<span data-ttu-id="044fd-109">Performansı iyileştirmek için değerini ayarlamak `reuseRowObject` için `true`.</span><span class="sxs-lookup"><span data-stu-id="044fd-109">To optimize performance, set the value of `reuseRowObject` to `true`.</span></span> <span data-ttu-id="044fd-110">Bunun yapılması her satır için yeni bir nesne içinde veri kümesi oluşturma yerine değerlendiriliyor gibi gevşek aynı nesneyi geçerli satırın verilerle dolduracaksınız.</span><span class="sxs-lookup"><span data-stu-id="044fd-110">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

<span data-ttu-id="044fd-111">Yalnızca bir kısmı veriler veya belirli dizinleri erişmeniz kullanırsanız [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve `reuseRowObject` parametre değerine `false` için istenen satır kümesindeki her biri için yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="044fd-111">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="044fd-112">Ardından, dönüştürme [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) bir dizi veya listesi.</span><span class="sxs-lookup"><span data-stu-id="044fd-112">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="044fd-113">Dönüştürme sonucunu [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) bir dizi veya listesini yükler istenen [ `IDataView` ](xref:Microsoft.ML.IDataView) satırları belleğe performansı etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="044fd-113">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="044fd-114">Koleksiyon oluşturulduktan sonra veriler üzerinde işlemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="044fd-114">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="044fd-115">Aşağıdaki kod parçacığında, kümesinde ilk üç satır alır ve ortalama geçerli fiyat hesaplar.</span><span class="sxs-lookup"><span data-stu-id="044fd-115">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="044fd-116">Tek bir sütunda bulunan değerleri inceleyin</span><span class="sxs-lookup"><span data-stu-id="044fd-116">Inspect values in a single column</span></span>

<span data-ttu-id="044fd-117">Modeldeki herhangi bir noktada oluşturma işlemi, değerler tek bir sütunda bir [ `IDataView` ](xref:Microsoft.ML.IDataView) kullanılarak erişilebilir [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="044fd-117">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="044fd-118">[ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Yöntemi tek bir sütundaki tüm değerleri döndürür bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="044fd-118">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="044fd-119">Aynı anda IDataView değerleri bir satır inceleyin</span><span class="sxs-lookup"><span data-stu-id="044fd-119">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="044fd-120">[`IDataView`](xref:Microsoft.ML.IDataView) Gevşek değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="044fd-120">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="044fd-121">Satırları yinelemek için bir [ `IDataView` ](xref:Microsoft.ML.IDataView) dönüştürme olmadan bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) bu belgenin önceki bölümlerde gösterildiği gibi oluşturun bir [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) kullanarak [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) yöntemi ve geçirmeye [DataViewSchema](xref:Microsoft.ML.DataViewSchema) , uygulamanızın [ `IDataView` ](xref:Microsoft.ML.IDataView) bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="044fd-121">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="044fd-122">Ardından satırları yineleme yapmak için kullanın [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) imleç yöntemi ile birlikte [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) her sütun ilgili değerlerini ayıklamak için temsilci.</span><span class="sxs-lookup"><span data-stu-id="044fd-122">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="044fd-123">ML.NET kullanımda performans amacıyla vektörlerine [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) yerel koleksiyon türleri yerine (diğer bir deyişle, `Vector`,`float[]`).</span><span class="sxs-lookup"><span data-stu-id="044fd-123">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span> 

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="044fd-124">Önizleme sonuçlarını ön işleme veya verilerin bir alt kümesi üzerinde eğitim</span><span class="sxs-lookup"><span data-stu-id="044fd-124">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="044fd-125">Kullanmayın `Preview` üretim aşamasında hata ayıklama için tasarlanmıştır ve performansını düşürebilir, çünkü kod.</span><span class="sxs-lookup"><span data-stu-id="044fd-125">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="044fd-126">Oluşturma işlemi Deneysel ve yinelemeli modelidir.</span><span class="sxs-lookup"><span data-stu-id="044fd-126">The model building process is experimental and iterative.</span></span> <span data-ttu-id="044fd-127">Hangi veri ön işleme sonra görünmesi mi makine öğrenimi modeli verilerin bir alt kümesi üzerinde kullanmak önizlemek için [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) döndüren yöntemi bir [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="044fd-127">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="044fd-128">Sonuç ile bir nesnedir `ColumnView` ve `RowView` her ikisi de özellikleri bir [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) ve belirli bir sütun veya satır değerler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="044fd-128">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="044fd-129">Dönüşüm ile uygulamak için satır sayısını belirtin `maxRows` parametresi.</span><span class="sxs-lookup"><span data-stu-id="044fd-129">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Veri hata ayıklayıcı Önizleme nesnesi](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="044fd-131">İnceleme sonucunu bir [ `IDataView` ](xref:Microsoft.ML.IDataView) aşağıdakine benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="044fd-131">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Veri hata ayıklayıcı Önizleme satır görünümü](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
