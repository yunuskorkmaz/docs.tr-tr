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
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380780"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="87a01-105">\<value>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="87a01-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="87a01-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="87a01-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="87a01-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87a01-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="87a01-108">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="87a01-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="87a01-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87a01-109">Remarks</span></span>

<span data-ttu-id="87a01-110">`<value>`Etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="87a01-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="87a01-111">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, [\<summary>](./summary.md) yeni özellik için bir etiket ekler.</span><span class="sxs-lookup"><span data-stu-id="87a01-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="87a01-112">Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a01-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="87a01-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="87a01-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="87a01-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="87a01-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="87a01-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87a01-115">See also</span></span>

- [<span data-ttu-id="87a01-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="87a01-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="87a01-117">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="87a01-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
