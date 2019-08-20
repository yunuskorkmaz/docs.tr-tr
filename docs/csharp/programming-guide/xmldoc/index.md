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
ms.openlocfilehash: 46dd947ac6ff5a45c7d952acaa55e25c3a46969c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588051"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="dd7a3-102">XML Belgeleri Yorumları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dd7a3-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="dd7a3-103">Visual C#'de, kaynak kodda doğrudan açıklamaların başvurduğu kod bloğunun hemen öncesindeki özel açıklama alanlarına (üç eğik çizgiyle gösterilir) XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="dd7a3-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="dd7a3-104">[/Doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-104">When you compile with the [/doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="dd7a3-105">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="dd7a3-106">XML öğelerine başvurmak için (örneğin, işleviniz bir XML belge açıklamasında açıklama eklemek istediğiniz belirli XML öğelerini işler), standart tırnak işareti mekanizmasını (`<` ve `>`) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="dd7a3-107">Kod başvurusu (`cref`) öğelerinde genel tanımlayıcılara başvurmak için, kaçış karakterlerini (örneğin, `cref="List&lt;T&gt;"`) veya küme ayracı (`cref="List{T}"`) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="dd7a3-108">Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd7a3-109">XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd7a3-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dd7a3-110">In This Section</span></span>  
  
- [<span data-ttu-id="dd7a3-111">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="dd7a3-111">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)  
  
- [<span data-ttu-id="dd7a3-112">XML Dosyasını İşleme</span><span class="sxs-lookup"><span data-stu-id="dd7a3-112">Processing the XML File</span></span>](./processing-the-xml-file.md)  
  
- [<span data-ttu-id="dd7a3-113">Belge Etiketleri için Sınırlayıcılar</span><span class="sxs-lookup"><span data-stu-id="dd7a3-113">Delimiters for Documentation Tags</span></span>](./delimiters-for-documentation-tags.md)  
  
- [<span data-ttu-id="dd7a3-114">Nasıl yapılır: XML belgesi özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="dd7a3-114">How to: Use the XML Documentation Features</span></span>](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="dd7a3-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dd7a3-115">Related Sections</span></span>  
 <span data-ttu-id="dd7a3-116">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="dd7a3-116">For more information, see:</span></span>  
  
- [<span data-ttu-id="dd7a3-117">/Doc (Işlem belgeleri açıklamaları)</span><span class="sxs-lookup"><span data-stu-id="dd7a3-117">/doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="dd7a3-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="dd7a3-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd7a3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-119">See also</span></span>

- [<span data-ttu-id="dd7a3-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dd7a3-120">C# Programming Guide</span></span>](../index.md)
