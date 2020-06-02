---
title: <paramref>-C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287317"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="9c46f-102">\<paramref>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9c46f-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c46f-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9c46f-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="9c46f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c46f-104">Parameters</span></span>

- `name`

  <span data-ttu-id="9c46f-105">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="9c46f-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="9c46f-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="9c46f-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="9c46f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c46f-107">Remarks</span></span>

<span data-ttu-id="9c46f-108">`<paramref>`Etiketi, kod açıklamalarındaki bir sözcüğün, örneğin bir `<summary>` veya bloğunda bir parametreye başvurduğunu göstermek için bir yol sağlar `<remarks>` .</span><span class="sxs-lookup"><span data-stu-id="9c46f-108">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="9c46f-109">Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="9c46f-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="9c46f-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="9c46f-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9c46f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c46f-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="9c46f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c46f-112">See also</span></span>

- [<span data-ttu-id="9c46f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9c46f-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9c46f-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="9c46f-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
