---
title: Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: fa579303ad268a88269f360bdf626f9590c5d6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648501"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="7d372-102">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="7d372-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="7d372-103">Dizeleri işlemek ve çözümlemek için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="7d372-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="7d372-104">Bazı yöntemlere Visual Basic dilinin bir parçası olan ve diğerleri de belirlidir `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d372-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="7d372-105">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7d372-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="7d372-106">Visual Basic yöntemleri, doğal dil işlevleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d372-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="7d372-107">Kodunuzda nitelik olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d372-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="7d372-108">Aşağıdaki örnek, bir Visual Basic dize işleme komut tipik kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7d372-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="7d372-109">Bu örnekte, `Mid` işlevi üzerinde doğrudan bir işlem gerçekleştiren `aString` ve değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="7d372-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="7d372-110">Visual Basic dize düzenleme yöntemlerinin bir listesi için bkz [dize düzenleme özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="7d372-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="7d372-111">Paylaşılan ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7d372-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="7d372-112">Dize yöntemleri ile işleyebileceğiniz `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d372-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="7d372-113">Yöntemleri iki tür vardır `String`: *paylaşılan* yöntemleri ve *örneği* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7d372-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="7d372-114">Paylaşılan yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7d372-114">Shared Methods</span></span>  
 <span data-ttu-id="7d372-115">Paylaşılan bir yöntemine gelen kaynaklandığını yöntemdir `String` sınıfının kendisini ve çalışmak için bu sınıfın bir örneğini gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="7d372-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="7d372-116">Bu yöntemler, sınıfın adıyla nitelendirilmesi (`String`) yerine örneğiyle birlikte `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d372-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="7d372-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d372-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="7d372-118">Önceki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemi statik yöntem bir ifade üzerinde çalışan verilir ve çıkan değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="7d372-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="7d372-119">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7d372-119">Instance Methods</span></span>  
 <span data-ttu-id="7d372-120">Örnek yöntemleri, aksine, belirli bir örneğini kökü `String` ve örnek adı ile nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d372-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="7d372-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d372-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="7d372-122">Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemdir örneğinin bir yöntemin `String` (diğer bir deyişle, `aString`).</span><span class="sxs-lookup"><span data-stu-id="7d372-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="7d372-123">Üzerinde bir işlem gerçekleştirir `aString` ve bu değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="7d372-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="7d372-124">Daha fazla bilgi için belgelerine bakın <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d372-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d372-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d372-125">See also</span></span>
- [<span data-ttu-id="7d372-126">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="7d372-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
