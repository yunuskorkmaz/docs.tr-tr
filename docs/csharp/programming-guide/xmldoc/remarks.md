---
title: <remarks> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287291"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="8a290-102">\<remarks>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8a290-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a290-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a290-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="8a290-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a290-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="8a290-105">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="8a290-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a290-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a290-106">Remarks</span></span>

<span data-ttu-id="8a290-107">`<remarks>`Etiketi, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="8a290-107">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="8a290-108">Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8a290-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="8a290-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8a290-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8a290-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a290-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="8a290-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a290-111">See also</span></span>

- [<span data-ttu-id="8a290-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8a290-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8a290-113">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="8a290-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
