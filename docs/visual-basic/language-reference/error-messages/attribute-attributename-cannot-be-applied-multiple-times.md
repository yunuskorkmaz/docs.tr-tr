---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968234"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>'\<AttributeName > ' özniteliği birden çok kez uygulanamaz

Özniteliği yalnızca bir kez uygulanabilir. `AttributeUsage` özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.  
  
 **Hata kimliği:** BC30663  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özniteliğin yalnızca bir kez uygulandığından emin olun.  
  
2. Geliştirdiğiniz özel öznitelikler kullanıyorsanız, aşağıdaki örnekte olduğu gibi, `AttributeUsage` özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AttributeUsageAttribute>
- [Özel Öznitelikler Oluşturma](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
