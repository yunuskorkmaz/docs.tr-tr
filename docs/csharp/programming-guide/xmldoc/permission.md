---
title: <permission> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093480"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="d6c0e-102">\<izin> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d6c0e-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c0e-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6c0e-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="d6c0e-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6c0e-104">Parameters</span></span>

- <span data-ttu-id="d6c0e-105">cref = `member`" "</span><span class="sxs-lookup"><span data-stu-id="d6c0e-105">cref = " `member`"</span></span>

  <span data-ttu-id="d6c0e-106">Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d6c0e-107">Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki kanonik öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d6c0e-108">*üye* çift tırnak içinde görünmelidir (" ").</span><span class="sxs-lookup"><span data-stu-id="d6c0e-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="d6c0e-109">Genel bir türe nasıl bir cref başvurusu oluşturabilirsiniz hakkında bilgi için [bkz.](./cref-attribute.md)</span><span class="sxs-lookup"><span data-stu-id="d6c0e-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="d6c0e-110">Üyeye erişimin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c0e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6c0e-111">Remarks</span></span>

<span data-ttu-id="d6c0e-112">İzin \<> etiketi, bir üyenin erişimini belgelemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="d6c0e-113">Sınıf, <xref:System.Security.PermissionSet> bir üyeye erişimi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="d6c0e-114">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d6c0e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6c0e-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="d6c0e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6c0e-116">See also</span></span>

- [<span data-ttu-id="d6c0e-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6c0e-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d6c0e-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="d6c0e-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
