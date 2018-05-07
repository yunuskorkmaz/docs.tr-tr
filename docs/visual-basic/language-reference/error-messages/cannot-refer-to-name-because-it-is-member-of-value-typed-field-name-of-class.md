---
title: Başvuramıyor &#39; &lt;adı&gt; &#39; değer yazdınız alanın üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfının &#39; &lt;classname&gt; &#39;olan &#39;System.MarshalByRefObject&#39; temel sınıf olarak
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Başvuramıyor &#39; &lt;adı&gt; &#39; değer yazdınız alanın üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfının &#39; &lt;classname&gt; &#39;olan &#39;System.MarshalByRefObject&#39; temel sınıf olarak
`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırlarında nesnelere uzaktan erişimi destekleyen uygulamalar sağlar. Türleri öğesinden devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında. Nesne üyeleri oluşturulmuş uygulama etki alanı kullanılabilir olmadığından nesnenin durumunu kopyalanmayacak.  
  
 **Hata Kimliği:** BC30310  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurulan üye geçerli olduğundan emin olmak için başvuru denetleyin.  
  
2.  Açıkça üyesiyle nitelemek `Me` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.MarshalByRefObject>  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
