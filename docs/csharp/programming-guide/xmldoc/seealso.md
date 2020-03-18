---
title: <seealso> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093467"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="24256-102">\<seealso> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="24256-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="24256-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24256-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="24256-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24256-104">Parameters</span></span>

- <span data-ttu-id="24256-105">cref = `member`" "</span><span class="sxs-lookup"><span data-stu-id="24256-105">cref = " `member`"</span></span>

  <span data-ttu-id="24256-106">Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="24256-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="24256-107">Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki öğe adına geçer.`member`</span><span class="sxs-lookup"><span data-stu-id="24256-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="24256-108">çift tırnak işaretleri içinde görünmelidir (" ").</span><span class="sxs-lookup"><span data-stu-id="24256-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="24256-109">Genel bir türe nasıl bir cref başvurusu oluşturabilirsiniz hakkında bilgi için [bkz.](./cref-attribute.md)</span><span class="sxs-lookup"><span data-stu-id="24256-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="24256-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24256-110">Remarks</span></span>

<span data-ttu-id="24256-111">Seealso> etiketi, \<Bkz. Ayrıca bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="24256-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="24256-112">Metin içinden bir bağlantı belirtmek için [ \<bkz.>](./see.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="24256-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="24256-113">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="24256-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="24256-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="24256-114">Example</span></span>

<span data-ttu-id="24256-115">Seealso> kullanma \<örneği için özet [ \<>](./summary.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="24256-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="24256-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24256-116">See also</span></span>

- [<span data-ttu-id="24256-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24256-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="24256-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="24256-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
