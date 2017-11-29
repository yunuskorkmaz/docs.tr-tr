---
title: "&#39; &lt;membername&gt;&#39; türündeki &#39; gösteremez&lt; TypeName&gt;&#39; üzerinden proje dışına &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords: BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39; &lt;membername&gt;&#39; türündeki &#39; gösteremez&lt; TypeName&gt;&#39; üzerinden proje dışına &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;
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
