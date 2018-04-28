---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6d23aa54b150748aac9aa955f4bd86ee88358ea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="33b1c-102">XML Değişmez Değerlerinde Boşluk (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33b1c-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="33b1c-103">Visual Basic derleyici oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden içerir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi.</span><span class="sxs-lookup"><span data-stu-id="33b1c-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="33b1c-104">Önemsiz boşluk karakterleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="33b1c-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="33b1c-105">Önemli ve önemsiz beyaz alan</span><span class="sxs-lookup"><span data-stu-id="33b1c-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="33b1c-106">XML değişmez değerlerinde boşluk karakterleri yalnızca üç alana önemlidir:</span><span class="sxs-lookup"><span data-stu-id="33b1c-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="33b1c-107">Bir öznitelik değeri olduklarında.</span><span class="sxs-lookup"><span data-stu-id="33b1c-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="33b1c-108">Ne zaman bir öğenin metin içeriğini parçasıdır ve metin ayrıca diğer karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="33b1c-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="33b1c-109">Bir öğenin metin içeriği katıştırılmış bir ifadede olduklarında.</span><span class="sxs-lookup"><span data-stu-id="33b1c-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="33b1c-110">Aksi takdirde derleyici boşluk karakterleri önemsiz olarak değerlendirir ve ardından eklememeyi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değeri için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="33b1c-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="33b1c-111">XML değişmez değer anlamsız boşluk eklemek için bir boşluk ile değişmez dize değeri içeren katıştırılmış ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b1c-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33b1c-112">Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, Visual Basic derleyici özniteliğinde içeren <xref:System.Xml.Linq.XElement> nesnesi, ancak bu öznitelik derleyici boşluk nasıl işler değiştirmez ekleme.</span><span class="sxs-lookup"><span data-stu-id="33b1c-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="33b1c-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="33b1c-113">Examples</span></span>  
 <span data-ttu-id="33b1c-114">Aşağıdaki örnek, dış ve iç iki XML öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="33b1c-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="33b1c-115">Her iki öğeler, metin içeriğini boşluk içerir.</span><span class="sxs-lookup"><span data-stu-id="33b1c-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="33b1c-116">Boşluk Dış öğede yalnızca boşluk ve bir XML öğesi içerdiğinden önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="33b1c-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="33b1c-117">Boşluk iç öğesinde, boşluk ve metin içerdiği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="33b1c-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="33b1c-118">Bu kodu çalıştırdığınızda, aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="33b1c-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33b1c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33b1c-119">See Also</span></span>  
 [<span data-ttu-id="33b1c-120">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="33b1c-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
