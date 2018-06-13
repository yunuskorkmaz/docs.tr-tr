---
title: Değer türü &#39;type1&#39; dönüştürülemiyor &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602768"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="57f5b-102">Değer türü &#39;type1&#39; dönüştürülemiyor &#39;type2&#39;</span><span class="sxs-lookup"><span data-stu-id="57f5b-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="57f5b-103">'Type1' türünün değeri 'type2' dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="57f5b-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="57f5b-104">'Value' özelliği ilk öğesi dize değerini almak için kullanabileceğiniz '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="57f5b-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="57f5b-105">Belirli bir türünü değişmez değer XML dolaylı olarak bir girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="57f5b-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="57f5b-106">XML değişmez değeri belirtilen türe örtük olarak atanamaz.</span><span class="sxs-lookup"><span data-stu-id="57f5b-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="57f5b-107">**Hata Kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="57f5b-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57f5b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="57f5b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="57f5b-109">Kullanım `Value` değer olarak başvurmak için değişmez değer XML özelliğinin bir `String`.</span><span class="sxs-lookup"><span data-stu-id="57f5b-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="57f5b-110">Kullanım `CType` işlevi, başka bir tür dönüştürme işlevi veya <xref:System.Convert> sınıfı değeri belirtilen tür olarak yayınlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="57f5b-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f5b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57f5b-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="57f5b-112">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="57f5b-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="57f5b-113">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="57f5b-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="57f5b-114">XML</span><span class="sxs-lookup"><span data-stu-id="57f5b-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
