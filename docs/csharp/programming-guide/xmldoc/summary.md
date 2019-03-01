---
title: <summary> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 12898d5cd10d9ecca4ec0fd1f7d06be0761b57b8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978559"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="878b6-102">\<Özet > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="878b6-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="878b6-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="878b6-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="878b6-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="878b6-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="878b6-105">Nesne bir özeti.</span><span class="sxs-lookup"><span data-stu-id="878b6-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="878b6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="878b6-106">Remarks</span></span>  
 <span data-ttu-id="878b6-107">\<Özet > etiketi, bir tür veya tür üye tanımlamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="878b6-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="878b6-108">Kullanım [ \<remarks >](../../../csharp/programming-guide/xmldoc/remarks.md) ek bilgiler bir tür tanımı eklemek için.</span><span class="sxs-lookup"><span data-stu-id="878b6-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="878b6-109">Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) belgeleri araçları gibi etkinleştirmek üzere [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) iç kod öğeleri için belge sayfalarına köprüler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="878b6-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="878b6-110">Metni \<Özet > etiketi yalnızca kaynak ıntellisense'te tür hakkında bilgilerin ve bir nesne tarayıcı penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="878b6-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="878b6-111">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="878b6-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="878b6-112">Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="878b6-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="878b6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="878b6-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="878b6-114">Önceki örnekte, aşağıdaki XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="878b6-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="878b6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="878b6-115">Example</span></span>  
 <span data-ttu-id="878b6-116">Aşağıdaki örnek nasıl yapılacağını gösteren bir `cref` genel bir tür referansı.</span><span class="sxs-lookup"><span data-stu-id="878b6-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="878b6-117">Önceki örnekte, aşağıdaki XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="878b6-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="878b6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="878b6-118">See also</span></span>

- [<span data-ttu-id="878b6-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="878b6-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="878b6-120">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="878b6-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
