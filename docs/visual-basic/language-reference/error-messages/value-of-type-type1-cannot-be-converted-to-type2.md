---
title: "Değer türü &#39; type1 &#39; dönüştürülemiyor &#39; type2 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="fe714-102">Değer türü &#39; type1 &#39; dönüştürülemiyor &#39; type2 &#39;</span><span class="sxs-lookup"><span data-stu-id="fe714-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="fe714-103">'Type1' türünün değeri 'type2' dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="fe714-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="fe714-104">'Value' özelliği ilk öğesi dize değerini almak için kullanabileceğiniz '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="fe714-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="fe714-105">Belirli bir türünü değişmez değer XML dolaylı olarak bir girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="fe714-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="fe714-106">XML değişmez değeri belirtilen türe örtük olarak atanamaz.</span><span class="sxs-lookup"><span data-stu-id="fe714-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="fe714-107">**Hata Kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="fe714-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe714-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fe714-108">To correct this error</span></span>  
  
-   <span data-ttu-id="fe714-109">Kullanım `Value` değer olarak başvurmak için değişmez değer XML özelliğinin bir `String`.</span><span class="sxs-lookup"><span data-stu-id="fe714-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="fe714-110">Kullanım `CType` işlevi, başka bir tür dönüştürme işlevi veya <xref:System.Convert> sınıfı değeri belirtilen tür olarak yayınlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="fe714-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe714-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe714-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="fe714-112">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="fe714-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fe714-113">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="fe714-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="fe714-114">XML</span><span class="sxs-lookup"><span data-stu-id="fe714-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
