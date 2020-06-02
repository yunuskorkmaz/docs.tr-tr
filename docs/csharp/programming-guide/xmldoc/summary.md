---
title: <summary> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: e1a8c9d61e61eae7ba6bf7f0c1b9d2a8dc8a4171
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287213"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="6959e-102">\<summary>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6959e-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6959e-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6959e-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="6959e-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6959e-104">Parameters</span></span>

- `description`

  <span data-ttu-id="6959e-105">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="6959e-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="6959e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6959e-106">Remarks</span></span>

<span data-ttu-id="6959e-107">`<summary>`Etiket bir tür veya tür üyesini tanımlamakta kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6959e-107">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="6959e-108">[\<remarks>](./remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6959e-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="6959e-109">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçlarını etkinleştirmek için [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6959e-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="6959e-110">Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6959e-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="6959e-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6959e-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="6959e-112">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6959e-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="6959e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6959e-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="6959e-114">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="6959e-114">The previous example produces the following XML file.</span></span>

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

## <a name="example"></a><span data-ttu-id="6959e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6959e-115">Example</span></span>

<span data-ttu-id="6959e-116">Aşağıdaki örnek, genel bir türe nasıl başvuru yapılacağını gösterir `cref` .</span><span class="sxs-lookup"><span data-stu-id="6959e-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="6959e-117">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="6959e-117">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6959e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6959e-118">See also</span></span>

- [<span data-ttu-id="6959e-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6959e-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6959e-120">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="6959e-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
