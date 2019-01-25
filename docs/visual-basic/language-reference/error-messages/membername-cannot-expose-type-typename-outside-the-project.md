---
title: '&#39;&lt;membername&gt; &#39; türü gösteremez &#39; &lt;typename&gt; &#39; aracılığıyla projenin dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672350"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt; &#39; türü gösteremez &#39; &lt;typename&gt; &#39; aracılığıyla projenin dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
Bir değişken, yordam parametre veya dönüş işlevi kapsayıcısı dışında sunulur, ancak kapsayıcı dışında açılmamalıdır bir türü olarak bildirilmiş.  
  
 Aşağıdaki çatı kod bu hatayı oluşturan durumu gösterir.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Bildirilen tür `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır. Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amacını boşa. Önceki iskelet kodda `exposedVar` olduğu `Public` ve kullanılabilmesini `privateClass` , erişimi olmaması gereken kod için.  
  
 **Hata Kimliği:** BC30909  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değişken, yordam parametresi veya işlev erişim düzeyini değiştir en az olabildiğince kısıtlayıcı kendi veri türüne erişim düzeyini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
