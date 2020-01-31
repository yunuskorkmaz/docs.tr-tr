---
title: <typeparamref> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789654"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="0c8e7-102">\<typeparamref > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0c8e7-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c8e7-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c8e7-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="0c8e7-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c8e7-104">Parameters</span></span>

- `name`

  <span data-ttu-id="0c8e7-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="0c8e7-105">The name of the type parameter.</span></span> <span data-ttu-id="0c8e7-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="0c8e7-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="0c8e7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c8e7-107">Remarks</span></span>

<span data-ttu-id="0c8e7-108">Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c8e7-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="0c8e7-109">Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c8e7-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="0c8e7-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="0c8e7-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0c8e7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c8e7-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="0c8e7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8e7-112">See also</span></span>

- [<span data-ttu-id="0c8e7-113">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0c8e7-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0c8e7-114">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="0c8e7-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
