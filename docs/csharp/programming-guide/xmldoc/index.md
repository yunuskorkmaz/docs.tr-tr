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
ms.openlocfilehash: d784ec58096e44cf010edd279f682555df58a8ef
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478391"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML belgeleri Yorumları (C# Programlama Kılavuzu)

C# ' de, örneğin, yorumların başvurduğu kod bloğundan hemen önce, kaynak kodundaki özel Açıklama alanlarına (üç eğik çizgi ile gösterilir) XML öğeleri ekleyerek kodunuz için belge oluşturabilirsiniz.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Belgelerce [**Tationfile**](../../language-reference/compiler-options/output.md#documentationfile) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

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

- [**Belgetationfile** (Işlem belgeleri açıklamaları)](../../language-reference/compiler-options/output.md#documentationfile)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
