---
title: "Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="0bc4a-102">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="0bc4a-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="0bc4a-103">Analiz etmek ve dizelerinizi işlemek için birkaç farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="0bc4a-104">Yöntemlerin bazıları bir parçası olan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dil ve diğerleri de devralınan `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-104">Some of the methods are a part of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="0bc4a-105">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0bc4a-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="0bc4a-106">yöntemleri dil devralınmış işlevler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="0bc4a-107">Kodunuzu nitelikte olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="0bc4a-108">Aşağıdaki örnek, tipik kullanımını gösterir bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dize işleme komutu:</span><span class="sxs-lookup"><span data-stu-id="0bc4a-108">The following example shows typical use of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="0bc4a-109">Bu örnekte, `Mid` işlevi gerçekleştirir doğrudan işlemi `aString` ve değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="0bc4a-110">Visual Basic dize düzenleme yöntemlerinin listesi için bkz [dize düzenleme özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="0bc4a-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="0bc4a-111">Paylaşılan ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0bc4a-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="0bc4a-112">Dize yöntemleri ile işleyebileceğiniz `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="0bc4a-113">İki tür yöntemleri vardır `String`: *paylaşılan* yöntemleri ve *örneği* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="0bc4a-114">Paylaşılan yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0bc4a-114">Shared Methods</span></span>  
 <span data-ttu-id="0bc4a-115">Bir paylaşılan yöntemi gelen kaynaklandığını yöntemdir `String` sınıfının kendisini ve çalışmak için bu sınıfının bir örneği gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="0bc4a-116">Bu yöntemlerden sınıfın adını nitelenmiş olmalıdır (`String`) yerine bir örneğiyle `String` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="0bc4a-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0bc4a-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="0bc4a-118">Önceki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemdir bir ifade üzerinde çalışan verilir ve çıkan değeri atar bir statik yöntem `bString`.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="0bc4a-119">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0bc4a-119">Instance Methods</span></span>  
 <span data-ttu-id="0bc4a-120">Örnek yöntemleri, bunun aksine, belirli bir örneği gövdesi `String` ve örnek adıyla nitelendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="0bc4a-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0bc4a-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="0bc4a-122">Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin bir yöntemdir `String` (diğer bir deyişle, `aString`).</span><span class="sxs-lookup"><span data-stu-id="0bc4a-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="0bc4a-123">Üzerinde bir işlemi gerçekleştiren `aString` ve bu değeri atar `bString`.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="0bc4a-124">Daha fazla bilgi için belgelerine bakın <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc4a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bc4a-125">See Also</span></span>  
 [<span data-ttu-id="0bc4a-126">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="0bc4a-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
