---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614969"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="8231b-101">Ana/ayrıntı senaryosunda ADO verileri görüntülenirken birincil anahtarı değiştirme</span><span class="sxs-lookup"><span data-stu-id="8231b-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="8231b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8231b-102">Details</span></span>

<span data-ttu-id="8231b-103">Bir tür öğe derlediğinizi `Order` ve &quot; &quot; Bu ilişkiyi `Detail` birincil anahtar OrderID aracılığıyla bir tür öğe koleksiyonuyla ilişkili OrderDetails adlı bir ilişkiye &quot; sahip olduğunuzu varsayalım &quot; .</span><span class="sxs-lookup"><span data-stu-id="8231b-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="8231b-104">WPF uygulamanızda, belirli bir siparişin ayrıntılarına bir liste denetimi bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8231b-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="8231b-105">DataContext 'in bir olduğu yer `Order` .</span><span class="sxs-lookup"><span data-stu-id="8231b-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="8231b-106">WPF, özelliğinin değerini alır `OrderDetails` - `Detail` `OrderID` ana öğe ile eşleşen tüm öğelerin D koleksiyonu `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="8231b-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="8231b-107">Ana öğenin birincil anahtarını değiştirdiğinizde davranış değişikliği ortaya çıkar `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="8231b-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="8231b-108">ADO, `OrderID` Ayrıntılar koleksiyonundaki etkilenen kayıtların her birini otomatik olarak değiştirir (yani, D koleksiyonuna kopyalanırlar).</span><span class="sxs-lookup"><span data-stu-id="8231b-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="8231b-109">Ancak D 'ye ne olur?</span><span class="sxs-lookup"><span data-stu-id="8231b-109">But what happens to D?</span></span>

- <span data-ttu-id="8231b-110">Eski davranış: koleksiyon D temizlendi.</span><span class="sxs-lookup"><span data-stu-id="8231b-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="8231b-111">Ana *öğe, özelliği* için bir değişiklik bildirimi oluşturmaz `OrderDetails` .</span><span class="sxs-lookup"><span data-stu-id="8231b-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="8231b-112">Liste kutusu artık boş olan D koleksiyonunu kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8231b-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="8231b-113">Yeni davranış: koleksiyon D değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8231b-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="8231b-114">Öğelerinin her biri, özelliği için bir değişiklik bildirimi oluşturur `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="8231b-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="8231b-115">ListBox, koleksiyonu D 'yi kullanmaya devam eder ve yeni ile ayrıntıları görüntüler `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="8231b-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="8231b-116">WPF, farklı bir şekilde koleksiyon oluşturarak yeni davranışı uygular: ADO yöntemini <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> `followParent` olarak ayarlanmış bağımsız değişkenle çağırarak `true` .</span><span class="sxs-lookup"><span data-stu-id="8231b-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8231b-117">Öneri</span><span class="sxs-lookup"><span data-stu-id="8231b-117">Suggestion</span></span>

<span data-ttu-id="8231b-118">Uygulama, aşağıdaki AppContext anahtarını kullanarak yeni davranışı alır.</span><span class="sxs-lookup"><span data-stu-id="8231b-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="8231b-119">Anahtar, .net `true` 4.7.1 veya sonraki sürümlerini hedefleyen uygulamalar için (eski davranış), `false` .NET 4.7.2 veya üstünü hedefleyen uygulamalar için ise (yeni davranış) olarak varsayılan değeri (eski davranış) olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8231b-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="8231b-120">Name</span><span class="sxs-lookup"><span data-stu-id="8231b-120">Name</span></span>    | <span data-ttu-id="8231b-121">Değer</span><span class="sxs-lookup"><span data-stu-id="8231b-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8231b-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8231b-122">Scope</span></span>   | <span data-ttu-id="8231b-123">İkincil</span><span class="sxs-lookup"><span data-stu-id="8231b-123">Minor</span></span>       |
| <span data-ttu-id="8231b-124">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8231b-124">Version</span></span> | <span data-ttu-id="8231b-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8231b-125">4.7.2</span></span>       |
| <span data-ttu-id="8231b-126">Tür</span><span class="sxs-lookup"><span data-stu-id="8231b-126">Type</span></span>    | <span data-ttu-id="8231b-127">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="8231b-127">Retargeting</span></span> |
