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
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="0d627-102">XML belge açıklamaları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0d627-102">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="0d627-103">' C#De, örneğin, yorumların başvurduğu kod bloğundan hemen önce, kaynak kodundaki özel Açıklama alanlarına (üç eğik çizgi ile GÖSTERILIR) XML öğeleri ekleyerek kodunuz için belgeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d627-103">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="0d627-104">[-Doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d627-104">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="0d627-105">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d627-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="0d627-106">XML öğelerine başvurmak için (örneğin, işleviniz, bir XML belge açıklamasında açıklama eklemek istediğiniz belirli XML öğelerini işliyorsa), standart tırnak içine alma mekanizmasını (`<` ve `>`) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d627-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="0d627-107">Kod başvurusu (`cref`) öğelerinde genel tanımlayıcılara başvurmak için, kaçış karakterlerini (örneğin, `cref="List&lt;T&gt;"`) veya küme ayraçlarını (`cref="List{T}"`) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d627-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="0d627-108">Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="0d627-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="0d627-109">XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="0d627-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0d627-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="0d627-110">In this section</span></span>

- [<span data-ttu-id="0d627-111">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="0d627-111">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="0d627-112">XML dosyası işleniyor</span><span class="sxs-lookup"><span data-stu-id="0d627-112">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="0d627-113">Belge etiketleri için sınırlayıcılar</span><span class="sxs-lookup"><span data-stu-id="0d627-113">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="0d627-114">XML belgeleri özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0d627-114">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="0d627-115">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="0d627-115">Related sections</span></span>

<span data-ttu-id="0d627-116">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="0d627-116">For more information, see:</span></span>

- [<span data-ttu-id="0d627-117">-Doc (Işlem belgeleri açıklamaları)</span><span class="sxs-lookup"><span data-stu-id="0d627-117">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="0d627-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0d627-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0d627-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d627-119">See also</span></span>

- [<span data-ttu-id="0d627-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0d627-120">C# Programming Guide</span></span>](../index.md)
