---
title: <value> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793347"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="95493-102">\<değeri > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="95493-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="95493-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95493-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="95493-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95493-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="95493-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="95493-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="95493-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95493-106">Remarks</span></span>

<span data-ttu-id="95493-107">\<Value > etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="95493-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="95493-108">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için bir [\<summary >](./summary.md) etiketi ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="95493-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="95493-109">Sonra özelliğin temsil ettiği değeri tanımlayan bir \<değer > etiketi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="95493-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="95493-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="95493-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="95493-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="95493-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="95493-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95493-112">See also</span></span>

- [<span data-ttu-id="95493-113">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95493-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="95493-114">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="95493-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
