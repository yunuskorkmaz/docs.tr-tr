---
title: <value> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <value> Etiket. Bu etiket, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477637"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="7fd75-105">\<value> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7fd75-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fd75-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fd75-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="7fd75-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7fd75-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="7fd75-108">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="7fd75-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fd75-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7fd75-109">Remarks</span></span>

<span data-ttu-id="7fd75-110">`<value>`Etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fd75-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="7fd75-111">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, [\<summary>](./summary.md) yeni özellik için bir etiket ekler.</span><span class="sxs-lookup"><span data-stu-id="7fd75-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="7fd75-112">Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fd75-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="7fd75-113">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7fd75-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7fd75-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fd75-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="7fd75-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fd75-115">See also</span></span>

- [<span data-ttu-id="7fd75-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7fd75-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7fd75-117">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="7fd75-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
