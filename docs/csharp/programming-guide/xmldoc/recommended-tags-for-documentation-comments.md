---
title: Belge açıklamaları için - önerilen etiketler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: fb4d8d4dde38d7cbe1b0434c290dd922b2e328a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245593"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)
C# Derleyici, kodunuzda belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyasında XML olarak biçimlendirir **/doc** komut satırı seçeneği. Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Etiketler, kod yapıları türleri gibi işlenir ve tür üyelerini.  
  
> [!NOTE]
>  Belge açıklamaları için bir ad alanı uygulanamaz.  
  
 Derleyici, geçerli bir XML değil herhangi bir etiket işleyecektir. Aşağıdaki kullanıcı belgeleri, genel olarak kullanılan işlevler sunar.  
  
## <a name="tags"></a>Etiketler  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<kod >](../../../csharp/programming-guide/xmldoc/code.md)|[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<Örnek >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<Summary >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<Ekle >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<REMARKS >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<listesi >](../../../csharp/programming-guide/xmldoc/list.md)|[\<döndürür >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<Değer >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* derleyici sözdizimini doğrular gösterir.)  
  
 Açılı belgeleri açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
