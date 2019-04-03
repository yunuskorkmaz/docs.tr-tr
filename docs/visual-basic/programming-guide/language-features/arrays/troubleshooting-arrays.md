---
title: Dizilerle İlgili Sorun Giderme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833379"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="b1f12-102">Dizilerle İlgili Sorun Giderme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1f12-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="b1f12-103">Bu sayfada dizilerle çalışırken ortaya çıkabilecek bazı yaygın sorunlar listelenir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="b1f12-104">Derleme hataları bildirme ve bir dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="b1f12-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="b1f12-105">Yanlış anlama bildirme, oluşturma ve dizileri başlatma kurallarını, gelen derleme hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="b1f12-106">Hataların en yaygın nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b1f12-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="b1f12-107">Sağlama bir [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) boyutun uzunluğu dizi değişken bildiriminde belirttikten sonra yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b1f12-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="b1f12-108">Aşağıdaki kod satırları bu türünde geçersiz bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="b1f12-109">Birden çok basit bir dizi en üst düzey dizi boyut uzunlukları belirtme.</span><span class="sxs-lookup"><span data-stu-id="b1f12-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="b1f12-110">Aşağıdaki kod satırı, bu tür geçersiz bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="b1f12-111">Atlama `New` öğe değerlerini belirlerken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b1f12-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="b1f12-112">Aşağıdaki kod satırı, bu tür geçersiz bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="b1f12-113">Sağlama bir `New` yan tümcesi küme ayraçları olmadan (`{}`).</span><span class="sxs-lookup"><span data-stu-id="b1f12-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="b1f12-114">Aşağıdaki kod satırları bu türünde geçersiz bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="b1f12-115">Bir dizi je mimo rozsah erişme</span><span class="sxs-lookup"><span data-stu-id="b1f12-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="b1f12-116">Dizi başlatma işlemi, her boyut için üst limit ve alt sınırı atar.</span><span class="sxs-lookup"><span data-stu-id="b1f12-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="b1f12-117">Her bir öğe dizinin erişim, geçerli dizin veya her boyut için alt simge belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="b1f12-118">Herhangi bir dizini altında kendi alt sınır veya üst sınır, yukarıda ise bir <xref:System.IndexOutOfRangeException> özel durum sonuçları.</span><span class="sxs-lookup"><span data-stu-id="b1f12-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="b1f12-119">Çalışma zamanında bir hata oluşmaz derleyici bu tür bir hataya algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="b1f12-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="b1f12-120">Sınırları belirleme</span><span class="sxs-lookup"><span data-stu-id="b1f12-120">Determining Bounds</span></span>  
 <span data-ttu-id="b1f12-121">Başka bir bileşen, kodunuzu bir dizi geçerse, örneğin bir yordam bağımsız değişken olarak, bu dizinin boyutu veya boyutlarının uzunluklarının bilmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f12-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="b1f12-122">Herhangi bir öğe erişmeye çalışmadan önce her zaman bir dizinin her boyutunun üst sınırını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="b1f12-123">Dizi dışındaki bir Visual Basic bazı yollarla oluşturulduysa `New` yan tümcesi alt sınırı 0 dışında bir şey olabilir ve de bu alt sınır belirlemek en güvenlisidir.</span><span class="sxs-lookup"><span data-stu-id="b1f12-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="b1f12-124">Boyut belirtme</span><span class="sxs-lookup"><span data-stu-id="b1f12-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="b1f12-125">Çok boyutlu bir dizinin sınırları belirlerken, boyut nasıl belirttiğiniz ilgileniriz.</span><span class="sxs-lookup"><span data-stu-id="b1f12-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="b1f12-126">`dimension` Parametrelerinin <xref:System.Array.GetLowerBound%2A> ve <xref:System.Array.GetUpperBound%2A> yöntemleri 0 tabanlıdır; çalışırken `Rank` Visual Basic parametrelerinin <xref:Microsoft.VisualBasic.Information.LBound%2A> ve <xref:Microsoft.VisualBasic.Information.UBound%2A> işlevleri 1 tabanlı.</span><span class="sxs-lookup"><span data-stu-id="b1f12-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f12-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f12-127">See also</span></span>

- [<span data-ttu-id="b1f12-128">Diziler</span><span class="sxs-lookup"><span data-stu-id="b1f12-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="b1f12-129">Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma</span><span class="sxs-lookup"><span data-stu-id="b1f12-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
