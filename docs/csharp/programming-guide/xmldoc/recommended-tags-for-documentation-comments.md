---
title: Dokümantasyon yorumları için önerilen etiketler - C# programlama kılavuzu
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789721"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Dokümantasyon yorumları için önerilen etiketler (C# programlama kılavuzu)

C# derleyicisi, **/doc** komut satırı seçeneğinde adını belirttiğiniz bir dosyada belgeleri kodunuzdaki belgeleri işler ve XML olarak biçimlendirin. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

Etiketler, tür ve tür üyeleri gibi kod yapılarında işlenir.

> [!NOTE]
> Belge açıklamaları bir ad alanına uygulanamaz.  
  
 Derleyici, geçerli olan herhangi bir etiketi XML'i işler. Aşağıdaki etiketler, kullanıcı belgelerinde genel olarak kullanılan işlevselliği sağlar.  
  
## <a name="tags"></a>Etiketler  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<bkz.>](./see.md)*|[\<değer>](./value.md)  
|[\<kod>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<örnek>](./example.md)|[\<paramref>](./paramref.md)|[\<özet>](./summary.md)|  
|[\<özel durum>](./exception.md)*|[\<izin>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<>dahil](./include.md)*|[\<açıklamalar>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<liste>](./list.md)|[\<kalıtsal doc>](./inheritdoc.md)|[\<>döndürür](./returns.md)|
  
(\* derleyicinin sözdizimini doğruladığını gösterir.)

Bir belge açıklama metninde açı braketlerinin görünmesini istiyorsanız, html `<` kodlamasını `&lt;` ve `&gt;` `>` sırasıyla ve sırasıyla kullanın. Bu kodlama aşağıdaki örnekte gösterilmiştir.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [-doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belgeleri yorumları](./index.md)
