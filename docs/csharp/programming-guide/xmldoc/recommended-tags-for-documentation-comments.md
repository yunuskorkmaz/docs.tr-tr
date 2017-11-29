---
title: "Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d558bbe58d1f4a1c290b4f36718293d5ba1c734
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)
C# Derleyici, kodundaki belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyada XML olarak biçimlendirir **/doc** komut satırı seçeneği. Derleyicinin ürettiği dosyasını temel alarak son belgeleri oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Etiketleri kod yapıları türleri gibi işlenir ve üyeleri yazın.  
  
> [!NOTE]
>  Belge açıklamaları için bir ad alanı uygulanamaz.  
  
 Derleyici geçerli XML herhangi bir etiket işler. Aşağıdaki kullanıcı belgelerinde genellikle kullanılan işlevsellik sağlar.  
  
## <a name="tags"></a>Etiketler  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<kodu >](../../../csharp/programming-guide/xmldoc/code.md)|[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<Örnek >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<Özet >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<dahil >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<Açıklamalar >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<Liste >](../../../csharp/programming-guide/xmldoc/list.md)|[\<döndürür >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<Değer >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* derleyici sözdizimi doğrular gösterir.)  
  
 Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML belgeleri yorumları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
