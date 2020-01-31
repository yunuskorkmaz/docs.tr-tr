---
title: <param> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789768"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="8fe47-102">\<param > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8fe47-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fe47-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fe47-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="8fe47-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fe47-104">Parameters</span></span>

- `name`

  <span data-ttu-id="8fe47-105">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="8fe47-105">The name of a method parameter.</span></span> <span data-ttu-id="8fe47-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="8fe47-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="8fe47-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="8fe47-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fe47-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fe47-108">Remarks</span></span>

<span data-ttu-id="8fe47-109">Yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimi için açıklamasında \<param > etiketi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fe47-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="8fe47-110">Birden çok parametreyi belgelemek için, birden çok \<param > etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fe47-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="8fe47-111">\<param > etiketinin metni IntelliSense 'de, Nesne Tarayıcısı ve kod yorumu Web raporunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fe47-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="8fe47-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8fe47-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8fe47-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fe47-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="8fe47-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fe47-114">See also</span></span>

- [<span data-ttu-id="8fe47-115">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8fe47-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8fe47-116">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="8fe47-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
