---
title: Belge açıklamaları için - önerilen etiketler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 07594d70b92e2075c3d5aba605eab23d766faed6
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052743"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)
C# Derleyici, kodunuzda belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyasında XML olarak biçimlendirir **/doc** komut satırı seçeneği. Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Etiketler, kod yapıları türleri gibi işlenir ve tür üyelerini.  
  
> [!NOTE]
>  Belge açıklamaları için bir ad alanı uygulanamaz.  
  
 Derleyici, geçerli bir XML değil herhangi bir etiket işleyecektir. Aşağıdaki kullanıcı belgeleri, genel olarak kullanılan işlevler sunar.  
  
## <a name="tags"></a>Etiketler  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<kod >](../../../csharp/programming-guide/xmldoc/code.md)|[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<Örnek >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<Ekle >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<REMARKS >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<listesi >](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* derleyici sözdizimini doğrular gösterir.)  
  
 Açılı belgeleri açıklama metninde görünmesini istiyorsanız ait HTML kodlamasını kullanın `<` ve `>` olduğu `&lt;` ve `&gt;` sırasıyla. Bu kodlama, aşağıdaki örnekte gösterilmiştir:
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/index.md)
