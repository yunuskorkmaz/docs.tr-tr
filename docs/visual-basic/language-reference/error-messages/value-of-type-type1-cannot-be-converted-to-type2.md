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
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a>BC31194: ' type1 ' türündeki değer ' type2 ' olarak dönüştürülemez

' Type1 ' türünün değeri ' type2 ' olarak dönüştürülemez. ' ' Öğesinin ilk öğesinin dize değerini almak için ' Value ' özelliğini kullanabilirsiniz \<parentElement> .

 Bir XML sabit değerini örtük olarak belirli bir türe atama girişiminde bulunuldu. XML sabit değeri örtük olarak belirtilen türe atanamaz.

 **Hata kimliği:** BC31194

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Value`Değeri olarak başvurmak IÇIN XML sabit değerinin özelliğini kullanın `String` . `CType` <xref:System.Convert> Değeri belirtilen tür olarak atamak için işlevi, başka bir tür dönüştürme işlevini veya sınıfını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert>
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
