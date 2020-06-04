---
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400285"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="b14cb-102">'type1' türünün değeri 'type2' olarak dönüştürülemez</span><span class="sxs-lookup"><span data-stu-id="b14cb-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="b14cb-103">' Type1 ' türünün değeri ' type2 ' olarak dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="b14cb-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="b14cb-104">' ' Öğesinin ilk öğesinin dize değerini almak için ' Value ' özelliğini kullanabilirsiniz \<parentElement> .</span><span class="sxs-lookup"><span data-stu-id="b14cb-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="b14cb-105">Bir XML sabit değerini örtük olarak belirli bir türe atama girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="b14cb-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="b14cb-106">XML sabit değeri örtük olarak belirtilen türe atanamaz.</span><span class="sxs-lookup"><span data-stu-id="b14cb-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="b14cb-107">**Hata kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="b14cb-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b14cb-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b14cb-108">To correct this error</span></span>  
  
- <span data-ttu-id="b14cb-109">`Value`Değeri olarak başvurmak IÇIN XML sabit değerinin özelliğini kullanın `String` .</span><span class="sxs-lookup"><span data-stu-id="b14cb-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="b14cb-110">`CType` <xref:System.Convert> Değeri belirtilen tür olarak atamak için işlevi, başka bir tür dönüştürme işlevini veya sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b14cb-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14cb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b14cb-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="b14cb-112">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b14cb-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="b14cb-113">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="b14cb-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="b14cb-114">XML</span><span class="sxs-lookup"><span data-stu-id="b14cb-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
