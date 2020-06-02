---
title: <value> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287200"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="ed99e-102">\<value>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ed99e-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed99e-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed99e-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="ed99e-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed99e-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="ed99e-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="ed99e-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed99e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed99e-106">Remarks</span></span>

<span data-ttu-id="ed99e-107">`<value>`Etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed99e-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="ed99e-108">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, [\<summary>](./summary.md) yeni özellik için bir etiket ekler.</span><span class="sxs-lookup"><span data-stu-id="ed99e-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="ed99e-109">Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed99e-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="ed99e-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="ed99e-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ed99e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed99e-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="ed99e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed99e-112">See also</span></span>

- [<span data-ttu-id="ed99e-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed99e-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ed99e-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="ed99e-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
