---
title: XML belge açıklamaları- C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789789"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML belge açıklamaları (C# Programlama Kılavuzu)

' C#De, örneğin, yorumların başvurduğu kod bloğundan hemen önce, kaynak kodundaki özel Açıklama alanlarına (üç eğik çizgi ile GÖSTERILIR) XML öğeleri ekleyerek kodunuz için belgeler oluşturabilirsiniz.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

[-Doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

XML öğelerine başvurmak için (örneğin, işleviniz, bir XML belge açıklamasında açıklama eklemek istediğiniz belirli XML öğelerini işliyorsa), standart tırnak içine alma mekanizmasını (`<` ve `>`) kullanabilirsiniz.  Kod başvurusu (`cref`) öğelerinde genel tanımlayıcılara başvurmak için, kaçış karakterlerini (örneğin, `cref="List&lt;T&gt;"`) veya küme ayraçlarını (`cref="List{T}"`) kullanabilirsiniz.  Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.

> [!NOTE]
> XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.

## <a name="in-this-section"></a>Bu bölümde

- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)

- [XML dosyası işleniyor](./processing-the-xml-file.md)

- [Belge etiketleri için sınırlayıcılar](./delimiters-for-documentation-tags.md)

- [XML belgeleri özelliklerini kullanma](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [-Doc (Işlem belgeleri açıklamaları)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
