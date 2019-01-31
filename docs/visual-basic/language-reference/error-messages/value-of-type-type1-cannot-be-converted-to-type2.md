---
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: eb30d63e83452e75f353c44a9d0445c7dbb1013a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287514"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="920c3-102">'type1' türünün değeri 'type2' olarak dönüştürülemez</span><span class="sxs-lookup"><span data-stu-id="920c3-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="920c3-103">'Type1' türünün değeri 'type2' olarak dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="920c3-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="920c3-104">'Value' özelliğini ilk öğesinin dize değerini almak için kullanabileceğiniz '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="920c3-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="920c3-105">Belirli bir türe sabit değeri bir XML dolaylı olarak girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="920c3-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="920c3-106">XML değişmez değeri belirtilen türe örtük olarak yayınlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="920c3-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="920c3-107">**Hata Kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="920c3-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="920c3-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="920c3-108">To correct this error</span></span>  
  
-   <span data-ttu-id="920c3-109">Kullanım `Value` özellik değeri olarak başvurmak için XML değişmez bir `String`.</span><span class="sxs-lookup"><span data-stu-id="920c3-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="920c3-110">Kullanım `CType` işlev, başka bir tür dönüştürme işlevi veya <xref:System.Convert> belirtilen tür olarak değerde dönüştürme yapmak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="920c3-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920c3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="920c3-111">See also</span></span>
- <xref:System.Convert>
- [<span data-ttu-id="920c3-112">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="920c3-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="920c3-113">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="920c3-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="920c3-114">XML</span><span class="sxs-lookup"><span data-stu-id="920c3-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
