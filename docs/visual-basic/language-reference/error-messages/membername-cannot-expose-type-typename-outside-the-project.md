---
title: '&#39;&lt;membername&gt; &#39; türünü gösteremez &#39; &lt;typename&gt; &#39; üzerinden proje dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt; &#39; türünü gösteremez &#39; &lt;typename&gt; &#39; üzerinden proje dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
Değişken, yordam parametresini veya işlev dönüş kapsayıcısı dışında gösterilir, ancak kapsayıcı dışında gösterilmeyen gerekir bir türü olarak bildirilmiş.  
  
 Aşağıdaki iskelet kod bu hatayı oluşturan bir durumu gösterir.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Bildirilmiş bir türü `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır. Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amaçla boşa. Önceki iskelet kodda, `exposedVar` olan `Public` ve kullanılabilmesini `privateClass` erişimi olmaması gereken kodu.  
  
 **Hata Kimliği:** BC30909  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değiştirme değişkeni, yordam parametresini ya da işlevin erişim düzeyi en az olabildiğince kısıtlayıcı, veri türü erişim düzeyi dönün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
