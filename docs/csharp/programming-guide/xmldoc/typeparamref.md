---
title: <typeparamref>-C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <typeparamref> . Bu etiket, belge dosyası tüketicilerinin sözcüğü farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlar.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380728"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="6be6c-104">\<typeparamref>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6be6c-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6be6c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6be6c-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="6be6c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6be6c-106">Parameters</span></span>

- `name`

  <span data-ttu-id="6be6c-107">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="6be6c-107">The name of the type parameter.</span></span> <span data-ttu-id="6be6c-108">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="6be6c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6be6c-109">Remarks</span></span>

<span data-ttu-id="6be6c-110">Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="6be6c-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="6be6c-111">Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6be6c-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="6be6c-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6be6c-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="6be6c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6be6c-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="6be6c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be6c-114">See also</span></span>

- [<span data-ttu-id="6be6c-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6be6c-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6be6c-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="6be6c-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
