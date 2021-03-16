---
title: <typeparamref> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <typeparamref> . Bu etiket, belge dosyası tüketicilerinin sözcüğü farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlar.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 1bb9a73f4122f3b9d521565a7172a9b8f75f7a98
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477667"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="b935c-104">\<typeparamref> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b935c-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b935c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b935c-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="b935c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b935c-106">Parameters</span></span>

- `name`

  <span data-ttu-id="b935c-107">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="b935c-107">The name of the type parameter.</span></span> <span data-ttu-id="b935c-108">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="b935c-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="b935c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b935c-109">Remarks</span></span>

<span data-ttu-id="b935c-110">Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="b935c-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="b935c-111">Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b935c-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="b935c-112">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="b935c-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b935c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b935c-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="b935c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b935c-114">See also</span></span>

- [<span data-ttu-id="b935c-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b935c-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b935c-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="b935c-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
