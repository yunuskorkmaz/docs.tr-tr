---
title: <param> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287330"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="441d3-102">\<param>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="441d3-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="441d3-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="441d3-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="441d3-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="441d3-104">Parameters</span></span>

- `name`

  <span data-ttu-id="441d3-105">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="441d3-105">The name of a method parameter.</span></span> <span data-ttu-id="441d3-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="441d3-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="441d3-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="441d3-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="441d3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="441d3-108">Remarks</span></span>

<span data-ttu-id="441d3-109">`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="441d3-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="441d3-110">Birden çok parametreyi belgelemek için birden çok `<param>` etiket kullanın.</span><span class="sxs-lookup"><span data-stu-id="441d3-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="441d3-111">`<param>`Etiket metni IntelliSense, nesne tarayıcısı ve kod açıklaması Web raporu ' nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="441d3-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="441d3-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="441d3-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="441d3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="441d3-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="441d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="441d3-114">See also</span></span>

- [<span data-ttu-id="441d3-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="441d3-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="441d3-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="441d3-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
