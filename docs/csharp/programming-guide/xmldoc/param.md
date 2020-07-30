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
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381560"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="2c730-105">\<param>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2c730-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c730-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2c730-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="2c730-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c730-107">Parameters</span></span>

- `name`

  <span data-ttu-id="2c730-108">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="2c730-108">The name of a method parameter.</span></span> <span data-ttu-id="2c730-109">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="2c730-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="2c730-110">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="2c730-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c730-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c730-111">Remarks</span></span>

<span data-ttu-id="2c730-112">`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c730-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="2c730-113">Birden çok parametreyi belgelemek için birden çok `<param>` etiket kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c730-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="2c730-114">`<param>`Etiket metni IntelliSense, nesne tarayıcısı ve kod açıklaması Web raporu ' nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2c730-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="2c730-115">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2c730-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2c730-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c730-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="2c730-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c730-117">See also</span></span>

- [<span data-ttu-id="2c730-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c730-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2c730-119">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="2c730-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
