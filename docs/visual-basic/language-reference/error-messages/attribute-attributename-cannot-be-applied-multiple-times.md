---
title: "Öznitelik &#39; &lt;attributename&gt;&#39; birden çok kez uygulanamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Öznitelik &#39; &lt;attributename&gt;&#39; birden çok kez uygulanamaz
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
 [Özel öznitelikler oluşturma](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
