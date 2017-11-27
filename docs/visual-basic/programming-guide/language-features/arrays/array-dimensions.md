---
title: "Visual Basic'de Dizi Boyutları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="71238-102">Visual Basic'de Dizi Boyutları</span><span class="sxs-lookup"><span data-stu-id="71238-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="71238-103">A *boyut* içinde gösterebilir bir dizinin öğelerini belirtimi bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="71238-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="71238-104">Satış her ay gün için toplam tutan bir dizi bir boyut (ayın günü) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="71238-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="71238-105">Satış toplam bölüm tarafından her ayın için tutan bir dizi (bölüm numarası ve ayın günü) iki boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="71238-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="71238-106">Bir dizisi olduğundan dimensions sayısı adlı kendi *derece*.</span><span class="sxs-lookup"><span data-stu-id="71238-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71238-107">Kullanabileceğiniz <xref:System.Array.Rank%2A> kaç boyutları bir dizisi olduğundan belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="71238-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="71238-108">Boyutlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="71238-108">Working with Dimensions</span></span>  
 <span data-ttu-id="71238-109">Sağlayarak bir dizi bir öğe belirtin bir *dizin* veya *alt simge* her boyutları.</span><span class="sxs-lookup"><span data-stu-id="71238-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="71238-110">Her boyut bitişik o boyutu için en yüksek dizin aracılığıyla 0 dizinden öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="71238-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="71238-111">Aşağıdaki çizimler farklı sıralar dizilerle kavramsal yapısını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="71238-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="71238-112">Her bir öğesinde çizimler erişim dizin değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="71238-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="71238-113">Örneğin, ikinci satırın iki boyutlu dizinin ilk öğesi dizinleri belirterek erişebileceğiniz `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="71238-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="71238-114">![Bir &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="71238-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="71238-115">Tek boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="71238-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="71238-116">![İki &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="71238-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="71238-117">İki boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="71238-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="71238-118">![Üç &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="71238-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="71238-119">Üç boyutlu dizi</span><span class="sxs-lookup"><span data-stu-id="71238-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="71238-120">Bir boyut</span><span class="sxs-lookup"><span data-stu-id="71238-120">One Dimension</span></span>  
 <span data-ttu-id="71238-121">Birçok diziler her yaş kişiler sayısı gibi yalnızca bir boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="71238-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="71238-122">Bu öğe sayısı tutan yaş yalnızca bir öğe belirtin gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="71238-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="71238-123">Bu nedenle, bu tür bir dizi yalnızca bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="71238-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="71238-124">Aşağıdaki örnek tutmak için bir değişken bildiren bir *tek boyutlu dizi* yaş 0 ile 120 için yaşını sayar.</span><span class="sxs-lookup"><span data-stu-id="71238-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="71238-125">İki boyutu</span><span class="sxs-lookup"><span data-stu-id="71238-125">Two Dimensions</span></span>  
 <span data-ttu-id="71238-126">Bazı diziler iki boyutları, her bir yerleşkede oluşturmanın her aşamasında ofisleri sayısı gibi sahip.</span><span class="sxs-lookup"><span data-stu-id="71238-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="71238-127">Bir öğenin belirtimi bina numarasını ve kat gerektirir ve her öğe sayısı bina ve kat birleşimi için tutar.</span><span class="sxs-lookup"><span data-stu-id="71238-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="71238-128">Bu nedenle, bu tür bir dizi iki dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="71238-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="71238-129">Aşağıdaki örnek tutmak için bir değişken bildiren bir *iki boyutlu dizi* office sayısının binalar 0 ile 40 ve Katlar 0 ile 5.</span><span class="sxs-lookup"><span data-stu-id="71238-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="71238-130">İki boyutlu bir dizi olarak da adlandırılan bir *dikdörtgen dizi*.</span><span class="sxs-lookup"><span data-stu-id="71238-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="71238-131">Üç boyut</span><span class="sxs-lookup"><span data-stu-id="71238-131">Three Dimensions</span></span>  
 <span data-ttu-id="71238-132">Birkaç diziler üç boyutlu alan değerleri gibi üç boyut sahip.</span><span class="sxs-lookup"><span data-stu-id="71238-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="71238-133">Bu tür bir dizi bu durumda x, y ve fiziksel alan z koordinatları temsil üç dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="71238-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="71238-134">Aşağıdaki örnek tutmak için bir değişken bildiren bir *üç boyutlu dizi* , üç boyutlu bir birim çeşitli yerlerinde hava etme.</span><span class="sxs-lookup"><span data-stu-id="71238-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="71238-135">Birden fazla üç boyut</span><span class="sxs-lookup"><span data-stu-id="71238-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="71238-136">Bir dizi olarak en fazla 32 boyutları sahip olabilirsiniz, ancak en fazla üç sahip nadir.</span><span class="sxs-lookup"><span data-stu-id="71238-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71238-137">Bir dizi boyutları eklediğinizde, toplam depolama dizisi tarafından gereken önemli ölçüde, bunu kullanmak çok boyutlu diziler dikkatli artırır.</span><span class="sxs-lookup"><span data-stu-id="71238-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="71238-138">Farklı boyutları kullanma</span><span class="sxs-lookup"><span data-stu-id="71238-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="71238-139">Her ayın mevcut için satış tutarlarının izlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="71238-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="71238-140">Aşağıdaki örnek olarak ayın her günü için gösterir tek boyutlu dizi 31 öğelerle bildirme.</span><span class="sxs-lookup"><span data-stu-id="71238-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="71238-141">Şimdi, aynı bilgileri, her gün için yalnızca bir ay aynı zamanda yılın her ay için izlemek istediğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="71238-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="71238-142">Aşağıdaki örnekte gösterildiği gibi iki boyutlu bir dizi 12 satırlar (ay için) ve (gündür), 31 sütunlarla bildirme.</span><span class="sxs-lookup"><span data-stu-id="71238-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="71238-143">Şimdi sahip karar varsayalım bilgi birden fazla bir yıl için dizinizi tutun.</span><span class="sxs-lookup"><span data-stu-id="71238-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="71238-144">Satış tutarlarının 5 yıl boyunca izlemek isterseniz, aşağıdaki örnekte gösterildiği gibi üç boyutlu bir dizi 5 katmanlar, 12 satırları ve 31 sütunlarla bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71238-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="71238-145">Her dizin, en çok her boyutu 0'dan değiştiğinden, Not `salesAmounts` o boyut için bir gerekli uzunluğundan daha az olarak bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="71238-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="71238-146">Ayrıca, dizi boyutu her yeni bir boyut ile artar unutmayın.</span><span class="sxs-lookup"><span data-stu-id="71238-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="71238-147">Üç önceki örneklerde 31, 372 ve 1,860 öğeleri sırasıyla boyutlarıdır.</span><span class="sxs-lookup"><span data-stu-id="71238-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71238-148">Bir dizi kullanmadan oluşturabileceğiniz `Dim` deyimi veya `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="71238-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="71238-149">Örneğin, çağırabilirsiniz <xref:System.Array.CreateInstance%2A> yöntemi ya da başka bir bileşen iletebilir kodunuzu bu şekilde oluşturulan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71238-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="71238-150">Bu tür bir dizi alt sınırı 0'dan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="71238-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="71238-151">Kullanarak her zaman bir boyutun alt sınır için bir test edebilirsiniz <xref:System.Array.GetLowerBound%2A> yöntemi veya `LBound` işlevi.</span><span class="sxs-lookup"><span data-stu-id="71238-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71238-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71238-152">See Also</span></span>  
 [<span data-ttu-id="71238-153">Diziler</span><span class="sxs-lookup"><span data-stu-id="71238-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="71238-154">Dizilerle ilgili sorun giderme</span><span class="sxs-lookup"><span data-stu-id="71238-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
