---
description: "Hakkında daha fazla bilgi edinin: BC31194: ' type1 ' türünün değeri ' type2 ' olarak dönüştürülemez"
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8cdb5206f0bc09a447ce241921b0efda63792c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674785"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="701d4-103">BC31194: ' type1 ' türündeki değer ' type2 ' olarak dönüştürülemez</span><span class="sxs-lookup"><span data-stu-id="701d4-103">BC31194: Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="701d4-104">' Type1 ' türünün değeri ' type2 ' olarak dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="701d4-104">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="701d4-105">' ' Öğesinin ilk öğesinin dize değerini almak için ' Value ' özelliğini kullanabilirsiniz \<parentElement> .</span><span class="sxs-lookup"><span data-stu-id="701d4-105">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>

 <span data-ttu-id="701d4-106">Bir XML sabit değerini örtük olarak belirli bir türe atama girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="701d4-106">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="701d4-107">XML sabit değeri örtük olarak belirtilen türe atanamaz.</span><span class="sxs-lookup"><span data-stu-id="701d4-107">The XML literal cannot be implicitly cast to the specified type.</span></span>

 <span data-ttu-id="701d4-108">**Hata kimliği:** BC31194</span><span class="sxs-lookup"><span data-stu-id="701d4-108">**Error ID:** BC31194</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="701d4-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="701d4-109">To correct this error</span></span>

- <span data-ttu-id="701d4-110">`Value`Değeri olarak başvurmak IÇIN XML sabit değerinin özelliğini kullanın `String` .</span><span class="sxs-lookup"><span data-stu-id="701d4-110">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="701d4-111">`CType` <xref:System.Convert> Değeri belirtilen tür olarak atamak için işlevi, başka bir tür dönüştürme işlevini veya sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="701d4-111">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>

## <a name="see-also"></a><span data-ttu-id="701d4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="701d4-112">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="701d4-113">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="701d4-113">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="701d4-114">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="701d4-114">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="701d4-115">XML</span><span class="sxs-lookup"><span data-stu-id="701d4-115">XML</span></span>](../../programming-guide/language-features/xml/index.md)
