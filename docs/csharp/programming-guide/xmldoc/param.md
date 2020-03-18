---
title: <param> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789768"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="1170a-102">\<param> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1170a-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1170a-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1170a-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="1170a-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1170a-104">Parameters</span></span>

- `name`

  <span data-ttu-id="1170a-105">Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="1170a-105">The name of a method parameter.</span></span> <span data-ttu-id="1170a-106">Adı çift tırnak işaretlerine (" ") ekin.</span><span class="sxs-lookup"><span data-stu-id="1170a-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="1170a-107">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="1170a-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="1170a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1170a-108">Remarks</span></span>

<span data-ttu-id="1170a-109">Param \<> etiketi, yöntemin parametrelerinden birini açıklamak için bir yöntem bildirimi için açıklama da kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1170a-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="1170a-110">Birden çok parametreyi \<belgelemek için birden çok param> etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1170a-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="1170a-111">Param> \<etiketinin metni IntelliSense, Object Browser ve Code Comment Web Report'ta görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1170a-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="1170a-112">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="1170a-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1170a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1170a-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="1170a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1170a-114">See also</span></span>

- [<span data-ttu-id="1170a-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1170a-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1170a-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="1170a-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
