---
title: "Başvuramıyor &#39; &lt;adı&gt;&#39; &#39; değer yazdınız alan üyesi olduğundan&lt; ad&gt;&#39; sınıfı &#39;&lt; ClassName&gt;&#39; olan &#39; System.MarshalByRefObject &#39; bir temel sınıf olarak"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords: BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Başvuramıyor &#39; &lt;adı&gt;&#39; &#39; değer yazdınız alan üyesi olduğundan&lt; ad&gt;&#39; sınıfı &#39;&lt; ClassName&gt;&#39; olan &#39; System.MarshalByRefObject &#39; bir temel sınıf olarak
`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırlarında nesnelere uzaktan erişimi destekleyen uygulamalar sağlar. Türleri öğesinden devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında. Nesne üyeleri oluşturulmuş uygulama etki alanı kullanılabilir olmadığından nesnenin durumunu kopyalanmayacak.  
  
 **Hata Kimliği:** BC30310  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurulan üye geçerli olduğundan emin olmak için başvuru denetleyin.  
  
2.  Açıkça üyesiyle nitelemek `Me` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.MarshalByRefObject>  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
