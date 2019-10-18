---
title: Belge açıklamaları için önerilen Etiketler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: d17ff0b78d8ae40916447e8e12da7948a21e5717
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523360"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)
C# Derleyici kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı SEÇENEĞINDE belirttiğiniz bir dosyada xml olarak biçimlendirir. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.  
  
 Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.  
  
> [!NOTE]
> Belge açıklamaları bir ad alanına uygulanamaz.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işleyecek. Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.  
  
## <a name="tags"></a>Etiketler  
  
||||  
|---|---|---|  
|[\<c >](./code-inline.md)|[\<para >](./para.md)|[\<see >](./see.md) *|  
|[\<code >](./code.md)|[\<param >](./param.md) *|[\<seealso >](./seealso.md) *|  
|[\<example >](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception >](./exception.md) *|[\<permission >](./permission.md) *|[\<typeparam >](./typeparam.md) *|  
|[\<include >](./include.md) *|[\<remarks >](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list >](./list.md)|[\<returns>](./returns.md)|[\<value>](./value.md)|  
  
 (* derleyicinin söz dizimini doğruladığını gösterir.)  
  
 Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `<` ve `>` HTML kodlamasını kullanın `&lt;` ve `&gt;`. Bu kodlama aşağıdaki örnekte gösterilmiştir:
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](./index.md)
