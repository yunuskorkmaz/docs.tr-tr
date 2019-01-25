---
title: Başvurulamaz &#39; &lt;adı&gt; &#39; değer alanının bir üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfın &#39; &lt;classname&gt; &#39;olduğu &#39;System.MarshalByRefObject&#39; bir temel sınıf olarak
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739303"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Başvurulamaz &#39; &lt;adı&gt; &#39; değer alanının bir üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfın &#39; &lt;classname&gt; &#39;olduğu &#39;System.MarshalByRefObject&#39; bir temel sınıf olarak
`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırları uzak nesnelere erişimi destekleyen uygulamalar sağlar. Türleri devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında. Bir nesnenin üyelerine oluşturulmuş olan uygulama etki alanı dışında kullanılabilir olmadığı için nesne durumunu kopyalanmayacak.  
  
 **Hata Kimliği:** BC30310  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurulan üyenin geçerli olduğundan emin olmak için başvuru denetleyin.  
  
2.  Açıkça üyesiyle uygun `Me` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.MarshalByRefObject>
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
