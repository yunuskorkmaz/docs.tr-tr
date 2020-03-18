---
title: <typeparamref>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789654"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="4e24d-102">\<typeparamref> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4e24d-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e24d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e24d-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="4e24d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e24d-104">Parameters</span></span>

- `name`

  <span data-ttu-id="4e24d-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="4e24d-105">The name of the type parameter.</span></span> <span data-ttu-id="4e24d-106">Adı çift tırnak işaretlerine (" ") ekin.</span><span class="sxs-lookup"><span data-stu-id="4e24d-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="4e24d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e24d-107">Remarks</span></span>

<span data-ttu-id="4e24d-108">Genel tür ve yöntemlerdeki tür parametreleri hakkında daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4e24d-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="4e24d-109">Belge dosyasının tüketicilerinsözcüğü farklı şekillerde biçimlendirmesini sağlamak için bu etiketi kullanın, örneğin italik durumlarda.</span><span class="sxs-lookup"><span data-stu-id="4e24d-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="4e24d-110">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="4e24d-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4e24d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e24d-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="4e24d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e24d-112">See also</span></span>

- [<span data-ttu-id="4e24d-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e24d-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4e24d-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="4e24d-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
