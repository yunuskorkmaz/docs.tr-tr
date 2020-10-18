---
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 107936aa969690d0cc9fd4a2605cfceea31eeca8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161419"
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
