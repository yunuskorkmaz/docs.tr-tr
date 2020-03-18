---
title: <paramref>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793398"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="eb897-102">\<paramref> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="eb897-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb897-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb897-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="eb897-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb897-104">Parameters</span></span>

- `name`

  <span data-ttu-id="eb897-105">Başvurmak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="eb897-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="eb897-106">Adı çift tırnak işaretlerine (" ") ekin.</span><span class="sxs-lookup"><span data-stu-id="eb897-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="eb897-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb897-107">Remarks</span></span>

<span data-ttu-id="eb897-108">\<Paramref> etiketi, kod açıklamalarında, örneğin \<bir özet> veya \<blok> açıklamadaki bir sözcüğün bir parametreye atıfta bulunduğunu belirtmeniz için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="eb897-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="eb897-109">XML dosyası, bu sözcüğü kalın veya italik yazı tipi gibi farklı şekillerde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb897-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="eb897-110">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="eb897-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="eb897-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb897-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="eb897-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb897-112">See also</span></span>

- [<span data-ttu-id="eb897-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb897-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eb897-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="eb897-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
