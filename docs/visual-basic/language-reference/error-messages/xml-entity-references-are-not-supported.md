---
title: XML varlık başvuruları desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 37e72dbd6de61a50b4192a0151db40cb4be49d1c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163278"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a>BC31180: XML varlık başvuruları desteklenmiyor

XML 1,0 belirtiminde tanımlanmayan bir varlık başvurusu (örneğin, `©` ), BIR XML sabit değeri için değer olarak eklenmiştir. `&`XML değişmez değerlerinde yalnızca,,, `"` `<` `>` ve `'` XML varlık başvuruları desteklenir.

 **Hata kimliği:** BC31180

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Desteklenmeyen varlık başvurusunu kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Değişmez Değerleri ve XML 1.0 Belirtimi](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
