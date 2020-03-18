---
title: <summary> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789667"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="46deb-102">\<özet> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="46deb-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="46deb-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46deb-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="46deb-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46deb-104">Parameters</span></span>

- `description`

  <span data-ttu-id="46deb-105">Nesnenin bir özeti.</span><span class="sxs-lookup"><span data-stu-id="46deb-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="46deb-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46deb-106">Remarks</span></span>

<span data-ttu-id="46deb-107">Özet \<> etiketi, bir türü veya bir tür üyesini tanımlamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46deb-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="46deb-108">Tür açıklamasına ek bilgi eklemek için [ \<açıklamaları>](./remarks.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="46deb-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="46deb-109">Kod öğeleri için dokümantasyon sayfalarına dahili köprüler oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi dokümantasyon araçlarını etkinleştirmek için [cref Attribute'ı](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="46deb-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="46deb-110">Özet> \<etiketinin metni IntelliSense'deki tür le ilgili tek bilgi kaynağıdır ve Nesne Tarayıcı Penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="46deb-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="46deb-111">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="46deb-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="46deb-112">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46deb-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="46deb-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="46deb-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="46deb-114">Önceki örnek, aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="46deb-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="46deb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="46deb-115">Example</span></span>

<span data-ttu-id="46deb-116">Aşağıdaki örnek, genel bir `cref` türe nasıl başvuru yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46deb-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="46deb-117">Önceki örnek, aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="46deb-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="46deb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46deb-118">See also</span></span>

- [<span data-ttu-id="46deb-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46deb-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="46deb-120">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="46deb-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
