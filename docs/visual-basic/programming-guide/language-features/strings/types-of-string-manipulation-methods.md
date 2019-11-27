---
title: Visual Basic'te Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346277"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="4d37a-102">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="4d37a-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="4d37a-103">Dizelerinizi çözümlemek ve işlemek için çeşitli farklı yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="4d37a-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="4d37a-104">Yöntemlerin bazıları Visual Basic dilin bir parçasıdır ve diğerleri `String` sınıfına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="4d37a-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="4d37a-105">Visual Basic dili ve .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d37a-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="4d37a-106">Visual Basic Yöntemler, dilin devralınan işlevleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d37a-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="4d37a-107">Kodunuzda nitelendirme olmadan kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="4d37a-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="4d37a-108">Aşağıdaki örnek Visual Basic dize işleme komutunun tipik kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4d37a-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="4d37a-109">Bu örnekte, `Mid` işlevi `aString` üzerinde doğrudan işlem gerçekleştirir ve değeri `bString`atar.</span><span class="sxs-lookup"><span data-stu-id="4d37a-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="4d37a-110">Visual Basic dize düzenleme yöntemlerinin listesi için bkz. [dize düzenleme Özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="4d37a-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="4d37a-111">Paylaşılan Yöntemler ve örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4d37a-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="4d37a-112">Ayrıca, `String` sınıfının yöntemleriyle dizeleri de yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d37a-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="4d37a-113">`String`iki tür yöntem vardır: *paylaşılan* Yöntemler ve *örnek* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4d37a-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="4d37a-114">Paylaşılan Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d37a-114">Shared Methods</span></span>  
 <span data-ttu-id="4d37a-115">Paylaşılan bir yöntem, `String` sınıfından kaynaklanan ve bu sınıfın bir örneğinin çalışmasını gerektirmeyen bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4d37a-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="4d37a-116">Bu yöntemler, `String` sınıfının bir örneği yerine, sınıfın adı (`String`) ile nitelenebilir.</span><span class="sxs-lookup"><span data-stu-id="4d37a-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="4d37a-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4d37a-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="4d37a-118">Yukarıdaki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemi, verilen bir ifadeye davranan ve elde edilen değeri `bString`atayan statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4d37a-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="4d37a-119">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4d37a-119">Instance Methods</span></span>  
 <span data-ttu-id="4d37a-120">Örneğin, belirli bir `String` örneğinden gövdeli örnek yöntemleri, örnek adı ile nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4d37a-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="4d37a-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4d37a-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="4d37a-122">Bu örnekte <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi, `String` örneğinin bir yöntemidir (yani, `aString`).</span><span class="sxs-lookup"><span data-stu-id="4d37a-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="4d37a-123">`aString` bir işlem gerçekleştirir ve bu değeri `bString`atar.</span><span class="sxs-lookup"><span data-stu-id="4d37a-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="4d37a-124">Daha fazla bilgi için <xref:System.String> sınıfına yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="4d37a-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d37a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d37a-125">See also</span></span>

- [<span data-ttu-id="4d37a-126">Visual Basic dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="4d37a-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
