---
title: XML belge açıklamaları- C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 6405b094ccc50499bfeb4db4522f0ec9b01f68ad
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523489"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML Belgeleri Yorumları (C# Programlama Kılavuzu)
Visual C#'de, kaynak kodda doğrudan açıklamaların başvurduğu kod bloğunun hemen öncesindeki özel açıklama alanlarına (üç eğik çizgiyle gösterilir) XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz, örneğin:  
  
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
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)  
  
- [XML Dosyasını İşleme](./processing-the-xml-file.md)  
  
- [Belge Etiketleri için Sınırlayıcılar](./delimiters-for-documentation-tags.md)  
  
- [Nasıl yapılır: XML Belgesi Özelliklerini Kullanma](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
- [-Doc (Işlem belgeleri açıklamaları)](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
