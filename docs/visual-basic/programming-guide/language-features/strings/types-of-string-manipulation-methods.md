---
title: Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 11903e067c064f129ecd2df80244edb6741c73be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648700"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="9b4b6-102">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="9b4b6-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="9b4b6-103">Analiz etmek ve dizelerinizi işlemek için birkaç farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="9b4b6-104">Yöntemlerin bazıları Visual Basic Dil parçası olan ve diğerleri de devralınan `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="9b4b6-105">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b4b6-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="9b4b6-106">Visual Basic yöntemleri dil devralınmış işlevler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="9b4b6-107">Kodunuzu nitelikte olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="9b4b6-108">Aşağıdaki örnek, bir Visual Basic dize düzenlemesi komutu tipik kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9b4b6-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="9b4b6-109">Bu örnekte, `Mid` işlevi gerçekleştirir doğrudan işlemi `aString` ve değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="9b4b6-110">Visual Basic dize düzenleme yöntemlerinin listesi için bkz [dize düzenleme özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="9b4b6-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="9b4b6-111">Paylaşılan ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="9b4b6-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="9b4b6-112">Dize yöntemleri ile işleyebileceğiniz `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="9b4b6-113">İki tür yöntemleri vardır `String`: *paylaşılan* yöntemleri ve *örneği* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="9b4b6-114">Paylaşılan yöntemleri</span><span class="sxs-lookup"><span data-stu-id="9b4b6-114">Shared Methods</span></span>  
 <span data-ttu-id="9b4b6-115">Bir paylaşılan yöntemi gelen kaynaklandığını yöntemdir `String` sınıfının kendisini ve çalışmak için bu sınıfının bir örneği gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="9b4b6-116">Bu yöntemlerden sınıfın adını nitelenmiş olmalıdır (`String`) yerine bir örneğiyle `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="9b4b6-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9b4b6-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="9b4b6-118">Önceki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemdir bir ifade üzerinde çalışan verilir ve çıkan değeri atar bir statik yöntem `bString`.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="9b4b6-119">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="9b4b6-119">Instance Methods</span></span>  
 <span data-ttu-id="9b4b6-120">Örnek yöntemleri, bunun aksine, belirli bir örneği gövdesi `String` ve örnek adıyla nitelendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="9b4b6-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9b4b6-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="9b4b6-122">Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin bir yöntemdir `String` (diğer bir deyişle, `aString`).</span><span class="sxs-lookup"><span data-stu-id="9b4b6-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="9b4b6-123">Üzerinde bir işlemi gerçekleştiren `aString` ve bu değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="9b4b6-124">Daha fazla bilgi için belgelerine bakın <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4b6-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b4b6-125">See Also</span></span>  
 [<span data-ttu-id="9b4b6-126">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="9b4b6-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
