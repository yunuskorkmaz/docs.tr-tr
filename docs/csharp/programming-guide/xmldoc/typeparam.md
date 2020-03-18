---
title: <typeparam> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793360"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="3c62c-102">\<typeparam> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3c62c-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c62c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c62c-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="3c62c-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c62c-104">Parameters</span></span>

- `name`

  <span data-ttu-id="3c62c-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="3c62c-105">The name of the type parameter.</span></span> <span data-ttu-id="3c62c-106">Adı çift tırnak işaretlerine (" ") ekin.</span><span class="sxs-lookup"><span data-stu-id="3c62c-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="3c62c-107">Tür parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="3c62c-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c62c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c62c-108">Remarks</span></span>

<span data-ttu-id="3c62c-109">Etiket, `<typeparam>` bir tür parametresini açıklamak için genel bir tür veya yöntem bildirimi için yorumda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c62c-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="3c62c-110">Genel tür veya yöntemin her tür parametresi için bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c62c-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="3c62c-111">Daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3c62c-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="3c62c-112">Etiketin `<typeparam>` metni, [Nesne Tarayıcı Penceresi](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu yorum web raporu olan IntelliSense'de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3c62c-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="3c62c-113">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="3c62c-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="3c62c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c62c-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="3c62c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c62c-115">See also</span></span>

- [<span data-ttu-id="3c62c-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c62c-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3c62c-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3c62c-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="3c62c-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="3c62c-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
