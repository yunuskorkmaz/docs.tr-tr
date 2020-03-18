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
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="37f0d-102">XML dokümantasyon yorumları (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37f0d-102">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="37f0d-103">C#'da, örneğin yorumların atıfta bulunduğu kod bloğundan hemen önce kaynak koduna özel yorum alanlarına XML öğelerini (üçlü kesikler ile gösterilir) ekleyerek kodunuz için belgeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37f0d-103">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="37f0d-104">[-doc](../../language-reference/compiler-options/doc-compiler-option.md) seçeneğiyle derlediğinizde, derleyici kaynak koddaki tüm XML etiketlerini arar ve bir XML dokümandosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37f0d-104">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="37f0d-105">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37f0d-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="37f0d-106">XML öğelerine başvurmak için (örneğin, işleviniz bir XML dokümantasyon yorumunda açıklamak istediğiniz belirli XML`<` öğelerini işler), standart teklif mekanizmasını (ve) `>`kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37f0d-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="37f0d-107">Kod başvurusu (`cref`) öğelerindeki genel tanımlayıcılara başvurmak için kaçış karakterlerini (örneğin) `cref="List&lt;T&gt;"`veya ayraçları`cref="List{T}"`().</span><span class="sxs-lookup"><span data-stu-id="37f0d-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="37f0d-108">Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="37f0d-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="37f0d-109">XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="37f0d-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="37f0d-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="37f0d-110">In this section</span></span>

- [<span data-ttu-id="37f0d-111">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="37f0d-111">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="37f0d-112">XML dosyasını işleme</span><span class="sxs-lookup"><span data-stu-id="37f0d-112">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="37f0d-113">Belge etiketleri için sınırlayıcılar</span><span class="sxs-lookup"><span data-stu-id="37f0d-113">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="37f0d-114">XML belge özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="37f0d-114">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="37f0d-115">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="37f0d-115">Related sections</span></span>

<span data-ttu-id="37f0d-116">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="37f0d-116">For more information, see:</span></span>

- [<span data-ttu-id="37f0d-117">-doc (Süreç Dokümantasyonu Yorumları)</span><span class="sxs-lookup"><span data-stu-id="37f0d-117">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="37f0d-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="37f0d-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="37f0d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37f0d-119">See also</span></span>

- [<span data-ttu-id="37f0d-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="37f0d-120">C# Programming Guide</span></span>](../index.md)
