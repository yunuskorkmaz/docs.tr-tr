---
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827152"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="67e1b-102">'type1' türünün değeri 'type2' olarak dönüştürülemez</span><span class="sxs-lookup"><span data-stu-id="67e1b-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="67e1b-103">'Type1' türünün değeri 'type2' olarak dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="67e1b-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="67e1b-104">'Value' özelliğini ilk öğesinin dize değerini almak için kullanabileceğiniz '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="67e1b-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="67e1b-105">Belirli bir türe sabit değeri bir XML dolaylı olarak girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="67e1b-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="67e1b-106">XML değişmez değeri belirtilen türe örtük olarak yayınlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="67e1b-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="67e1b-107">**Hata Kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="67e1b-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67e1b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="67e1b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="67e1b-109">Kullanım `Value` özellik değeri olarak başvurmak için XML değişmez bir `String`.</span><span class="sxs-lookup"><span data-stu-id="67e1b-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="67e1b-110">Kullanım `CType` işlev, başka bir tür dönüştürme işlevi veya <xref:System.Convert> belirtilen tür olarak değerde dönüştürme yapmak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67e1b-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e1b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e1b-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="67e1b-112">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="67e1b-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="67e1b-113">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="67e1b-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="67e1b-114">XML</span><span class="sxs-lookup"><span data-stu-id="67e1b-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
