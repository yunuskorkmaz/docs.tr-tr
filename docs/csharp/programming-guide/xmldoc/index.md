---
title: XML belge açıklamaları-C# Programlama Kılavuzu
description: XML belge açıklamaları hakkında bilgi edinin. Özel Açıklama alanlarına XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz.
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
ms.openlocfilehash: fbdeb53331d9fc63d24a3322ea13863d7c0a3630
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381885"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML belgeleri Yorumları (C# Programlama Kılavuzu)

C# ' de, örneğin, yorumların başvurduğu kod bloğundan hemen önce, kaynak kodundaki özel Açıklama alanlarına (üç eğik çizgi ile gösterilir) XML öğeleri ekleyerek kodunuz için belge oluşturabilirsiniz.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

[-Doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

XML öğelerine başvurmak için (örneğin, işleviniz bir XML belge açıklamasında açıklama eklemek istediğiniz belirli XML öğelerini işler), standart tırnak işareti mekanizmasını ( `<` ve `>` ) kullanabilirsiniz.  Kod başvurusu () öğelerinde genel tanımlayıcılara başvurmak için `cref` , kaçış karakterlerini (örneğin, `cref="List&lt;T&gt;"` ) veya küme ayracı ( `cref="List{T}"` ) kullanabilirsiniz.  Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.

> [!NOTE]
> XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.

## <a name="in-this-section"></a>Bu bölümde

- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)

- [XML dosyasını işleme](./processing-the-xml-file.md)

- [Belge etiketleri için sınırlayıcılar](./delimiters-for-documentation-tags.md)

- [XML belge özelliklerini kullanma](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [-Doc (Işlem belgeleri açıklamaları)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
