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
ms.openlocfilehash: 379d3fda06c50e9e988784e671061d604e6e5b36
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477845"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="4f984-105">\<permission> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4f984-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f984-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f984-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="4f984-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f984-107">Parameters</span></span>

- <span data-ttu-id="4f984-108">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="4f984-108">cref = " `member`"</span></span>

  <span data-ttu-id="4f984-109">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="4f984-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4f984-110">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="4f984-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4f984-111">*üye* çift tırnak işareti ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f984-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="4f984-112">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="4f984-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="4f984-113">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="4f984-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f984-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f984-114">Remarks</span></span>

<span data-ttu-id="4f984-115">`<permission>`Etiketi bir üyenin erişimini belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f984-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="4f984-116"><xref:System.Security.PermissionSet>Sınıfı, bir üyeye erişim belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f984-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="4f984-117">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="4f984-117">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4f984-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f984-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="4f984-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f984-119">See also</span></span>

- [<span data-ttu-id="4f984-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4f984-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4f984-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="4f984-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
