---
title: <summary> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <summary> bir türü veya tür üyesini anlatmak için kullanılan etiket. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: f9243e598aaf0c12dd48b48045f461b4b307c18f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380611"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="1a40b-105">\<summary>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1a40b-105">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a40b-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1a40b-106">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="1a40b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a40b-107">Parameters</span></span>

- `description`

  <span data-ttu-id="1a40b-108">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="1a40b-108">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a40b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a40b-109">Remarks</span></span>

<span data-ttu-id="1a40b-110">`<summary>`Etiket bir tür veya tür üyesini tanımlamakta kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a40b-110">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="1a40b-111">[\<remarks>](./remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a40b-111">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="1a40b-112">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçlarını etkinleştirmek için [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a40b-112">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="1a40b-113">Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1a40b-113">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="1a40b-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="1a40b-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="1a40b-115">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a40b-115">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="1a40b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a40b-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="1a40b-117">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="1a40b-117">The previous example produces the following XML file.</span></span>

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
            </summary>
            <seealso cref="M:TestClass.Main"/>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="1a40b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a40b-118">Example</span></span>

<span data-ttu-id="1a40b-119">Aşağıdaki örnek, genel bir türe nasıl başvuru yapılacağını gösterir `cref` .</span><span class="sxs-lookup"><span data-stu-id="1a40b-119">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="1a40b-120">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="1a40b-120">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1a40b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a40b-121">See also</span></span>

- [<span data-ttu-id="1a40b-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1a40b-122">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1a40b-123">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="1a40b-123">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
