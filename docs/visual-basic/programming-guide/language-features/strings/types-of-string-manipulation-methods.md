---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic dize düzenleme yöntemlerinin türleri'
title: Visual Basic'te Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 02b127d5cd023a8bd73a3042a8bcec340ce63ed8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429760"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="a80e6-103">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="a80e6-103">Types of String Manipulation Methods in Visual Basic</span></span>

<span data-ttu-id="a80e6-104">Dizelerinizi çözümlemek ve işlemek için çeşitli farklı yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="a80e6-104">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="a80e6-105">Yöntemlerin bazıları Visual Basic dilin bir parçasıdır ve diğerleri sınıfına dahil edilir `String` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-105">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="a80e6-106">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a80e6-106">Visual Basic Language and the .NET Framework</span></span>  

 <span data-ttu-id="a80e6-107">Visual Basic Yöntemler, dilin devralınan işlevleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a80e6-107">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="a80e6-108">Kodunuzda nitelendirme olmadan kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="a80e6-108">They may be used without qualification in your code.</span></span> <span data-ttu-id="a80e6-109">Aşağıdaki örnek Visual Basic dize işleme komutunun tipik kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a80e6-109">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="a80e6-110">Bu örnekte, `Mid` işlevi üzerinde doğrudan bir işlem gerçekleştirir `aString` ve değerini öğesine atar `bString` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="a80e6-111">Visual Basic dize düzenleme yöntemlerinin listesi için bkz. [dize düzenleme Özeti](../../../language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="a80e6-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="a80e6-112">Paylaşılan Yöntemler ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a80e6-112">Shared Methods and Instance Methods</span></span>  

 <span data-ttu-id="a80e6-113">Dizeleri sınıfının yöntemleriyle de işleyebilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="a80e6-114">İçinde iki tür yöntem vardır `String` : *paylaşılan* Yöntemler ve *örnek* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a80e6-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="a80e6-115">Paylaşılan Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a80e6-115">Shared Methods</span></span>  

 <span data-ttu-id="a80e6-116">Paylaşılan bir yöntem, `String` sınıfın kendisinden kaynaklanan ve bu sınıfın bir örneğinin çalışmasını gerektirmeyen bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a80e6-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="a80e6-117">Bu yöntemler, `String` sınıfının bir örneğiyle değil, sınıfının () adıyla nitelenebilir `String` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="a80e6-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a80e6-118">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="a80e6-119">Yukarıdaki örnekte, <xref:System.String.Copy%2A?displayProperty=nameWithType> Yöntemi verilen bir ifadeye davranan ve elde edilen değeri atayan statik bir yöntemdir `bString` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-119">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="a80e6-120">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a80e6-120">Instance Methods</span></span>  

 <span data-ttu-id="a80e6-121">Örneğin, belirli bir örneğinden gövdeli örnek yöntemleri, `String` örnek adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a80e6-121">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="a80e6-122">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a80e6-122">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="a80e6-123">Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin `String` (yani,) bir yöntemidir `aString` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-123">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="a80e6-124">Üzerinde bir işlem gerçekleştirir `aString` ve bu değeri öğesine atar `bString` .</span><span class="sxs-lookup"><span data-stu-id="a80e6-124">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="a80e6-125">Daha fazla bilgi için, sınıfının belgelerine bakın <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="a80e6-125">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80e6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a80e6-126">See also</span></span>

- [<span data-ttu-id="a80e6-127">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="a80e6-127">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
