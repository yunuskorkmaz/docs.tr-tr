---
title: <permission> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 14abb5bd181f401a4e6834d110e20fa920566580
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789731"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="4cd5c-102">\<izin > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4cd5c-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4cd5c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cd5c-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="4cd5c-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cd5c-104">Parameters</span></span>

- <span data-ttu-id="4cd5c-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="4cd5c-105">cref = " `member`"</span></span>

  <span data-ttu-id="4cd5c-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4cd5c-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4cd5c-108">*üye* çift tırnak işareti ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="4cd5c-109">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [\<](./see.md).</span><span class="sxs-lookup"><span data-stu-id="4cd5c-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>

- `description`

  <span data-ttu-id="4cd5c-110">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cd5c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cd5c-111">Remarks</span></span>

<span data-ttu-id="4cd5c-112">\<izin > etiketi bir üyenin erişimini belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="4cd5c-113"><xref:System.Security.PermissionSet> sınıfı, bir üyeye erişim belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="4cd5c-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4cd5c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cd5c-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="4cd5c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cd5c-116">See also</span></span>

- [<span data-ttu-id="4cd5c-117">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4cd5c-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4cd5c-118">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="4cd5c-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
