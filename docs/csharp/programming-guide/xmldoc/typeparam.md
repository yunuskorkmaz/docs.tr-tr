---
title: <typeparam> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <typeparam> Etiket. Bu etiket, bir tür parametresini anlatmak için genel bir tür veya yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380793"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="a2f1a-105">\<typeparam>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a2f1a-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2f1a-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a2f1a-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="a2f1a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2f1a-107">Parameters</span></span>

- `name`

  <span data-ttu-id="a2f1a-108">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-108">The name of the type parameter.</span></span> <span data-ttu-id="a2f1a-109">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="a2f1a-110">Tür parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2f1a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2f1a-111">Remarks</span></span>

<span data-ttu-id="a2f1a-112">`<typeparam>`Etiket, bir tür parametresini betimleyen genel tür veya yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="a2f1a-113">Genel tür veya metodun her tür parametresi için bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="a2f1a-114">Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2f1a-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="a2f1a-115">`<typeparam>`Etiketin metni IntelliSense 'de, [nesne tarayıcısı pencere](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu açıklama Web raporu ' nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="a2f1a-116">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a2f1a-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2f1a-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="a2f1a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2f1a-118">See also</span></span>

- [<span data-ttu-id="a2f1a-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2f1a-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="a2f1a-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a2f1a-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a2f1a-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="a2f1a-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
