---
title: Dizi Boyutları
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413110"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="3f657-102">Visual Basic'de Dizi Boyutları</span><span class="sxs-lookup"><span data-stu-id="3f657-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="3f657-103">*Boyut* , bir dizinin öğelerinin belirtimini değiştirebileceğiniz bir yöndir.</span><span class="sxs-lookup"><span data-stu-id="3f657-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="3f657-104">Ayın her günü için satış toplamı tutan bir dizinin bir boyutu (ayın günü) vardır.</span><span class="sxs-lookup"><span data-stu-id="3f657-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="3f657-105">Ayın her günü için departmanın satış toplamı tutan bir dizinin iki boyutu vardır (Departman numarası ve ayın günü).</span><span class="sxs-lookup"><span data-stu-id="3f657-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="3f657-106">Bir dizinin sahip olduğu boyut sayısı *derece*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3f657-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="3f657-107"><xref:System.Array.Rank%2A>Bir dizinin kaç boyut olduğunu anlamak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f657-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="3f657-108">Boyutlarla çalışma</span><span class="sxs-lookup"><span data-stu-id="3f657-108">Working with Dimensions</span></span>

<span data-ttu-id="3f657-109">Bir dizinin bir öğesini, boyutlarının her biri için bir *Dizin* veya *alt simge* sağlayarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f657-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="3f657-110">Öğeler, 0 dizininden bu boyut için en yüksek dizin arasındaki her bir boyut boyunca bitişik.</span><span class="sxs-lookup"><span data-stu-id="3f657-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="3f657-111">Aşağıdaki çizimler, farklı derecelendirilerle dizilerin kavramsal yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f657-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="3f657-112">Çizimlerde bulunan her öğe, ona erişen dizin değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f657-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="3f657-113">Örneğin, dizinler belirterek iki boyutlu dizinin ikinci satırındaki ilk öğesine erişebilirsiniz `(1, 0)` .</span><span class="sxs-lookup"><span data-stu-id="3f657-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Tek boyutlu dizi gösteren diyagram.](./media/array-dimensions/one-dimensional-array.gif)

![İki boyutlu bir dizi gösteren diyagram.](./media/array-dimensions/two-dimensional-array.gif)

![Üç boyutlu bir diziyi gösteren diyagram.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="3f657-117">Bir boyut</span><span class="sxs-lookup"><span data-stu-id="3f657-117">One Dimension</span></span>

<span data-ttu-id="3f657-118">Birçok dizi, her bir yaş için kişi sayısı gibi yalnızca bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f657-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="3f657-119">Bir öğeyi belirtmeye yönelik tek gereksinim, bu öğenin sayımı tutan yaşdır.</span><span class="sxs-lookup"><span data-stu-id="3f657-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="3f657-120">Bu nedenle, bu tür bir dizi yalnızca bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f657-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="3f657-121">Aşağıdaki örnek, 0 ile 120 arasındaki yaşlar için *tek boyutlu* bir yaş dizisi sayısı tutan bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f657-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="3f657-122">İki boyut</span><span class="sxs-lookup"><span data-stu-id="3f657-122">Two Dimensions</span></span>

<span data-ttu-id="3f657-123">Bazı diziler, kampüs üzerinde her binadaki her bir kata ait ofislerin sayısı gibi iki boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f657-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="3f657-124">Bir öğenin belirtimi hem bina numarası hem de kat gerektirir ve her öğe bu derleme ve kat birleşiminin sayısını tutar.</span><span class="sxs-lookup"><span data-stu-id="3f657-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="3f657-125">Bu nedenle, bu tür bir dizi iki dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f657-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="3f657-126">Aşağıdaki örnek, 0 ile 40 arası binalar ve 0 ile 5 arasındaki katkılar için *iki boyutlu bir dizi* Office sayımlarını tutmak üzere bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f657-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="3f657-127">İki boyutlu bir dizi *dikdörtgen dizi*olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3f657-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="3f657-128">Üç boyut</span><span class="sxs-lookup"><span data-stu-id="3f657-128">Three Dimensions</span></span>

<span data-ttu-id="3f657-129">Birkaç dizide üç boyutlu boşluk değerleri gibi üç boyut vardır.</span><span class="sxs-lookup"><span data-stu-id="3f657-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="3f657-130">Böyle bir dizi üç dizin kullanır. Bu örnekte, fiziksel alanın x, y ve z koordinatları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f657-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="3f657-131">Aşağıdaki örnek, üç boyutlu bir birimin çeşitli noktalarında *üç boyutlu* bir hava sıcaklığı dizisini tutacak bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f657-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="3f657-132">Üçten fazla boyut</span><span class="sxs-lookup"><span data-stu-id="3f657-132">More than Three Dimensions</span></span>

<span data-ttu-id="3f657-133">Bir dizide en fazla 32 boyut olabilir, ancak üçten fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f657-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="3f657-134">Bir diziye boyut eklediğinizde, dizi için gereken toplam depolama alanı önemli ölçüde artar, bu nedenle çok boyutlu dizileri dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f657-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="3f657-135">Farklı boyutlar kullanma</span><span class="sxs-lookup"><span data-stu-id="3f657-135">Using Different Dimensions</span></span>

<span data-ttu-id="3f657-136">Mevcut ayın her gününde satış miktarlarını izlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3f657-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="3f657-137">Aşağıdaki örnekte gösterildiği gibi, ayın her günü için bir tane olmak üzere 31 öğe içeren tek boyutlu bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f657-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="3f657-138">Şimdi yalnızca bir ayın her gününde değil, yılın her ayında aynı bilgileri izlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3f657-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="3f657-139">Aşağıdaki örnekte gösterildiği gibi 12 satır (aylar için) ve 31 sütun (günler için) ile iki boyutlu bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f657-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="3f657-140">Artık, dizi tutma bilgilerinizin bir yıldan daha fazla olması gerektiğine varsayın.</span><span class="sxs-lookup"><span data-stu-id="3f657-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="3f657-141">5 yıl boyunca satış tutarlarını izlemek isterseniz, aşağıdaki örnekte gösterildiği gibi 5 katman, 12 satır ve 31 sütunlu üç boyutlu bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f657-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="3f657-142">Her bir dizin 0 ' dan en büyük ' a değiştiğinden, her boyutun `salesAmounts` Bu boyut için gereken uzunluktan bir daha az olarak bildirildiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f657-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="3f657-143">Ayrıca, dizi boyutunun her yeni boyutla arttığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f657-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="3f657-144">Yukarıdaki örneklerde bulunan üç boyut sırasıyla 31, 372 ve 1.860 öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="3f657-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="3f657-145">`Dim`Deyimi veya yan tümcesini kullanmadan bir dizi oluşturabilirsiniz `New` .</span><span class="sxs-lookup"><span data-stu-id="3f657-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="3f657-146">Örneğin, <xref:System.Array.CreateInstance%2A> yöntemini çağırabilirsiniz ya da başka bir bileşen kodunuzu bu şekilde oluşturulan bir diziye geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="3f657-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="3f657-147">Böyle bir dizide 0 dışında bir alt sınır olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f657-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="3f657-148">Yöntemini veya işlevini kullanarak, boyutun alt sınır için her zaman test edebilirsiniz <xref:System.Array.GetLowerBound%2A> `LBound` .</span><span class="sxs-lookup"><span data-stu-id="3f657-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f657-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f657-149">See also</span></span>

- [<span data-ttu-id="3f657-150">Diziler</span><span class="sxs-lookup"><span data-stu-id="3f657-150">Arrays</span></span>](index.md)
- [<span data-ttu-id="3f657-151">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="3f657-151">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
