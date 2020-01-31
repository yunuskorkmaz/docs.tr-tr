---
title: Belge açıklamaları için önerilen Etiketler- C# Programlama Kılavuzu
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789721"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)

C# Derleyici kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı SEÇENEĞINDE belirttiğiniz bir dosyada xml olarak biçimlendirir. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.

> [!NOTE]
> Belge açıklamaları bir ad alanına uygulanamaz.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işleyecek. Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.  
  
## <a name="tags"></a>Etiketler  
  
|||||  
|---|---|---|---|
|[\<c >](./code-inline.md)|[\<paragraf >](./para.md)|[\<bkz. >](./see.md)*|[\<value>](./value.md)  
|[\<kodu >](./code.md)|[\<param >](./param.md)*|[\<seede >](./seealso.md)*|  
|[\<örnek >](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<özel durum >](./exception.md)*|[\<izin >](./permission.md)*|[\<typeparam >](./typeparam.md)*|  
|[\<> ekleme](./include.md)*|[\<açıklamalar >](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<listesi >](./list.md)|[\<devralma belgesi >](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* derleyicinin söz dizimini doğruladığını gösterir.)

Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `<` ve `>` HTML kodlamasını kullanın `&lt;` ve `&gt;`. Bu kodlama aşağıdaki örnekte gösterilmiştir.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belge açıklamaları](./index.md)
