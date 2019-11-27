---
title: Dizilerle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349074"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="5a65c-102">Dizilerle İlgili Sorun Giderme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a65c-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="5a65c-103">Bu sayfada, dizilerle çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="5a65c-104">Bir diziyi bildiren ve başlatarak derleme hataları</span><span class="sxs-lookup"><span data-stu-id="5a65c-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="5a65c-105">Derleme hataları, dizileri bildirmek, oluşturmak ve başlatmak için kuralların yanlış anlaşılmasından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="5a65c-106">Hataların en yaygın nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a65c-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="5a65c-107">Dizi değişkeni bildiriminde boyut uzunluklarını belirttikten sonra [Yeni bir işleç](../../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi sağlama.</span><span class="sxs-lookup"><span data-stu-id="5a65c-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="5a65c-108">Aşağıdaki kod satırları bu türün geçersiz bildirimlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="5a65c-109">Pürüzlü bir dizinin en üst düzey dizisinden daha fazla boyut uzunluğu belirtme.</span><span class="sxs-lookup"><span data-stu-id="5a65c-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="5a65c-110">Aşağıdaki kod satırı, bu türün geçersiz bir bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="5a65c-111">Öğe değerlerini belirtirken `New` anahtar sözcüğünü atlama.</span><span class="sxs-lookup"><span data-stu-id="5a65c-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="5a65c-112">Aşağıdaki kod satırı, bu türün geçersiz bir bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="5a65c-113">Küme ayracı olmadan bir `New` yan tümcesi sağlama (`{}`).</span><span class="sxs-lookup"><span data-stu-id="5a65c-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="5a65c-114">Aşağıdaki kod satırları bu türün geçersiz bildirimlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="5a65c-115">Dizi sınırların dışına erişme</span><span class="sxs-lookup"><span data-stu-id="5a65c-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="5a65c-116">Bir diziyi başlatma işlemi, her boyuta bir üst sınır ve alt sınır atar.</span><span class="sxs-lookup"><span data-stu-id="5a65c-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="5a65c-117">Dizi öğesine her erişim için her boyut için geçerli bir dizin veya alt simge belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="5a65c-118">Herhangi bir dizin alt sınırının altında veya üst sınırının üstünde olursa, <xref:System.IndexOutOfRangeException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a65c-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="5a65c-119">Derleyici bu tür bir hatayı algılayamazsınız, bu nedenle çalışma zamanında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a65c-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="5a65c-120">Sınırları belirleme</span><span class="sxs-lookup"><span data-stu-id="5a65c-120">Determining Bounds</span></span>  
 <span data-ttu-id="5a65c-121">Başka bir bileşen kodunuza bir dizi geçirirse (örneğin, bir yordam bağımsız değişkeni olarak), bu dizinin boyutunu veya boyutlarının uzunluğunu bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a65c-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="5a65c-122">Herhangi bir öğeye erişmeyi denemeden önce her zaman bir dizinin her boyutu için üst sınırı belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5a65c-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="5a65c-123">Dizi Visual Basic `New` yan tümcesi dışında bazı yollarla oluşturulduysa, alt sınır 0 dışında bir değer olabilir ve bu alt sınırın de belirlenmesi en güvenli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="5a65c-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="5a65c-124">Boyut belirtme</span><span class="sxs-lookup"><span data-stu-id="5a65c-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="5a65c-125">Çok boyutlu bir dizinin sınırlarını belirlerken, boyutu nasıl belirteceğini dikkatli yapın.</span><span class="sxs-lookup"><span data-stu-id="5a65c-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="5a65c-126"><xref:System.Array.GetLowerBound%2A> ve <xref:System.Array.GetUpperBound%2A> yöntemlerinin `dimension` parametreleri 0 tabanlıdır, ancak Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> `Rank` parametreleri ve <xref:Microsoft.VisualBasic.Information.UBound%2A> işlevleri 1 tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a65c-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a65c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a65c-127">See also</span></span>

- [<span data-ttu-id="5a65c-128">Diziler</span><span class="sxs-lookup"><span data-stu-id="5a65c-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="5a65c-129">Nasıl yapılır: Visual Basic dizi değişkenini başlatma</span><span class="sxs-lookup"><span data-stu-id="5a65c-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
