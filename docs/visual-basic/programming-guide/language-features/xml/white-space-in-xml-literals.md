---
description: 'Hakkında daha fazla bilgi edinin: XML değişmez değerlerinde boşluk (Visual Basic)'
title: XML Değişmez Değerlerinde Boşluk
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 9b4134626c0ad1f7f4be2923573eb6058fa7687f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428122"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="3e726-103">XML Değişmez Değerlerinde Boşluk (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e726-103">White Space in XML Literals (Visual Basic)</span></span>

<span data-ttu-id="3e726-104">Visual Basic derleyici bir nesne oluşturduğunda yalnızca bir XML sabit değerinden önemli boşluk karakterleri ekler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3e726-104">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="3e726-105">Önemli boşluk karakterleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="3e726-105">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="3e726-106">Önemli ve çok önemli boşluk</span><span class="sxs-lookup"><span data-stu-id="3e726-106">Significant and Insignificant White Space</span></span>  

 <span data-ttu-id="3e726-107">XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda önemlidir:</span><span class="sxs-lookup"><span data-stu-id="3e726-107">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="3e726-108">Bir öznitelik değeri olduğunda.</span><span class="sxs-lookup"><span data-stu-id="3e726-108">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="3e726-109">Bir öğenin metin içeriğinin bir parçası olduklarında ve metin diğer karakterleri de içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="3e726-109">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="3e726-110">Bir öğenin metin içeriği için gömülü bir ifadede olduklarında.</span><span class="sxs-lookup"><span data-stu-id="3e726-110">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="3e726-111">Aksi halde, derleyici boşluk karakterlerini önemli olarak değerlendirir ve daha sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer için nesnesine içermez.</span><span class="sxs-lookup"><span data-stu-id="3e726-111">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="3e726-112">Bir XML sabit değerinde boş bir boşluk eklemek için, boşluk içeren bir dize sabit değeri içeren gömülü bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e726-112">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e726-113">`xml:space`Öznitelik BIR XML öğesi değişmez değerinde görünürse, Visual Basic derleyici nesnedeki özniteliği içerir <xref:System.Xml.Linq.XElement> , ancak bu özniteliği eklemek derleyicinin boşluk olarak nasıl davrandığını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="3e726-113">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3e726-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3e726-114">Examples</span></span>  

 <span data-ttu-id="3e726-115">Aşağıdaki örnek, Outer ve Inner olmak üzere iki XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="3e726-115">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="3e726-116">Her iki öğe de metin içeriklerinde boşluk içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3e726-116">Both elements contain white space in their text content.</span></span> <span data-ttu-id="3e726-117">Dış öğedeki boşluk, yalnızca boşluk ve bir XML öğesi içerdiği için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3e726-117">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="3e726-118">İç öğedeki boşluk, boşluk ve metin içerdiğinden önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3e726-118">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="3e726-119">Çalıştırıldığında, bu kod aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3e726-119">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e726-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e726-120">See also</span></span>

- [<span data-ttu-id="3e726-121">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e726-121">Creating XML in Visual Basic</span></span>](creating-xml.md)
