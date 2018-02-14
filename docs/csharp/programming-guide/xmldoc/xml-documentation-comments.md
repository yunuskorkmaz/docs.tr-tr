---
title: "XML Belgeleri Yorumları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f8718096a7bce08b18a00ec04a5a8b0adb12bca
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2018
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML Belgeleri Yorumları (C# Programlama Kılavuzu)
Visual C#'de, kaynak kodda doğrudan açıklamaların başvurduğu kod bloğunun hemen öncesindeki özel açıklama alanlarına (üç eğik çizgiyle gösterilir) XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz, örneğin:  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 İle derleme zaman [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) seçeneği, derleyicinin tüm XML etiketleri kaynak kodu ve XML belge dosyası oluşturma için arayacaktır. Derleyicinin ürettiği dosyasını temel alarak son belgeleri oluşturmak için özel bir araç oluşturabilir veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 XML öğeleri (bir XML belgeleri açıklamada tanımlamak istediğiniz gibi işlev işlemleri belirli XML öğeleri) başvurmak için mekanizması tırnak içine almak standart kullanabilirsiniz (`<` ve `>`).  Kod başvurusu genel tanımlayıcıları başvurmak için (`cref`) öğeleri kaçış karakterleri kullanabilirsiniz (örneğin, `cref="List&lt;T&gt;"`) ya da küme ayraçları (`cref="List{T}"`).  Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.  
  
> [!NOTE]
>  XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [XML Dosyasını İşleme](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Belge Etiketleri için Sınırlayıcılar](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Nasıl yapılır: XML Belgesi Özelliklerini Kullanma](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [/ doc (işlem belgesi açıklamaları)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
