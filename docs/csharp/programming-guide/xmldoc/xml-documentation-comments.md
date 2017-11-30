---
title: "XML Belgeleri Yorumları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7f88a85dd493836a17a80310ab4bce8ebf47c23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="f39b2-102">XML Belgeleri Yorumları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f39b2-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="f39b2-103">Visual C#'de, kaynak kodda doğrudan açıklamaların başvurduğu kod bloğunun hemen öncesindeki özel açıklama alanlarına (üç eğik çizgiyle gösterilir) XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="f39b2-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 <span data-ttu-id="f39b2-104">İle derleme zaman [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) seçeneği, derleyicinin tüm XML etiketleri kaynak kodu ve XML belge dosyası oluşturma için arayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f39b2-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="f39b2-105">Derleyicinin ürettiği dosyasını temel alarak son belgeleri oluşturmak için özel bir araç oluşturabilir veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="f39b2-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="f39b2-106">XML öğeleri (bir XML belgeleri açıklamada tanımlamak istediğiniz gibi işlev işlemleri belirli XML öğeleri) başvurmak için mekanizması tırnak içine almak standart kullanabilirsiniz (`<` ve `>`).</span><span class="sxs-lookup"><span data-stu-id="f39b2-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="f39b2-107">Kod başvurusu genel tanımlayıcıları başvurmak için (`cref`) öğeleri kaçış karakterleri kullanabilirsiniz (örneğin, `cref="List<T>"`) ya da küme ayraçları (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="f39b2-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List<T>"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="f39b2-108">Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="f39b2-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f39b2-109">XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="f39b2-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f39b2-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f39b2-110">In This Section</span></span>  
  
-   [<span data-ttu-id="f39b2-111">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="f39b2-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="f39b2-112">XML dosyasını işleme</span><span class="sxs-lookup"><span data-stu-id="f39b2-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="f39b2-113">Belge etiketleri için sınırlayıcılar</span><span class="sxs-lookup"><span data-stu-id="f39b2-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="f39b2-114">Nasıl yapılır: XML belgeleri özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="f39b2-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="f39b2-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f39b2-115">Related Sections</span></span>  
 <span data-ttu-id="f39b2-116">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f39b2-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f39b2-117">/ doc (işlem belgesi açıklamaları)</span><span class="sxs-lookup"><span data-stu-id="f39b2-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f39b2-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f39b2-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f39b2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f39b2-119">See Also</span></span>  
 [<span data-ttu-id="f39b2-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f39b2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
