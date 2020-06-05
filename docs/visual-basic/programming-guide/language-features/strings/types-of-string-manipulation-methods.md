---
title: Visual Basic'te Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363765"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="4d510-102">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="4d510-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="4d510-103">Dizelerinizi çözümlemek ve işlemek için çeşitli farklı yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="4d510-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="4d510-104">Yöntemlerin bazıları Visual Basic dilin bir parçasıdır ve diğerleri sınıfına dahil edilir `String` .</span><span class="sxs-lookup"><span data-stu-id="4d510-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="4d510-105">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d510-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="4d510-106">Visual Basic Yöntemler, dilin devralınan işlevleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d510-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="4d510-107">Kodunuzda nitelendirme olmadan kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="4d510-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="4d510-108">Aşağıdaki örnek Visual Basic dize işleme komutunun tipik kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4d510-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="4d510-109">Bu örnekte, `Mid` işlevi üzerinde doğrudan bir işlem gerçekleştirir `aString` ve değerini öğesine atar `bString` .</span><span class="sxs-lookup"><span data-stu-id="4d510-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="4d510-110">Visual Basic dize düzenleme yöntemlerinin listesi için bkz. [dize düzenleme Özeti](../../../language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="4d510-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="4d510-111">Paylaşılan Yöntemler ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4d510-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="4d510-112">Dizeleri sınıfının yöntemleriyle de işleyebilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="4d510-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="4d510-113">İçinde iki tür yöntem vardır `String` : *paylaşılan* Yöntemler ve *örnek* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4d510-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="4d510-114">Paylaşılan Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d510-114">Shared Methods</span></span>  
 <span data-ttu-id="4d510-115">Paylaşılan bir yöntem, `String` sınıfın kendisinden kaynaklanan ve bu sınıfın bir örneğinin çalışmasını gerektirmeyen bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4d510-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="4d510-116">Bu yöntemler, `String` sınıfının bir örneğiyle değil, sınıfının () adıyla nitelenebilir `String` .</span><span class="sxs-lookup"><span data-stu-id="4d510-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="4d510-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4d510-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="4d510-118">Yukarıdaki örnekte, <xref:System.String.Copy%2A?displayProperty=nameWithType> Yöntemi verilen bir ifadeye davranan ve elde edilen değeri atayan statik bir yöntemdir `bString` .</span><span class="sxs-lookup"><span data-stu-id="4d510-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="4d510-119">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4d510-119">Instance Methods</span></span>  
 <span data-ttu-id="4d510-120">Örneğin, belirli bir örneğinden gövdeli örnek yöntemleri, `String` örnek adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4d510-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="4d510-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4d510-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="4d510-122">Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin `String` (yani,) bir yöntemidir `aString` .</span><span class="sxs-lookup"><span data-stu-id="4d510-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="4d510-123">Üzerinde bir işlem gerçekleştirir `aString` ve bu değeri öğesine atar `bString` .</span><span class="sxs-lookup"><span data-stu-id="4d510-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="4d510-124">Daha fazla bilgi için, sınıfının belgelerine bakın <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="4d510-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d510-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d510-125">See also</span></span>

- [<span data-ttu-id="4d510-126">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="4d510-126">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
