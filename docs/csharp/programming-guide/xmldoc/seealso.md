---
title: <seealso> -C# Programlama Kılavuzu
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
ms.openlocfilehash: 1b801ac1b5a0a59d97ccc35ec78930d99223e846
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287226"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="86c21-102">\<seealso>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="86c21-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="86c21-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="86c21-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="86c21-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86c21-104">Parameters</span></span>

- <span data-ttu-id="86c21-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="86c21-105">cref = " `member`"</span></span>

  <span data-ttu-id="86c21-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="86c21-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="86c21-107">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.`member`</span><span class="sxs-lookup"><span data-stu-id="86c21-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="86c21-108">Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="86c21-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="86c21-109">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="86c21-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="86c21-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86c21-110">Remarks</span></span>

<span data-ttu-id="86c21-111">`<seealso>`Etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c21-111">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="86c21-112">[\<see>](./see.md)Metnin içinden bir bağlantı belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="86c21-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="86c21-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="86c21-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="86c21-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="86c21-114">Example</span></span>

<span data-ttu-id="86c21-115">[\<summary>](./summary.md)Hakkında bir örnek için bkz \<seealso> ..</span><span class="sxs-lookup"><span data-stu-id="86c21-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="86c21-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c21-116">See also</span></span>

- [<span data-ttu-id="86c21-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86c21-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="86c21-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="86c21-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
