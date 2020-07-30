---
title: <permission> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <permission> Etiket. Bu etiket bir üyenin erişimini belgelemenizi sağlar, ancak PermissionSet sınıfı bir üyeye erişim belirtmenize izin verir.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381729"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="bc91d-105">\<permission>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bc91d-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc91d-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bc91d-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="bc91d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc91d-107">Parameters</span></span>

- <span data-ttu-id="bc91d-108">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="bc91d-108">cref = " `member`"</span></span>

  <span data-ttu-id="bc91d-109">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="bc91d-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="bc91d-110">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="bc91d-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="bc91d-111">*üye* çift tırnak işareti ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc91d-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="bc91d-112">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="bc91d-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="bc91d-113">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="bc91d-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc91d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc91d-114">Remarks</span></span>

<span data-ttu-id="bc91d-115">`<permission>`Etiketi bir üyenin erişimini belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc91d-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="bc91d-116"><xref:System.Security.PermissionSet>Sınıfı, bir üyeye erişim belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc91d-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="bc91d-117">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="bc91d-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bc91d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc91d-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="bc91d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc91d-119">See also</span></span>

- [<span data-ttu-id="bc91d-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bc91d-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bc91d-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="bc91d-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
