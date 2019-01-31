---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 62e84d174e4e218472eda9b7c08ed677e0140438
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278713"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Öznitelik '\<attributename >' birden çok kez uygulanamaz
Öznitelik yalnızca bir kez uygulanabilir. `AttributeUsage` Özniteliği bir öznitelik birden çok kez uygulanabilir olup olmadığını belirler.  
  
 **Hata Kimliği:** BC30663  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Öznitelik yalnızca bir kez uygulanır emin olun.  
  
2.  Geliştirdiğiniz özel öznitelikler kullanıyorsanız, değiştirmeyi göz önünde bulundurun, `AttributeUsage` birden çok öznitelik kullanımı, aşağıdaki örnek olarak izin vermek için özniteliği.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.AttributeUsageAttribute>
- [Özel Öznitelikler Oluşturma](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
