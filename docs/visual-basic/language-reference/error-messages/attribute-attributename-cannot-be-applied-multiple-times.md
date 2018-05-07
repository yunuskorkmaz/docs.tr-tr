---
title: Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
Öznitelik yalnızca bir kez uygulanabilir. `AttributeUsage` Özniteliği, özniteliğin birden çok kez uygulanabilir olup olmadığını belirler.  
  
 **Hata Kimliği:** BC30663  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Öznitelik yalnızca bir kez uygulanır emin olun.  
  
2.  Özel öznitelikler, geliştirilmiş kullanıyorsanız, değiştirmeyi göz önünde bulundurun kendi `AttributeUsage` özniteliği birden çok öznitelik kullanımı, aşağıdaki örnek olarak izin vermek için.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AttributeUsageAttribute>  
 [Özel Öznitelikler Oluşturma](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
