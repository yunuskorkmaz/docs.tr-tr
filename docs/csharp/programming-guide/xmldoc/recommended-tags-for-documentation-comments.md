---
title: Belge açıklamaları için önerilen Etiketler-C# Programlama Kılavuzu
description: Belge açıklamaları için önerilen Etiketler hakkında bilgi edinin. Önerilen etiketlerin listesini görün ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 74fd18a09458c399aa135552e5f6f0bca359f09e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477838"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)

C# derleyicisi kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı seçeneğinde belirttiğiniz BIR dosyada xml olarak biçimlendirir. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.

> [!NOTE]
> Belge açıklamaları bir ad alanına uygulanamaz.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işleyecek. Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.  
  
## <a name="tags"></a>Etiketler  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
( \* derleyicinin söz dizimini doğruladığını gösterir.)

Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, ve sırasıyla ve olan HTML kodlamasını kullanın `<` `>` `&lt;` `&gt;` . Bu kodlama aşağıdaki örnekte gösterilmiştir.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [**Belgetationfile** (C# derleyici seçenekleri)](../../language-reference/compiler-options/output.md#documentationfile)
- [XML belgeleri yorumları](./index.md)
