---
title: Visual Basic'de Dizi Boyutları
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 5ba92e113faf9d68bad97968937cc736132b2065
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708538"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="3b54e-102">Visual Basic'de Dizi Boyutları</span><span class="sxs-lookup"><span data-stu-id="3b54e-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="3b54e-103">A *boyut* içinde değişebilir bir dizinin öğelerin belirtimini yön olduğundan.</span><span class="sxs-lookup"><span data-stu-id="3b54e-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="3b54e-104">Ayın her günü için toplam satış tutan bir dizi bir boyut (ayın gününü) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="3b54e-105">Satış toplam departmana göre ayın her günü için tutan bir dizi iki boyutlu (bölüm numarası ve ayın günü) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="3b54e-106">Sahip bir dizi boyut sayısını çağrılır, *derece*.</span><span class="sxs-lookup"><span data-stu-id="3b54e-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b54e-107">Kullanabileceğiniz <xref:System.Array.Rank%2A> kaç boyutları bir dizi sahip olduğunu belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="3b54e-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="3b54e-108">Boyutlarla çalışma</span><span class="sxs-lookup"><span data-stu-id="3b54e-108">Working with Dimensions</span></span>  
 <span data-ttu-id="3b54e-109">Sağlayarak bir dizideki bir öğe belirttiğiniz bir *dizin* veya *alt simge* için her bir boyutundan.</span><span class="sxs-lookup"><span data-stu-id="3b54e-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="3b54e-110">Bitişik her boyut için bu boyut en yüksek dizin 0 dizininden öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="3b54e-111">Aşağıdaki çizimler farklı sıralamalara sahip dizilerle kavramsal yapısını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="3b54e-112">Çizimler her öğenin erişim dizin değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="3b54e-113">Örneğin, ilk öğesi iki boyutlu bir dizinin ikinci satırın dizinleri belirterek erişebileceğiniz `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="3b54e-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="3b54e-114">![Bir grafik diyagram&#45;boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="3b54e-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="3b54e-115">Tek boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="3b54e-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="3b54e-116">![İki grafik diyagram&#45;boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="3b54e-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="3b54e-117">iki boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="3b54e-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="3b54e-118">![Üç grafik diyagram&#45;boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="3b54e-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="3b54e-119">üç boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="3b54e-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="3b54e-120">Bir boyut</span><span class="sxs-lookup"><span data-stu-id="3b54e-120">One Dimension</span></span>  
 <span data-ttu-id="3b54e-121">Birçok dizileri her yaşında kişilerin sayısını gibi yalnızca bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="3b54e-122">Bir öğe belirtmek için tek gereksinim, o öğe sayısı tutan yaş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="3b54e-123">Bu nedenle, böyle bir dizi yalnızca bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="3b54e-124">Aşağıdaki örnek, tutacak bir değişken bildirir. bir *tek boyutlu dizi* yaşlar 0 ila 120 için yaşını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3b54e-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="3b54e-125">İki boyutlu</span><span class="sxs-lookup"><span data-stu-id="3b54e-125">Two Dimensions</span></span>  
 <span data-ttu-id="3b54e-126">Bazı diziler ve sayıda ofis her aşamasında, her bir Kampüste oluşturma gibi iki boyutlu sahip.</span><span class="sxs-lookup"><span data-stu-id="3b54e-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="3b54e-127">Hem bina numarasını hem de katı bir öğe belirtimi gerektirir ve her öğe bina ve kat birleşimi için tutar.</span><span class="sxs-lookup"><span data-stu-id="3b54e-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="3b54e-128">Bu nedenle, böyle bir dizi iki dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="3b54e-129">Aşağıdaki örnek, tutacak bir değişken bildirir. bir *iki boyutlu dizi* office sayılarını, 0 ile 40 Binalar ve Katlar 0 ile 5.</span><span class="sxs-lookup"><span data-stu-id="3b54e-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="3b54e-130">İki boyutlu bir dizi olarak da adlandırılan bir *dikdörtgen dizi*.</span><span class="sxs-lookup"><span data-stu-id="3b54e-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="3b54e-131">Üç boyutlu</span><span class="sxs-lookup"><span data-stu-id="3b54e-131">Three Dimensions</span></span>  
 <span data-ttu-id="3b54e-132">Birkaç diziler üç boyutlu alan değerleri gibi üç boyutlara sahip.</span><span class="sxs-lookup"><span data-stu-id="3b54e-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="3b54e-133">Böyle bir dizi, bu durumda x, y ve z bu gruplar fiziksel alan koordinatlarını temsil eden üç dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="3b54e-134">Aşağıdaki örnek, tutacak bir değişken bildirir. bir *üç boyutlu dizi* hava Sıcaklıkların çeşitli noktalarında üç boyutlu bir birim.</span><span class="sxs-lookup"><span data-stu-id="3b54e-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="3b54e-135">Üçten fazla boyutları</span><span class="sxs-lookup"><span data-stu-id="3b54e-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="3b54e-136">Bir dizi 32 adede kadar boyutları olabilse de, en fazla üç sahip nadir olarak rastlanıyor.</span><span class="sxs-lookup"><span data-stu-id="3b54e-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b54e-137">Bir diziye boyutları eklediğinizde, dizi tarafından gereken toplam depolama alanı önemli ölçüde, bunu kullanmak çok boyutlu diziler dikkatli artırır.</span><span class="sxs-lookup"><span data-stu-id="3b54e-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="3b54e-138">Farklı boyutları kullanma</span><span class="sxs-lookup"><span data-stu-id="3b54e-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="3b54e-139">Mevcut ayın her günü için satış tutarları izlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3b54e-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="3b54e-140">Aşağıdaki örnek, ayın her günü için gösterir 31 öğeleri içeren tek boyutlu bir dizi bildirin.</span><span class="sxs-lookup"><span data-stu-id="3b54e-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="3b54e-141">Artık her gün için yalnızca aynı bilgileri ayın aynı zamanda her bir yılın ayı izlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3b54e-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="3b54e-142">Aşağıdaki örnekte gösterildiği gibi iki boyutlu bir dizi (ay için) 12 satır ve (gün) boyunca 31 sütunlarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="3b54e-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="3b54e-143">Şimdi, karar varsayalım bilgi birden fazla bir yıl boyunca diziniz tutun.</span><span class="sxs-lookup"><span data-stu-id="3b54e-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="3b54e-144">Satış rakamlarını 5 yıl boyunca izlemek istiyorsanız, aşağıdaki örnekte gösterildiği gibi üç boyutlu bir dizi 5 katmanları, 12 satırlar ve sütunlar 31 bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b54e-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="3b54e-145">Her dizin, en fazla her boyutunun 0'dan değiştiğinden, Not `salesAmounts` o boyut için gerekli uzunluğundan küçük olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="3b54e-146">Ayrıca dizinin boyutu ile her yeni boyut arttığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3b54e-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="3b54e-147">Önceki örneklerde üç boyut 31 372 ve 1,860 öğeleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="3b54e-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b54e-148">Kullanmadan bir dizi oluşturabilirsiniz `Dim` deyimi veya `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3b54e-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="3b54e-149">Örneğin, çağırabilirsiniz <xref:System.Array.CreateInstance%2A> yöntemi veya başka bir bileşen geçirebilirsiniz kodunuzu bu şekilde oluşturulan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="3b54e-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="3b54e-150">Böyle bir dizi alt sınırı 0'dan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b54e-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="3b54e-151">Bir boyut için alt sınırı kullanarak her zaman test edebilirsiniz <xref:System.Array.GetLowerBound%2A> yöntemi veya `LBound` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3b54e-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b54e-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b54e-152">See also</span></span>
- [<span data-ttu-id="3b54e-153">Diziler</span><span class="sxs-lookup"><span data-stu-id="3b54e-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3b54e-154">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="3b54e-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
