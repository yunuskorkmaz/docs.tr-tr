---
title: <include> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 22d87559766c04e53141e843ee8768c8aab89a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156980"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="3007d-102">\<> (C# programlama kılavuzu) dahil</span><span class="sxs-lookup"><span data-stu-id="3007d-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3007d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3007d-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="3007d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3007d-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="3007d-105">Belgeleri içeren XML dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="3007d-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="3007d-106">Dosya adı, kaynak kod dosyasına göre bir yol ile nitelikli olabilir.</span><span class="sxs-lookup"><span data-stu-id="3007d-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="3007d-107">Tek `filename` tırnak işaretleri (' ') içine ala.</span><span class="sxs-lookup"><span data-stu-id="3007d-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="3007d-108">Etiketlerin etiketine `filename` yol açan `name`yolu.</span><span class="sxs-lookup"><span data-stu-id="3007d-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="3007d-109">Yolu tek tırnak işaretlerine (' ') içine ala.</span><span class="sxs-lookup"><span data-stu-id="3007d-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="3007d-110">Yorumlardan önce etikette ad belirtici; `name` bir `id`.</span><span class="sxs-lookup"><span data-stu-id="3007d-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="3007d-111">Yorumlardan önce etiketin kimliği.</span><span class="sxs-lookup"><span data-stu-id="3007d-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="3007d-112">Kimliği çift tırnak işaretlerine (" ") ekin.</span><span class="sxs-lookup"><span data-stu-id="3007d-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="3007d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3007d-113">Remarks</span></span>

<span data-ttu-id="3007d-114">Include \<> etiketi, kaynak kodunuzdaki türleri ve üyeleri açıklayan başka bir dosyadaki yorumlara başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3007d-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="3007d-115">Bu, belge yorumlarını doğrudan kaynak kod dosyanıza yerleştirmek için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="3007d-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="3007d-116">Belgeleri ayrı bir dosyaya koyarak, kaynak denetimi kaynak kodundan ayrı olarak belgelere uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3007d-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="3007d-117">Bir kişi kaynak kodu dosyasının kullanıma ait olması ve başka birinin belge dosyasının kullanıma ait olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="3007d-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="3007d-118">Include \<> etiketi XML XPath sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3007d-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="3007d-119">Dahil> kullanımınızı \<özelleştirmenin yolları için XPath belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="3007d-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>

## <a name="example"></a><span data-ttu-id="3007d-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="3007d-120">Example</span></span>

<span data-ttu-id="3007d-121">Bu çok dosyalı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="3007d-121">This is a multifile example.</span></span> <span data-ttu-id="3007d-122">Aşağıdaki,> içeren \<ilk dosyadır.</span><span class="sxs-lookup"><span data-stu-id="3007d-122">The following is the first file, which uses \<include>.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="3007d-123">İkinci dosya, *xml_include_tag.doc*, aşağıdaki dokümantasyon yorumlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3007d-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a><span data-ttu-id="3007d-124">Program çıktısı</span><span class="sxs-lookup"><span data-stu-id="3007d-124">Program output</span></span>

<span data-ttu-id="3007d-125">Aşağıdaki çıktı, Test ve Test2 sınıflarını aşağıdaki komut satırıyla `-doc:DocFileName.xml.` derlediğinizde oluşturulur: Visual Studio'da, Proje Tasarımcısı'nın Yapı bölmesinde XML doc yorum seçeneğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3007d-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="3007d-126">C# derleyicisi \<include> etiketini gördüğünde, geçerli kaynak dosyası yerine xml_include_tag.doc'da belge yorumlarını arar.</span><span class="sxs-lookup"><span data-stu-id="3007d-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="3007d-127">Derleyici daha sonra DocFileName.xml oluşturur ve bu son belgeleri üretmek için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi dokümantasyon araçları tarafından tüketilen dosyadır.</span><span class="sxs-lookup"><span data-stu-id="3007d-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a><span data-ttu-id="3007d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3007d-128">See also</span></span>

- [<span data-ttu-id="3007d-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3007d-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3007d-130">Dokümantasyon Yorumları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="3007d-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
