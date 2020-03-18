---
title: XML dokümantasyon yorumları - C# programlama kılavuzu
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76789789"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML dokümantasyon yorumları (C# programlama kılavuzu)

C#'da, örneğin yorumların atıfta bulunduğu kod bloğundan hemen önce kaynak koduna özel yorum alanlarına XML öğelerini (üçlü kesikler ile gösterilir) ekleyerek kodunuz için belgeler oluşturabilirsiniz.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

[-doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlediğinizde, derleyici kaynak koddaki tüm XML etiketlerini arar ve bir XML dokümandosyası oluşturur. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

XML öğelerine başvurmak için (örneğin, işleviniz bir XML dokümantasyon yorumunda açıklamak istediğiniz belirli XML`<` öğelerini işler), standart teklif mekanizmasını (ve) `>`kullanabilirsiniz.  Kod başvurusu (`cref`) öğelerindeki genel tanımlayıcılara başvurmak için kaçış karakterlerini (örneğin) `cref="List&lt;T&gt;"`veya ayraçları`cref="List{T}"`().  Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.

> [!NOTE]
> XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.

## <a name="in-this-section"></a>Bu bölümde

- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)

- [XML dosyasını işleme](./processing-the-xml-file.md)

- [Belge etiketleri için sınırlayıcılar](./delimiters-for-documentation-tags.md)

- [XML belge özelliklerini kullanma](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [-doc (Süreç Dokümantasyonu Yorumları)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
