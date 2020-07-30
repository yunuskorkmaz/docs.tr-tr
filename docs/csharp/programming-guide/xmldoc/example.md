---
title: <example> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <example> Etiket. Bu etiket, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize imkan sağlar.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381534"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="7c8b3-105">\<example>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7c8b3-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c8b3-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7c8b3-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="7c8b3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c8b3-107">Parameters</span></span>

- `description`

  <span data-ttu-id="7c8b3-108">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="7c8b3-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c8b3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c8b3-109">Remarks</span></span>

<span data-ttu-id="7c8b3-110">`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c8b3-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="7c8b3-111">Bu genellikle etiketinin kullanılmasını içerir [\<code>](./code.md) .</span><span class="sxs-lookup"><span data-stu-id="7c8b3-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="7c8b3-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7c8b3-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7c8b3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c8b3-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="7c8b3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c8b3-114">See also</span></span>

- [<span data-ttu-id="7c8b3-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7c8b3-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c8b3-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="7c8b3-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
