---
title: <param> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <param> Etiket. Bu etiket, yöntemi için olan parametrelerden birini açıklayacak bir yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 1385365b2cdf18563686fdf4a5a1b17b89feafcd
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477986"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="2ea55-105">\<param> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2ea55-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ea55-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ea55-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="2ea55-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ea55-107">Parameters</span></span>

- `name`

  <span data-ttu-id="2ea55-108">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="2ea55-108">The name of a method parameter.</span></span> <span data-ttu-id="2ea55-109">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="2ea55-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="2ea55-110">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="2ea55-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ea55-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ea55-111">Remarks</span></span>

<span data-ttu-id="2ea55-112">`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ea55-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="2ea55-113">Birden çok parametreyi belgelemek için birden çok `<param>` etiket kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ea55-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="2ea55-114">`<param>`Etiket metni IntelliSense, nesne tarayıcısı ve kod açıklaması Web raporu ' nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2ea55-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="2ea55-115">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2ea55-115">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2ea55-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ea55-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="2ea55-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea55-117">See also</span></span>

- [<span data-ttu-id="2ea55-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ea55-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2ea55-119">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="2ea55-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
