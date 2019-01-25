---
title: Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 6609ce299799bc3c4b78d48478e99e4d4101dd72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565169"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
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
