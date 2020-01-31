---
title: <paramref> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793398"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="d6476-102">\<paramref > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d6476-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6476-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6476-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="d6476-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6476-104">Parameters</span></span>

- `name`

  <span data-ttu-id="d6476-105">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d6476-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="d6476-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="d6476-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="d6476-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6476-107">Remarks</span></span>

<span data-ttu-id="d6476-108">\<paramref > etiketi, kod açıklamalarındaki bir sözcüğün, örneğin \<Özet > veya \<Comments > bloğunun bir parametreye başvurduğunu göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6476-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="d6476-109">Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d6476-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="d6476-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d6476-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d6476-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6476-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="d6476-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6476-112">See also</span></span>

- [<span data-ttu-id="d6476-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6476-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d6476-114">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="d6476-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
